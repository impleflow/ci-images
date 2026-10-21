# ci-images

Docker images for CI validation jobs (formatting, linting, tests). All tools are baked in at build time, so the jobs run **without internet access**.

Images are published to `ghcr.io/impleflow/<directory>`.

| Image | Base | Contents |
|-------|------|----------|
| `dev-java` | `eclipse-temurin:25-jdk-alpine` | google-java-format (1.37.0), SpotBugs (4.10.5) |
| `dev-python` | `python:3.14-slim` | PyYAML (>= 6.0.3), pytest (>= 9.1), ruff (>= 0.17), editorconfig-checker (>= 3.11) |
| `dev-shell` | `alpine:3.24` | bash (5.3.9), ShellCheck (0.11.0), shfmt (3.13.1) |


