FROM ubuntu:22.04

LABEL maintainer="kohdice <kohdice@gmail.com>"

ENV GOPATH=$HOME/go
ENV PYTHONUNBUFFERED 1
ENV PYTHONPATH=/root/workspace
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
    peco \
    tmux \
    tzdata \
    sudo \
    ninja-build \
    gettext \
    libtool-bin \
    cmake \
    g++ \
    pkg-config \
    unzip \
    software-properties-common

RUN curl -sfLS install-node.now.sh/lts | bash -s -- --yes \
    && add-apt-repository ppa:deadsnakes/ppa \
    && add-apt-repository ppa:longsleep/golang-backports \
    && apt-get install -y \
    python3.10 \
    python3-pip \
    python3-setuptools \
    python3-wheel \
    golang-go \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /root/workspace
