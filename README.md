# Pre-pull Docker Compose Selectively Service Images Action

## 🚀 Overview

When running `docker compose --dry-run`, image pulls are only simulated which can cause the dry-run to fail since no actual images are pulled. This action **pre-pull images for services in Docker Compose selectively in parallel** rather than pulling images for every single defined service in a Compose file.

## 🛠️ Inputs

| Input             | Required | Default | Description                                                               |
| ----------------- | -------- | ------- | ------------------------------------------------------------------------- |
| `services`        | ✅       | —       | Space or new-line separated list of Docker Compose service names to pull. |
| `compose_profile` | ❌       | `""`    | Docker Compose profile to use. Optional.                                  |
| `env_file`        | ❌       | `.env`  | Path to `.env` file for Docker Compose.                                   |

---

## 📖 Usage

### Example 1

```yaml
---
steps:
  - name: Checkout repository
    uses: actions/checkout@v4

  - name: Pre-pull service images
    uses: https://git.trez.wtf/Trez/docker-select-image-pull@main
    with:
      services: "web db"
```

### Example 2

```yaml
steps:
  - name: Checkout repository
    uses: actions/checkout@v4

  - name: Pre-pull service images
    uses: https://git.trez.wtf/Trez/docker-select-image-pull@main
    with:
      services: |
        web
        db
```
