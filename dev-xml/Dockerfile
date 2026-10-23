FROM alpine:3.24

LABEL org.opencontainers.image.source="https://github.com/impleflow/ci-images" \
      org.opencontainers.image.description="Alpine 3.24 + xmllint (libxml2) for offline CI" \
      org.opencontainers.image.licenses="Apache-2.0"

# Must match XMLLINT_VERSION in the projects' .gitlab-ci.yml (the image tag carries it).
# The version is a prefix of the Alpine package version (e.g. 2.13.9 for 2.13.9-r2), so the build fails
# if the Alpine release no longer ships it.
ARG XMLLINT_VERSION=2.13.9

RUN apk add --no-cache "libxml2-utils~=${XMLLINT_VERSION}" \
    && xmllint --version
