FROM ubuntu:latest
RUN apt update && apt install -y \
    autoconf \
    automake \
    build-essential \
    cmake \
    curl \
    gawk \
    git \
    libgdbm-dev \
    libgdbm-compat-dev \
    libtool \
    pkg-config \
    nasm \
    sudo \
    uuid-dev \
    zlib1g-dev
RUN cd /root && curl -L "https://github.com/lifegpc/calibre/raw/master/bypy/sources.json" -o sources.json && \
    curl -L "https://github.com/lifegpc/calibre-sources-json-get/releases/download/0.1.0/csjg" -o /usr/bin/csjg && \
    chmod 755 /usr/bin/csjg
# bzip2
RUN FILENAME=$(csjg -f /root/sources.json -n bzip2 -F) && \
    URL=$(csjg -f /root/sources.json -n bzip2 -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    make -j $(nproc) 'CFLAGS=-fPIC -Wall -Winline -O2 -g -D_FILE_OFFSET_BITS=64' && \
    make install PREFIX=/usr && cd /root && rm -rf $TMP
# xz
RUN FILENAME=$(csjg -f /root/sources.json -n xz -F) && \
    URL=$(csjg -f /root/sources.json -n xz -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# unrar
RUN FILENAME=$(csjg -f /root/sources.json -n unrar -F) && \
    URL=$(csjg -f /root/sources.json -n unrar -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd unrar && \
    make -j $(nproc) && make install PREFIX=/usr && cd /root && rm -rf $TMP
# brotli
RUN FILENAME=$(csjg -f /root/sources.json -n brotli -F) && \
    URL=$(csjg -f /root/sources.json -n brotli -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    mkdir build && cd build && cmake -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    make -j $(nproc) && make install && cd /root && rm -rf $TMP
# expat
RUN FILENAME=$(csjg -f /root/sources.json -n expat -F) && \
    URL=$(csjg -f /root/sources.json -n expat -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xjvf "$FILENAME" && cd $DIR && \
    ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# sqlite
RUN FILENAME=$(csjg -f /root/sources.json -n sqlite -F) && \
    URL=$(csjg -f /root/sources.json -n sqlite -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    ./configure --prefix=/usr --enable-session && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# libffi
RUN FILENAME=$(csjg -f /root/sources.json -n libffi -F) && \
    URL=$(csjg -f /root/sources.json -n libffi -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    ./configure --prefix=/usr --enable-portable-binary && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# hyphen
RUN FILENAME=$(csjg -f /root/sources.json -n hyphen -F) && \
    URL=$(csjg -f /root/sources.json -n hyphen -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# openssl
RUN FILENAME=$(csjg -f /root/sources.json -n openssl -F) && \
    URL=$(csjg -f /root/sources.json -n openssl -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    ./config --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP && cp -rv /usr/lib64/* /usr/lib
# ncurses
RUN FILENAME=$(csjg -f /root/sources.json -n ncurses -F) && \
    URL=$(csjg -f /root/sources.json -n ncurses -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# readline
RUN FILENAME=$(csjg -f /root/sources.json -n readline -F) && \
    URL=$(csjg -f /root/sources.json -n readline -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# python
RUN FILENAME=$(csjg -f /root/sources.json -n python -F) && \
    URL=$(csjg -f /root/sources.json -n python -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xJvf "$FILENAME" && cd $DIR && \
    ./configure --prefix=/usr --enable-optimizations --enable-ipv6 --with-lto && \
    make -j $(nproc) && make install && cd /root && rm -rf $TMP && \
    ln -s /usr/bin/python3 /usr/bin/python && ln -s /usr/bin/pip3 /usr/bin/pip
RUN useradd -ms /bin/bash calibre && \
    usermod -aG sudo calibre && \
    echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
USER calibre
