# Run My Job

> **Cloud runners for GitHub Actions & GitLab CI — up to 2× faster and 10× cheaper. Pay only for real usage, not idle time.**
---

## Table of Contents
- [Features](#features)
- [How-it-works](#how-it-works)
- [Quick-start](#quick-start)
- [Documentation](#documentation)
- [Support](#support)
- [Security](#security)
- [License](#license)

---

## Features

- **Spike Instances** — KVM-backed MicroVMs that boot in seconds, providing near bare-metal speed plus strong isolation.
- **Load-based billing** — billed per vCPU-second & GB-second; idle CPU is free, so heavy jobs cost less overall.
- **Seamless integration** — drop-in replacement for GitHub & GitLab runners; just change a single label.
- **Generous resources** — automatically scales each job up to dozens of cores and gigabytes of RAM, then back down.
- **Ephemeral filesystem** — every job mounts its own high-performance, throw-away filesystem; zero cleanup required.
- **Dashboard & API** — manage everything in the web console or fully-declarative Kubernetes manifests.

---

## How it Works

- Each CI job starts inside its own **Spike Instance** — a lightweight MicroVM that delivers raw CPU performance and complete tenant isolation.  
- Every second we meter the job’s actual CPU and memory load, so you pay only for the resources the job really uses, not for pre-allocated capacity that sits idle.  
- Because runners are completely ephemeral, your pipelines stay fast, secure, and self-cleaning.

---

## Quick Start

Follow the quick setup guides in our documentation:

- [GitHub Actions Runner Setup](https://docs.puzl.cloud/services/run-my-job/github-actions/quick-setup-of-github-runner)  
- [GitLab CI Runner Setup](https://docs.puzl.cloud/services/run-my-job/gitlab-pipelines/quick-setup-of-gitlab-runner)

---

## Pricing

Run My Job offers Free, Business, and Enterprise plans — all with transparent load-based usage pricing.  
Check the latest details here: [https://runmyjob.io/#pricing](https://runmyjob.io/#Pricing)

---

## Documentation

Full documentation, including advanced configuration, caching, storage options, and Terraform modules, is available at:  
[https://docs.puzl.cloud/services/run-my-job](https://docs.puzl.cloud/services/run-my-job)

---

## Support

- **Email** — support@puzl.cloud  

---

## Security

If you discover a vulnerability, please email security@puzl.cloud.

---

## License

Distributed under the **MIT License**. See [`LICENSE`](LICENSE) for more information.
