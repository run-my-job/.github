# Run My Job by Puzl Cloud

> **Cloud runners for GitHub Actions & GitLab CI — up to 2× faster and 10× cheaper. Pay only for real usage, not idle time.**
---

## Table of Contents
- [Features](#features)
- [How it Works](#how-it-works)
- [Quick Start](#quick-start)
  - [GitHub Actions](#github-actions)
  - [GitLab CI](#gitlab-ci)
- [Documentation](#documentation)
- [Support](#support)
- [Security](#security)

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

### GitHub Actions

1. **Install** the Puzl GitHub App to your organization.
2. **Push** a workflow file that targets the `puzl-ubuntu-latest` runner label:

```yaml
# .github/workflows/ci.yml
name: CI

on: [push, pull_request]

jobs:
  build:
    runs-on: puzl-ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: ./scripts/test.sh
```

That’s it — your jobs will now run on Run My Job’s blazingly fast Spike Instances.

### GitLab CI

1. **Create** a `GitLabPipelinesIntegration` (via the web console or `kubectl`):

```yaml
apiVersion: gitlab-pipelines.svcs.puzl.cloud/v2
kind: GitLabPipelinesIntegration
metadata:
  name: my-first-integration
spec:
  gitlabUrl: https://gitlab.com   # or your self-hosted GitLab
```

```bash
kubectl apply -f my-first-integration.yaml
```

2. **Request** a runner by creating a `GitLabRunnerClaim`:

```yaml
apiVersion: gitlab-pipelines.svcs.puzl.cloud/v2
kind: GitLabRunnerClaim
metadata:
  namespace: <Your_Integration_claimNamespaceRef>
  name: my-first-runner
spec:
  jobProvider:
    token: <YOUR_GITLAB_TOKEN>
```

```bash
kubectl apply -f my-first-runner.yaml
```

3. Once the claim status turns **Ready**, target the runner from your `.gitlab-ci.yml` using the `tags` you defined (tags are optional for GitLab ≥16).

---

## Documentation

Comprehensive docs live at **https://docs.puzl.cloud/services/run-my-job/getting-started**

---

## Support

- **Email** — support@puzl.cloud

We’re always happy to help!

---

## Security

If you discover a vulnerability, please email **security@puzl.cloud**.
