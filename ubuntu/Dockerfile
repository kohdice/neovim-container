FROM ubuntu:22.04

LABEL maintainer="kohdice <kohdice@gmail.com>"

ENV GOPATH=$HOME/go
ENV PYTHONUNBUFFERED 1
ENV PYTHONPATH=/workspace
ENV POETRY_HOME=/opt/poetry
ENV TZ=Asia/Tokyo

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    curl \
    exa \
    gcc \
    git \
    fish \
    fzf \
    make \
    ripgrep \
    software-properties-common \
    sudo \
    tar \
    tmux \
    tzdata \
    unzip \
    wget \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Go, Node, Python
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
        && add-apt-repository ppa:deadsnakes/ppa \
        && add-apt-repository ppa:longsleep/golang-backports \
        && apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
        golang-go \
        nodejs \
        python3.10 \
        python3-pip \
        python3-setuptools \
        python3-wheel \
        && apt-get clean \
        && rm -rf /var/lib/apt/lists/*

# Neovim
RUN wget https://github.com/neovim/neovim/releases/download/v0.9.1/nvim-linux64.tar.gz \
    && tar -zxvf nvim-linux64.tar.gz \
    && mv nvim-linux64/bin/nvim usr/bin/nvim \
    && mv nvim-linux64/lib/nvim usr/lib/nvim \
    && mv nvim-linux64/share/nvim/ usr/share/nvim \
    && rm -rf nvim-linux64 \
    && rm nvim-linux64.tar.gz

WORKDIR /workspace
