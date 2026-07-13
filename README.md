# Dev Container Features

## Contents

This repository contains following features:

- [ag](./src/ag/README.md): Installs ag (The Silver Searcher), a fast grep-like text search tool
- [agentcore-cli](./src/agentcore-cli/README.md): Installs the Amazon Bedrock AgentCore CLI (`@aws/agentcore`) from npm
- [amazon-q-cli](./src/amazon-q-cli/README.md): Install Amazon Q CLI for AWS development
- [aws-sam-cli](./src/aws-sam-cli/README.md): Installs AWS SAM CLI for serverless application development
- [gcloud-cli](./src/gcloud-cli/README.md): Installs Google Cloud CLI (gcloud) for Google Cloud Platform development
- [zip](./src/zip/README.md): Installs zip and unzip CLI tools for compression and extraction

## Usage

To use the features from this repository, add the desired features to devcontainer.json.

These examples show how to use features from this repository in a devcontainer:

```jsonc
{
    "image": "mcr.microsoft.com/devcontainers/base:ubuntu",
    "features": {
        "ghcr.io/skyred/features/ag:1": {},
        "ghcr.io/skyred/features/agentcore-cli:1": {},
        "ghcr.io/skyred/features/amazon-q-cli:1": {},
        "ghcr.io/skyred/features/aws-sam-cli:1": {},
        "ghcr.io/skyred/features/gcloud-cli:1": {},
        "ghcr.io/skyred/features/zip:1": {}
    }
}
```

Or use individual features with an additonal plugin:

```jsonc
{
    "image": "mcr.microsoft.com/devcontainers/base:ubuntu",
    "features": {
        "ghcr.io/skyred/features/gcloud-cli:1": {
            "installGkeAuthPlugin": true
        }
    }
}
```

## Repo and Feature Structure

Similar to the [`devcontainers/features`](https://github.com/devcontainers/features) repo, this repository has a `src` folder. Each feature has its own sub-folder, containing at least a `devcontainer-feature.json` and an entrypoint script `install.sh`.

```plaintext
├── src
│   ├── ag
│   │   ├── devcontainer-feature.json
│   │   ├── install.sh
│   │   └── README.md
│   ├── agentcore-cli
│   │   ├── devcontainer-feature.json
│   │   ├── install.sh
│   │   └── README.md
│   ├── amazon-q-cli
│   │   ├── devcontainer-feature.json
│   │   ├── install.sh
│   │   └── README.md
│   ├── aws-sam-cli
│   │   ├── devcontainer-feature.json
│   │   ├── install.sh
│   │   └── README.md
│   ├── gcloud-cli
│   │   ├── devcontainer-feature.json
│   │   ├── install.sh
│   │   └── README.md
│   ├── zip
│   │   ├── devcontainer-feature.json
│   │   ├── install.sh
│   │   └── README.md
├── test
│   ├── ag
│   ├── agentcore-cli
│   ├── amazon-q-cli
│   ├── aws-sam-cli
│   ├── gcloud-cli
│   └── zip
...
```

An [implementing tool](https://containers.dev/supporting#tools) will composite [the documented dev container properties](https://containers.dev/implementors/features/#devcontainer-feature-json-properties) from the feature's `devcontainer-feature.json` file, and execute in the `install.sh` entrypoint script in the container during build time. Implementing tools are also free to process attributes under the `customizations` property as desired.
