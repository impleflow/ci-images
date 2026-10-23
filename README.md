# ci-images

Docker images for CI validation jobs (formatting, linting, tests). All tools are baked in at build time, so the jobs run **without internet access**.

Images are published to `ghcr.io/impleflow/<directory>`.

| Image | Base | Contents |
|-------|------|----------|
| `dev-java` | `eclipse-temurin:25-jdk-alpine` | google-java-format (1.37.0), SpotBugs (4.10.5) |
| `dev-python` | `python:3.14-slim` | PyYAML (>= 6.0.3), pytest (>= 9.1), ruff (>= 0.17), editorconfig-checker (>= 3.11) |
| `dev-shell` | `alpine:3.24` | bash (5.3.9), ShellCheck (0.11.0), shfmt (3.13.1) |
| `dev-xml` | `alpine:3.24` | xmllint (2.13.9, libxml2-utils) |

Tags: `<VERSION>` and `<VERSION>-<YYYYMMDD>`. `dev-java` also gets one tag per tool, `<VERSION>-gjf<google-java-format>` and `<VERSION>-spotbugs<SpotBugs>` (e.g. `25-gjf1.37.0`, `25-spotbugs4.10.5`), taken from the `ARG`s in its Dockerfile. Each tag guarantees only that tool's version - the other tool in the image may differ between builds. `dev-xml` gets `<VERSION>-xmllint<xmllint>` (e.g. `3.24-xmllint2.13.9`) in the same way.


