FROM ubuntu:22.04

# Avoid interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Install necessary packages
RUN apt-get update && apt-get install -y \
    curl \
    git \
    unzip \
    xz-utils \
    zip \
    libglu1-mesa \
    wget \
    clang \
    cmake \
    ninja-build \
    pkg-config \
    libgtk-3-dev \
    && rm -rf /var/lib/apt/lists/*

# Create a non-root user
RUN useradd -ms /bin/bash vscode
USER vscode
WORKDIR /home/vscode

# Install Flutter
RUN git clone https://github.com/flutter/flutter.git -b stable /home/vscode/flutter

# Add flutter to PATH
ENV PATH="/home/vscode/flutter/bin:${PATH}"

# Pre-download Flutter artifacts
RUN flutter precache

# Enable Flutter web support
RUN flutter config --enable-web

# Verify installation
RUN flutter doctor
