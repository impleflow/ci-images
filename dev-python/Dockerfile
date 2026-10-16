FROM python:3.13-slim

LABEL org.opencontainers.image.source="https://github.com/impleflow/ci-images" \
      org.opencontainers.image.description="Python 3.13 + PyYAML, pytest, ruff and editorconfig-checker for offline CI" \
      org.opencontainers.image.licenses="Apache-2.0"

ENV PIP_NO_CACHE_DIR=1 \
    PIP_DISABLE_PIP_VERSION_CHECK=1

COPY requirements.txt /tmp/requirements.txt
RUN pip install -r /tmp/requirements.txt && rm /tmp/requirements.txt
