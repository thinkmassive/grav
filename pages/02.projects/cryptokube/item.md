---
title: CryptoKube
taxonomy:
  category: project
  tag: [ project, software, kubernetes, blockchain ]
---

CryptoKube is a reference implementation of a multi-blockchain application platform built on Kubernetes.

===

## CNCF Certified Kubernetes Administrator (CKA) study guide

The [Certified Kubernetes Administrator (CKA)](https://training.linuxfoundation.org/certification/certified-kubernetes-administrator-cka/) program was created by The Linux Foundation and the Cloud Native Computing Foundation (CNCF) as a part of their ongoing effort to help develop the Kubernetes ecosystem.

This is not the exact sequence I took, but it's how I would recommend using the same materials to someone who's comfortable in a Linux shell and has some familiarty with containers.

1. [kubernetes.io](https://kubernetes.io)
  - Browse the site, especially the [docs]() section. The goal is to become familiar with the terminology and gain a basic understanding of the site structure. There's a lot of content, so try not to dive too deep yet. This is the only outside resource you are allowed to use during the exam, so try to refer to it as often as possible before resorting to a general web search.

2. [Kubernetes Up and Running](http://shop.oreilly.com/product/0636920043874.do).
  - Read the book. Run the examples to the best of your ability, and make sure to get everything in the final chapter working. Some of the code in the book is no longer 100% accurate because the software is evolving so fast. I was able to resolve all issues without much stress, although during the final exercise I discovered the [eratta page](https://www.oreilly.com/catalog/errata.csp?isbn=0636920043874) that was helpful to confirm my approach. (If you're unsure about purchasing, check out some [sample chapters](https://mesosphere.com/wp-content/uploads/2017/09/running-kubernetes_oreilly-ebook.pdf) from an early release, courtesy of Mesosphere)

  - For all exercises in this book, I used [DigitalOcean Kubernetes](https://www.digitalocean.com/products/kubernetes/) (early access). It worked well and allowed me to concentrate on operations (which is mainly what the book covers) without worrying about whether Kubernetes itself was installed correctly. The cost is completely covered by their promotional credit for new accounts.

3. [Kubernetes the Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way)
  - Follow the self-taught course from Kelsey Hightower. This one utilizes Google Cloud Platform (GCP) and can be completed at no cost with trial credits.

4. [Kubernetes Fundamentals (LFS258)](https://training.linuxfoundation.org/training/kubernetes-fundamentals) 
  - Take the self-paced training course from the Linux Foundation. This can be purchased as a bundle with the CKA Exam to save $100 ($499 for both, or $299/ea). It is expensive compared with the other resources I recommend, however it was made specifically to compliment the exam, so I figured it was worth fitting into my budget.

  - The first half of the course content mostly overlaps with the book above, with the addition of a chapter for installation (a good review of "the hard way"). 

  - For all exercises in this course I used a 3-node cluster (installed according to the lab) built on DigitalOcean (4cpu, 8GB, Ubuntu 16.04, private networking).

5. [CKA Candidate Handbook](https://www.cncf.io/certification/candidate-handbook) (click to download PDF)
  - Review the handbook and schedule your exam!

### Kuberenetes Docs

**Additional Reading**
- [Kubernetes Object Management](https://kubernetes.io/docs/concepts/overview/object-management-kubectl/overview/) - understand the 3 object management techniques: imperative commands, imperative config, declarative config (labs use all of them, and I expect the exam will too)
- [Concepts](https://kubernetes.io/docs/concepts/) - best for concentrated reading due to its verbosity, rather than as a reference during labs (use the API Reference instead)
- [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/)
- [Custom Resources](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)
- [Troubleshoot clusters](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-cluster/)
- [Troubleshoot applications](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-application/) (pods, replication, services)
- [Determine reason for pod failure](https://kubernetes.io/docs/tasks/debug-application-cluster/determine-reason-pod-failure/)

**References**
- [API Reference (v1.11)](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.11/)
- Overview of [kubectl](https://kubernetes.io/docs/reference/kubectl/overview/)
- Overview of [kubeadm](https://kubernetes.io/docs/reference/setup-tools/kubeadm/kubeadm/)
- Creating a [single master cluster](https://kubernetes.io/docs/setup/independent/create-cluster-kubeadm/) with kubeadm - most concise reference for installation process, first search result for `kubeadm`
- Using [RBAC Authorization](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)

### Shell Setup

Here is my preferred Linux operating environment...

```bash
apt update -y ; apt upgrade -y ; apt autoremove -y
apt install vim htop tmux bash-completion
echo 'set shiftwidth=2 tabstop=2 expandtab smarttab smartindent' >> ~/.vimrc
echo 'source <(kubectl completion bash)' >> ~/.bashrc
echo 'set-window-option -g xterm-keys-on' >> ~/.tmux.conf
```

### Notes

I actually read the book last (after LFS258 and "the hard way"), but I found it very helpful to go through the LFS258 labs afterwards, trying to accomplish the tasks (black text) without looking at the shell output (blue text). This isn't always possible, for example when the task is "create <file.yaml>" and the content is only given in the blue text. 

A note about building a **Raspberry Pi hardware cluster**: This idea is documented in Appendix A of Kubernetes Up and Running (and many other places on the web). It seemed like a good idea to build a hardware cluster and run my own applications as a final exercise before taking the exam. Unfortunately I encountered so many issues with the hardware I had on-hand (primarily unreliable microSD cards, although it took a while to realize) that I ended up using only cloud servers for the remainder of my studies. There were also some inconsistencies between the steps in the book and the guides at [Hypriot](https://blog.hypriot.com/), which can be resolved but probably aren't relevant to the CKA exam. I still plan to build a Pi cluster when I can devote more attention to the embedded aspects of the project.
