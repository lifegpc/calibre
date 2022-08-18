FROM ubuntu:latest
RUN apt update && apt install -y \
    autoconf \
    automake \
    bison \
    build-essential \
    ca-certificates \
    cmake \
    curl \
    flex \
    gawk \
    gettext \
    gperf \
    git \
    libasound2 \
    libdotconf-dev \
    libgcrypt20-dev \
    libgdbm-dev \
    libgdbm-compat-dev \
    libgl1-mesa-dev \
    libgles2-mesa-dev \
    libglu1-mesa-dev \
    libgpg-error-dev \
    libjxr-dev \
    libnss3-dev \
    libsndfile1-dev \
    libssl-dev \
    libtool \
    libudev-dev \
    libwayland-dev \
    libwayland-egl1-mesa \
    libwayland-server0 \
    libxcomposite1 \
    libxdamage1 \
    libxkbcommon-dev \
    libxkbfile1 \
    libxrandr2 \
    libxrender1 \
    libxtst6 \
    openssl \
    pkg-config \
    nasm \
    sudo \
    unzip \
    uuid-dev \
    zlib1g-dev
RUN cd /root && curl -L "https://github.com/lifegpc/calibre/raw/master/bypy/sources.json" -o sources.json && \
    curl -L "https://github.com/lifegpc/calibre-sources-json-get/releases/download/0.1.0/csjg" -o /usr/bin/csjg && \
    chmod 755 /usr/bin/csjg
RUN useradd -ms /bin/bash calibre && \
    usermod -aG sudo calibre && \
    echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
USER calibre
