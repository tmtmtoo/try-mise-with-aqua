FROM mcr.microsoft.com/devcontainers/base:bullseye

RUN apt-get update \
    && apt-get -y --no-install-recommends install \
    sudo \
    curl \
    git \
    ca-certificates \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

SHELL ["/bin/bash", "-o", "pipefail", "-c"]
ENV MISE_DATA_DIR="/mise"
ENV MISE_CONFIG_DIR="/mise"
ENV MISE_CACHE_DIR="/mise/cache"
ENV MISE_INSTALL_PATH="/usr/local/bin/mise"
ENV PATH="/mise/shims:$PATH"
# ENV MISE_VERSION="..."

RUN gpg --keyserver hkps://keyserver.ubuntu.com --recv-keys 0x7413A06D \
    && curl https://mise.jdx.dev/install.sh.sig | gpg --decrypt > install.sh \
    && sh ./install.sh
