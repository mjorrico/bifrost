# Bifrost Sandbox

A local sandbox environment for the Bifrost AI gateway, pre-configured for routing, governance, and multi-provider integrations.

## Architecture

- **`config.json`**: The core ruleset. Configures authentication, logging, a PostgreSQL storage backend, and connections to LLM providers (AWS Bedrock, Anthropic, ModelArk). It reads sensitive credentials dynamically from environment variables.
- **`compose.yaml`**: Deploys the Bifrost server (`maximhq/bifrost:v1.4.18`). It mounts the local `config.json` into the container and injects secrets via a `.env` file.

## Prerequisites

- **PostgreSQL Database**: A Postgres server must already be running on the same Docker network (`pgvector_network`). It must be reachable at the hostname defined in your `.env` (e.g., `pgvector`) and contain a pre-created database with the exact name specified in your `.env` (e.g., `bifrost`).

## Quick Start

1. **Environment**: Create a `.env` file in the root directory with your database credentials and API keys.
2. **Run**:
    ```bash
    docker compose up -d
    ```
