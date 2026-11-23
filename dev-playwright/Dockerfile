FROM node:22-bookworm

LABEL org.opencontainers.image.source="https://github.com/impleflow/ci-images" \
      org.opencontainers.image.description="Node 22 + Playwright Chromium with its system libraries for offline CI" \
      org.opencontainers.image.licenses="Apache-2.0"

# Must equal VERSION. The project's @playwright/test must use the same version, otherwise Playwright looks for
# a browser build that is not in the image and tries to download it (jobs have no internet access).
ARG PLAYWRIGHT_VERSION=1.65.1

# Browsers in a fixed path, readable by any user the job runs as.
ENV PLAYWRIGHT_BROWSERS_PATH=/ms-playwright

# Chromium only (no Firefox/WebKit); --with-deps installs the system libraries through apt.
# The RUN fails the build if the browser does not start.
RUN npx -y "playwright@${PLAYWRIGHT_VERSION}" install --with-deps chromium \
    && chmod -R a+rX /ms-playwright \
    && rm -rf /var/lib/apt/lists/* /root/.npm \
    && ls /ms-playwright \
    && "$(ls -d /ms-playwright/chromium-*/chrome-linux*/ | head -n 1)chrome" --version
