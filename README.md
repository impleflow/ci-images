# ci-images

Docker images for CI validation jobs (formatting, linting, tests). All tools are baked in at build time, so the jobs run **without internet access**.

Images are published to `ghcr.io/impleflow/<directory>`.

| Image | Base | Contents |
|-------|------|----------|
| `dev-java` | `eclipse-temurin:25-jdk-alpine` | google-java-format, SpotBugs |
| `dev-python` | `python:3.14-slim` | PyYAML, pytest, ruff, editorconfig-checker |
| `dev-shell` | `alpine:3.24` | bash, ShellCheck, shfmt |

Tool versions are pinned in each `Dockerfile` (Java) or `requirements.txt` (Python). In `dev-shell` they are set by the Alpine release (the tag is the Alpine version). The Java tool versions must match the ones used in the consuming projects' `.gitlab-ci.yml`.
