# ci-images

Docker images for CI validation jobs (formatting, linting, tests). All tools are baked in at build time, so the jobs run **without internet access**.

Images are published to `ghcr.io/impleflow/<directory>`.

| Image | Base | Contents |
|-------|------|----------|
| `dev-java` | `eclipse-temurin:25-jdk-alpine` | google-java-format, SpotBugs |
| `dev-python` | `python:3.13-slim` | PyYAML, pytest, ruff, editorconfig-checker |

Tool versions are pinned in each `Dockerfile` (Java) or `requirements.txt` (Python). The Java tool versions must match the ones used in the consuming projects' `.gitlab-ci.yml`.
