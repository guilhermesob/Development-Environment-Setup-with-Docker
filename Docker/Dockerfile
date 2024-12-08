# Debian-based development environment
FROM debian:bullseye AS debian-base

# Set environment variables
ENV DEBIAN_FRONTEND=noninteractive

# Install development tools and dependencies
RUN apt-get update && apt-get install -y \
    curl \
    git \
    wget \
    build-essential \
    clang \
    python3 \
    python3-pip \
    ruby \
    ruby-dev \
    nodejs \
    npm \
    neovim \
    vim \
    && apt-get clean

# Install Ruby on Rails
RUN gem install rails bundler

# Set the default shell
SHELL ["/bin/bash", "-c"]

# ======================================================================

# Arch Linux-based development environment
FROM archlinux:base AS arch-base

# Install development tools and dependencies
RUN pacman -Sy --noconfirm --needed \
    base-devel \
    clang \
    git \
    wget \
    python \
    python-pip \
    ruby \
    ruby-bundler \
    nodejs \
    npm \
    neovim \
    vim

# Install Ruby on Rails
RUN gem install rails

# Set the default shell
SHELL ["/bin/bash", "-c"]

# ======================================================================

# Final stage (use --target to select the base image)
FROM debian-base AS final

# Working directory
WORKDIR /workspace

# Expose development files volume
VOLUME /workspace

# Default command
CMD ["bash"]
