---
title: Fedora Silverblue
taxonomy:
  category: project
  tag: [ project, os, containers, kubernetes ]
---

Fedora Silverblue immutable workstation OS

===

# Silverblue

Installing Fedora 29 Silverblue on NUC i3 32G 512G

### Docs
- Silverblue: https://docs.fedoraproject.org/en-US/fedora-silverblue
- Buildah tutorials; https://github.com/containers/buildah/tree/master/docs/tutorials
- libostree: https://ostree.readthedocs.io/en/latest
- rpm-ostree: https://rpm-ostree.readthedocs.io/en/latest
- Flatpak: http://docs.flatpak.org/en/latest

### RPM-OSTree
```bash
sudo rpm-ostree upgrade ; reboot
sudo rpm-ostree install tmux vim htop
```

### Flatpak
Ran `flatpak-update ; flatpak remote-ls --updates` with no apparent updates available

### Kubernetes
#### Initial Hyperkube test
```bash
sudo curl -o /etc/bash_completion.d/podman https://raw.githubusercontent.com/containers/libpod/master/completions/bash/podman
podman pull gcr.io/google_containers/hyperkube:v1.13.2
podman run --rm gcr.io/google_containers/hyperkube:v1.13.2 /hyperkube apiserver --help
podman run --rm gcr.io/google_containers/hyperkube:v1.13.2 /hyperkube scheduler --help
podman run --rm gcr.io/google_containers/hyperkube:v1.13.2 /hyperkube controller-manager --help
```

#### Cluster planning
- Cluster subnet: 10.20.0.0/16
  - 10.20.0.0/24 nodes
  - 10.20.10.0/24 master-1 pods
  - 10.20.20.0/24 minion-1 pods
  - 10.20.100.0/24 services
  - 10.20.0.1 master-1 (allow 80 & 443, net.ipv4.ip_forward=1)
  - 10.20.0.2 minion-1
- Cluster name: micromega
- Binaries
  - etcd
  - cri-o
  - hyperkube 

#### Disable swap
```bash
SWAP_PARTITION=$(grep $(lsblk -l | grep '\[SWAP\]' | awk '{print $1}') /etc/fstab | awk '{print $1}')
sudo swapoff $SWAP_PARTITION
sed -i "s|^$SWAP_PARTITION\s|#$SWAP_PARTITION |" /etc/fstab
```

#### Install kubectl
```bash
mkdir -p $HOME/bin

# Download kubectl binary
KUBECTL_URL=https://storage.googleapis.com/kubernetes-release/release
curl -L -o ~/bin/kubectl $KUBECTL_URL/$(curl -s $KUBECTL_URL/stable.txt)/bin/linux/amd64/kubectl
chmod +x ~/bin/kubectl

# Enable bash completion
source <(kubectl completion bash)
echo "source <(kubectl completion bash)" >> ~/.bash_profile

# Generate admin kubeconfig file
export KUBECONFIG=$HOME/.kube/config
export CLUSTER_NAME=silverblue
export CONTEXT_NAME=default
kubectl config set-cluster $CLUSTER_NAME --server=http://127.0.0.1 --insecure-skip-tls-verify=true
kubectl config set-context $CONTEXT_NAME --cluster=$CLUSTER_NAME --user=$USER
kubectl config use-context $CONTEXT_NAME
```

#### Initialize cluster config
```bash
export HK_TAG=v1.13.2 HK_IMAGE=k8s.gcr.io/hyperkube:$HK_TAG
export ETCD_TAG=3.3.10 ETCD_IMAGE=k8s.gcr.io/etcd:$ETCD_TAG
export KUBECONFIG=$HOME/.kube/config

sudo mkdir -p /etc/kubernetes/manifests /var/lib/kubelet /var/lib/kube-proxy
sudo cp ~/.kube/config /var/lib/kubelet/kubeconfig
sudo cp ~/.kube/config /var/lib/kube-proxy/kubeconfig
```

#### Setup CRI-O
```bash
sudo rpm-ostree install cri-o
sudo systemctl enable crio
sudo systemctl start crio
```

#### Start master services
```bash
# Start etcd
podman run --name etcd            \
  -d --net=host                   \
  $ETCD_IMAGE /usr/local/bin/etcd \
    --data-dir=/var/etcd/data

# Start kubelet
sudo podman run --name kubelet               \
  -d --net=host                              \
  -v /var/lib/kubelet:/var/lib/kubelet:z     \
  -v /var/run/crio:/var/run/crio:z           \
  -v /etc/kubernetes/manifests:/etc/kubernetes/manifests:z \
  $HK_IMAGE /hyperkube kubelet               \
    --kubeconfig=/var/lib/kubelet/kubeconfig \
    --v=2                                    \
    --address=0.0.0.0                        \
    --enable_server                          \
    --hostname_override=127.0.0.1            \
    --pod-manifest-path=/etc/kubernetes/manifests \
    --container-runtime=remote               \
    --container-runtime-endpoint=unix:///var/run/crio/crio.sock \
    --runtime-request-timeout=10m

# Troubleshooting SELinux
# type=AVC msg=audit(1547594214.044:387): avc:  denied  { write } for  pid=5522 comm="hyperkube" name="kubelet" dev="dm-1" ino=3145752 scontext=system_u:system_r:container_t:s0:c318,c932 tcontext=unconfined_u:object_r:var_lib_t:s0 tclass=dir permissive=0

# Start kube-proxy
podman run --name kube-proxy       \
  -d --net=host --privileged       \
  $HK_IMAGE /hyperkube proxy       \
    --master=http://127.0.0.1:8080 \
    --v=2
```

#### Kubernetes Links
- [Creating a Cluster from Scratch](https://kubernetes.io/docs/setup/scratch/)
- [etcd](https://github.com/coreos/etcd)
- [CRI-O](https://cri-o.io/)
  - CRI-O on Kubernetes: https://github.com/kubernetes-sigs/cri-o/blob/master/kubernetes.md

### Follow-up
- [systemd](https://developers.redhat.com/blog/2018/11/29/managing-containerized-system-services-with-podman/)
- Ansible
- [Token security]()
- kubelets & proxy have own token & kubeconfig
- [SSL](https://kubernetes.io/docs/setup/scratch/#security-models)
- [logrotate](http://linux.die.net/man/8/logrotate)
- [supervisord](http://supervisord.org/)
- volume plugin support (glusterfs, ceph)
- overlay network

### Bitcoin Core
```bash
sudo mkdir /opt/bitcoin
sudo chown 8333:8333 /opt/bitcoin

podman login docker.io
podman pull thinkmassive/bitcoin
podman run -d --name bitcoin --user 8333:8333 -v /opt/bitcoin:/root/.bitcoin thinkmassive/bitcoin-alpine
```
(had to increase ulimit nofile)

### Container registries
- Fedora Containers: https://registry.fedoraproject.org/
- Google Containers: https://console.cloud.google.com/gcr/images/google-containers/GLOBAL
- Flathub: https://flathub.org/home
