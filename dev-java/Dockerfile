FROM eclipse-temurin:25-jdk

LABEL org.opencontainers.image.source="https://github.com/impleflow/ci-images" \
      org.opencontainers.image.description="Eclipse Temurin 25 JDK + google-java-format and SpotBugs for offline CI" \
      org.opencontainers.image.licenses="Apache-2.0"

# Versions must match GJF_VERSION / SPOTBUGS_VERSION in the projects' .gitlab-ci.yml.
# The version is part of the file name, so a job can check that the image has the version it requires.
# The base image has no curl - files are fetched by ADD.
ARG GJF_VERSION=1.36.0
ARG SPOTBUGS_VERSION=4.10.4

ADD --chmod=644 "https://github.com/google/google-java-format/releases/download/v${GJF_VERSION}/google-java-format-${GJF_VERSION}-all-deps.jar" \
    /opt/tools/google-java-format-${GJF_VERSION}-all-deps.jar
ADD "https://github.com/spotbugs/spotbugs/releases/download/${SPOTBUGS_VERSION}/spotbugs-${SPOTBUGS_VERSION}.tgz" /tmp/spotbugs.tgz

# ADD from a URL does not unpack archives
RUN tar xzf /tmp/spotbugs.tgz -C /opt/tools \
    && rm /tmp/spotbugs.tgz \
    && test -f "/opt/tools/spotbugs-${SPOTBUGS_VERSION}/lib/spotbugs.jar"
