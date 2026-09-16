FROM mcr.microsoft.com/devcontainers/python:3.11-bookworm

# Install system dependencies for C++ and ESPHome compilation
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    clang \
    clang-format \
    && rm -rf /var/lib/apt/lists/*

# Install ESPHome
RUN pip3 install --no-cache-dir esphome

# Install Antigravity CLI (agy) globally for system-wide access
RUN curl -fsSL https://antigravity.google/cli/install.sh | bash && \
    if [ -f /root/.local/bin/agy ]; then mv /root/.local/bin/agy /usr/local/bin/agy; fi

# Install Antigravity CLI for the non-root 'vscode' user
USER vscode
RUN curl -fsSL https://antigravity.google/cli/install.sh | bash

# Ensure the local bin path is in the vscode user's PATH
ENV PATH="/home/vscode/.local/bin:${PATH}"
