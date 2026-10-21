FROM alpine:3.24

LABEL org.opencontainers.image.source="https://github.com/impleflow/ci-images" \
      org.opencontainers.image.description="Alpine 3.24 + bash, ShellCheck and shfmt for offline CI" \
      org.opencontainers.image.licenses="Apache-2.0"

# The tool versions come from the Alpine release (see the VERSION file), so they change only with the base image.
# The RUN fails the build if a tool is missing.
RUN apk add --no-cache bash shellcheck shfmt \
    && bash --version | head -n 1 \
    && shellcheck --version \
    && shfmt --version
