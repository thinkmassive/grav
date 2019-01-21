---
taxonomy:
  category: research
  tag: [research, sabbatical, development, kubernetes, blockchain]
---

Imported blog post from 2018 May 14

===

Today I am one week into a 12-week open source sabbatical. At the beginning of May, I left full-time employment to devote my full attention to producing a successful open source project. I recognize that I am very fortunate to be in a position to perform this type of endevour, so I want to make the most of this possibly once-in-a-lifetime opportunity.

As a bit of background, my past three jobs have been with a [big data leader](https://hortonworks.com), a [Linux distro](https://endlessos.com), and a leading non-custodial cryptocurrency exchange (that wishes to remain nameless). From these and prior roles I have gained significant experience in many aspects of modern computing architecture, however one area where I haven't gained more than a superficial knowledge is containers. The deepest relevant experience comes from Hadoop's YARN, which provides decent insight into one application-specific use case. I want to gain an expert-level understanding of general containers and their orchestration.

Another area of technology that I have a good amount of experience (relative to the industry) is operating a variatey of blockchain systems. I say "relative to the industry" because I've witnessed first-hand the lack of experience and discipline that's prevelent in the blockchain industry. While I've met many talented developers (typically go, python, nodejs), the talented infrastructure people seem to be few and far between. Many developers are using containers already, and some blockchain platforms even distribute an official Docker image, but what the crypto space lacks is a good way to deploy containerized applications alongside blockchain interfaces in a unified environment.

To fill this void I am creating CryptoKube, a blockchain application platform. The mission is to minimize friction for developers to build and deploy blockchain applications to the world. I believe that blockchain technology offers many potential improvements, so I want to enable the visionaries in the space to implement their projects as easily as possible. If this project is a success, then it's also likely to lead to future opportunities for myself to expand/customize/implement it, and I will welcome most of these opportunities if they occur. Either way, I expect to maintain this project for the foreseeable future, if for nothing else than managing my own crypto infrastructure.

### Sabbatical goals

  - Primary: deliver useful platform tooling to the blockchain development community
  - Secondary: deep-dive into new technologies, in particular containers & blockchains
  - Tertiary: produce a long-lived system that leads to business opportunities

### Additional ambitions & guidance
  - Loosely follow the CNCF [Cloud Native Trail Map](https://github.com/cncf/landscape#trail-map)
  - Adhere to the Linux Foundation [Core Infrastructure Initiative Best Practices](https://github.com/coreinfrastructure/best-practices-badge/blob/master/doc/criteria.md)
  - Join the the [CNCF Landscape](https://github.com/cncf/landscape)
  
You can follow my progress at:
  - [ThinkMassive.org](https://thinkmassive.org) (this blog)
  - [Github repo](https://github.com/thinkmassive/CryptoKube)
  - [Twitter](https://twitter.com/thinkmassive) for notifications about blog updates

## 12-week open source sabbatical timeline

### May 2018
- Week 1: Research and preparation
- Week 2: Project groudwork (website, repo, license, docs)
- Week 3: Release engineering (build system, container registry, automated testing) & backups
- Week 4: Blockchain application containers (geth, ipfs, wallet, block explorer)

### June 2018
- Week 5: Monitoring (prometheus)
- Week 6: Logging (fluentd)
- Week 7: Visualization & reporting (grafana)
- Week 8: Kubernetes best practices (security/AAA, high-availability, autoscaling)

### July 2018
- Week 9: Extending kubernetes (helm, CRDs, operators)
- Week 10: Bitcoin (lightning, rootstock)
- Week 11: Data pipeline
- Week 12: Stabilize

