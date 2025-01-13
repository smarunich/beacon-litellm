# Beacon LiteLLM

A containerized LiteLLM proxy service with Kubernetes support for scalable LLM request handling.

## Features
- PostgreSQL database integration for request logging and monitoring
- Kubernetes-ready deployment configuration
- Configurable master key and security settings
- Support for Slack alerting
- Prometheus metrics integration
- Connection pooling and timeout management

## Quick Start

### Prerequisites
- [Task](https://taskfile.dev) installed
- Kubernetes cluster access
- Docker installed
- AWS credentials configured (for Bedrock access)

### Deployment
1. Configure your database settings in `config.yaml`
2. Set your master key and desired configuration options
3. Deploy using Task commands:

```bash
# Initialize configuration and secrets
task init

# Deploy LiteLLM proxy (includes init and postgres-deploy)
task deploy

# Check deployment status
task status
```

Alternatively, for local Docker deployment:
```bash
task build-and-push
docker run -p 4000:4000 us-east1-docker.pkg.dev/dogfood-cx/registryrepository/litellm:main-latest
```

## Configuration
See `config.yaml` for available configuration options including:
- Database connection settings
- Alerting configuration
- Performance tuning parameters
- Logging preferences

Default service port: 4000
