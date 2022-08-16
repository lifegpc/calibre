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
    make -j $(nproc) && make install PREFIX=/usr && make clean && make lib -j $(nproc) && \
    make install-lib PREFIX=/usr && mkdir /usr/include/unrar && install -m 644 dll.hpp /usr/include/unrar && \
    cd /root && rm -rf $TMP
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
# RUN FILENAME=$(csjg -f /root/sources.json -n openssl -F) && \
#     URL=$(csjg -f /root/sources.json -n openssl -u0) && \
#     TMP=$(mktemp -d) && cd $TMP && \
#     DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
#     curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
#     ./config --prefix=/usr && make -j $(nproc) && make install && \
#     cd /root && rm -rf $TMP && cp -rv /usr/lib64/* /usr/lib
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
# icu
RUN FILENAME=$(csjg -f /root/sources.json -n icu -F) && \
    URL=$(csjg -f /root/sources.json -n icu -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd icu/source/ && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC ./configure --prefix=/usr --enable-static && \
    make -j $(nproc) && make install && cd /root && rm -rf $TMP
# libstemmer
RUN FILENAME=$(csjg -f /root/sources.json -n libstemmer -F) && \
    URL=$(csjg -f /root/sources.json -n libstemmer -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    make -j $(nproc) 'CFLAGS=-fPIC -O2' && \
    install -m 644 libstemmer.a /usr/lib && \
    install -m 644 include/libstemmer.h /usr/include && \
    cd /root && rm -rf $TMP
# libjpeg
RUN FILENAME=$(csjg -f /root/sources.json -n libjpeg -F) && \
    URL=$(csjg -f /root/sources.json -n libjpeg -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    mkdir build && cd build && CFLAGS=-fPIC cmake -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    make -j $(nproc) && make install && cd /root && rm -rf $TMP
# libpng
RUN FILENAME=$(csjg -f /root/sources.json -n libpng -F) && \
    URL=$(csjg -f /root/sources.json -n libpng -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xJvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# libwebp
RUN FILENAME=$(csjg -f /root/sources.json -n libwebp -F) && \
    URL=$(csjg -f /root/sources.json -n libwebp -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# freetype
RUN FILENAME=$(csjg -f /root/sources.json -n freetype -F) && \
    URL=$(csjg -f /root/sources.json -n freetype -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xJvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# graphite
RUN FILENAME=$(csjg -f /root/sources.json -n graphite -F) && \
    URL=$(csjg -f /root/sources.json -n graphite -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    mkdir build && cd build && CFLAGS=-fPIC cmake -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    make -j $(nproc) && make install && cd /root && rm -rf $TMP
# fontconfig
RUN FILENAME=$(csjg -f /root/sources.json -n fontconfig -F) && \
    URL=$(csjg -f /root/sources.json -n fontconfig -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xJvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# iconv
RUN FILENAME=$(csjg -f /root/sources.json -n iconv -F) && \
    URL=$(csjg -f /root/sources.json -n iconv -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC ./configure --enable-static --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# libxml2
RUN FILENAME=$(csjg -f /root/sources.json -n libxml2 -F) && \
    URL=$(csjg -f /root/sources.json -n libxml2 -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xJvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# libxslt
RUN FILENAME=$(csjg -f /root/sources.json -n libxslt -F) && \
    URL=$(csjg -f /root/sources.json -n libxslt -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xJvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# chmlib
RUN FILENAME=$(csjg -f /root/sources.json -n chmlib -F) && \
    URL=$(csjg -f /root/sources.json -n chmlib -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xjvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# optipng
RUN FILENAME=$(csjg -f /root/sources.json -n optipng -F) && \
    URL=$(csjg -f /root/sources.json -n optipng -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# mozjpeg
RUN FILENAME=$(csjg -f /root/sources.json -n mozjpeg -F) && \
    URL=$(csjg -f /root/sources.json -n mozjpeg -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    mkdir build && cd build && CFLAGS=-fPIC cmake -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    make -j $(nproc) && make install && cd /root && rm -rf $TMP
# libusb
RUN FILENAME=$(csjg -f /root/sources.json -n libusb -F) && \
    URL=$(csjg -f /root/sources.json -n libusb -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xjvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && \
    make install && cd /root && rm -rf $TMP
# libmtp
RUN FILENAME=$(csjg -f /root/sources.json -n libmtp -F) && \
    URL=$(csjg -f /root/sources.json -n libmtp -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# openjpeg
RUN FILENAME=$(csjg -f /root/sources.json -n openjpeg -F) && \
    URL=$(csjg -f /root/sources.json -n openjpeg -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    mkdir build && cd build && CFLAGS=-fPIC cmake -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    make -j $(nproc) && make install && cd /root && rm -rf $TMP
# poppler
RUN FILENAME=$(csjg -f /root/sources.json -n poppler -F) && \
    URL=$(csjg -f /root/sources.json -n poppler -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xJvf "$FILENAME" && cd $DIR && \
    mkdir build && cd build && CFLAGS=-fPIC CXXFLAGS=-fPIC cmake \
        -DCMAKE_INSTALL_PREFIX=/usr -DENABLE_BOOST=OFF ../ && \
    make -j $(nproc) && make install && cd /root && rm -rf $TMP
# podofo
RUN FILENAME=$(csjg -f /root/sources.json -n podofo -F) && \
    URL=$(csjg -f /root/sources.json -n podofo -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    mkdir build && cd build && CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    make -j $(nproc) && make install && cd /root && rm -rf $TMP
# PRCE
RUN TMP=$(mktemp -d) && cd $TMP && \
    curl -L "https://sourceforge.net/projects/pcre/files/pcre/8.45/pcre-8.45.tar.bz2/download" -o "pcre-8.45.tar.bz2" && \
    tar -xjvf "pcre-8.45.tar.bz2" && cd pcre-8.45 && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && \
    make install && cd /root && rm -rf $TMP
RUN pip install meson ninja
# glib
RUN FILENAME=$(csjg -f /root/sources.json -n glib -F) && \
    URL=$(csjg -f /root/sources.json -n glib -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xJvf "$FILENAME" && cd $DIR && \
    LDFLAGS='-liconv' meson setup build --buildtype=release --prefix=/usr && cd build && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
# dbus
RUN FILENAME=$(csjg -f /root/sources.json -n dbus -F) && \
    URL=$(csjg -f /root/sources.json -n dbus -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# dbusglib
RUN FILENAME=$(csjg -f /root/sources.json -n dbusglib -F) && \
    URL=$(csjg -f /root/sources.json -n dbusglib -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# hunspell
RUN FILENAME=$(csjg -f /root/sources.json -n hunspell -F) && \
    URL=$(csjg -f /root/sources.json -n hunspell -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# node.js
# RUN FILENAME=$(csjg -f /root/sources.json -n nodejs -F) && \
#     URL=$(csjg -f /root/sources.json -n nodejs -u0) && \
#     TMP=$(mktemp -d) && cd $TMP && \
#     curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd node-* && \
#     python configure.py --prefix=/usr --enable-lto --ninja && make -j $(nproc) && \
#     make install && cd /root && rm -rf $TMP
RUN curl -L "https://nodejs.org/dist/v16.16.0/node-v16.16.0-linux-x64.tar.xz" -o node-v16.16.0-linux-x64.tar.xz && \
    tar -xJvf "node-v16.16.0-linux-x64.tar.xz" && cp -rv node-v16.16.0-linux-x64/* /usr && \
    rm -rf node-v16.16.0-linux-x64 node-v16.16.0-linux-x64.tar.xz
# double-conversion
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=double-conversion-3.2.1.tar.gz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://github.com/google/double-conversion/archive/refs/tags/v3.2.1.tar.gz" -o $FILENAME && \
    tar -xzvf $FILENAME && cd $DIR && \
    mkdir build && cd build && CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    make -j $(nproc) && make install && cd /root && rm -rf $TMP
# md4c
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=md4c-release-0.4.8.tar.gz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://github.com/mity/md4c/archive/refs/tags/release-0.4.8.tar.gz" -o $FILENAME && \
    tar -xzvf $FILENAME && cd $DIR && \
    mkdir build && cd build && CFLAGS=-fPIC cmake -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    make -j $(nproc) && make install && cd /root && rm -rf $TMP
# qt-base
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=qtbase-everywhere-src-6.3.1.tar.xz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://download.qt.io/archive/qt/6.3/6.3.1/submodules/qtbase-everywhere-src-6.3.1.tar.xz" -o $FILENAME && \
    tar -xJvf $FILENAME && cd $DIR && ./configure -prefix /usr && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
# qt-svg
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=qtsvg-everywhere-src-6.3.1.tar.xz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://download.qt.io/archive/qt/6.3/6.3.1/submodules/qtsvg-everywhere-src-6.3.1.tar.xz" -o $FILENAME && \
    tar -xJvf $FILENAME && cd $DIR && mkdir build && cd build && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
# qt-shadertools
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=qtshadertools-everywhere-src-6.3.1.tar.xz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://download.qt.io/archive/qt/6.3/6.3.1/submodules/qtshadertools-everywhere-src-6.3.1.tar.xz" -o $FILENAME && \
    tar -xJvf $FILENAME && cd $DIR && mkdir build && cd build && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
# qt-declarative
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=qtdeclarative-everywhere-src-6.3.1.tar.xz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://download.qt.io/archive/qt/6.3/6.3.1/submodules/qtdeclarative-everywhere-src-6.3.1.tar.xz" -o $FILENAME && \
    tar -xJvf $FILENAME && cd $DIR && mkdir build && cd build && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
# qt-imageformats
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=qtimageformats-everywhere-src-6.3.1.tar.xz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://download.qt.io/archive/qt/6.3/6.3.1/submodules/qtimageformats-everywhere-src-6.3.1.tar.xz" -o $FILENAME && \
    tar -xJvf $FILENAME && cd $DIR && mkdir build && cd build && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
# qt-websockets
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=qtwebsockets-everywhere-src-6.3.1.tar.xz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://download.qt.io/archive/qt/6.3/6.3.1/submodules/qtwebsockets-everywhere-src-6.3.1.tar.xz" -o $FILENAME && \
    tar -xJvf $FILENAME && cd $DIR && mkdir build && cd build && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
# qt-webchannel
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=qtwebchannel-everywhere-src-6.3.1.tar.xz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://download.qt.io/archive/qt/6.3/6.3.1/submodules/qtwebchannel-everywhere-src-6.3.1.tar.xz" -o $FILENAME && \
    tar -xJvf $FILENAME && cd $DIR && mkdir build && cd build && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
# qt-positioning
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=qtpositioning-everywhere-src-6.3.1.tar.xz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://download.qt.io/archive/qt/6.3/6.3.1/submodules/qtpositioning-everywhere-src-6.3.1.tar.xz" -o $FILENAME && \
    tar -xJvf $FILENAME && cd $DIR && mkdir build && cd build && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
# qt-wayland
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=qtwayland-everywhere-src-6.3.1.tar.xz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://download.qt.io/archive/qt/6.3/6.3.1/submodules/qtwayland-everywhere-src-6.3.1.tar.xz" -o $FILENAME && \
    tar -xJvf $FILENAME && cd $DIR && mkdir build && cd build && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
# qt-sensors
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=qtsensors-everywhere-src-6.3.1.tar.xz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://download.qt.io/archive/qt/6.3/6.3.1/submodules/qtsensors-everywhere-src-6.3.1.tar.xz" -o $FILENAME && \
    tar -xJvf $FILENAME && cd $DIR && mkdir build && cd build && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
RUN pip install setuptools==57.4.0 html5lib==1.1
# libcups2
RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=cups-2.4.2.tar.gz && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "https://github.com/OpenPrinting/cups/releases/download/v2.4.2/cups-2.4.2-source.tar.gz" -o $FILENAME && \
    tar -xzvf $FILENAME && cd $DIR && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP
# qt-webengine
# RUN TMP=$(mktemp -d) && cd $TMP && FILENAME=qtwebengine-everywhere-src-6.3.1.tar.xz && \
#     DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
#     curl -L "https://download.qt.io/archive/qt/6.3/6.3.1/submodules/qtwebengine-everywhere-src-6.3.1.tar.xz" -o $FILENAME && \
#     tar -xJf $FILENAME && rm $FILENAME && cd $DIR && mkdir build && cd build && \
#     CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/usr ../ && \
#     ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
RUN pip install six==1.16.0 unrardll==0.1.5 lxml==4.9.1 pychm==0.8.6 html5-parser==0.4.10 css-parser==1.0.7 \
    python-dateutil==2.8.2 jeepney==0.7.1 dnspython==2.1.0 mechanize==0.4.7 feedparser==6.0.8 sgmllib3k==1.0.0 \
    markdown==3.3.6 html2text==2020.1.16 soupsieve==2.3.1 beautifulsoup4==4.10.0 regex==2021.11.10 chardet==4.0.0
# uchardet
RUN FILENAME=$(csjg -f /root/sources.json -n uchardet -F) && \
    URL=$(csjg -f /root/sources.json -n uchardet -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xJvf "$FILENAME" && cd $DIR && mkdir build && cd build && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC cmake -G Ninja -DCMAKE_INSTALL_PREFIX=/usr ../ && \
    ninja -j $(nproc) && ninja install && cd /root && rm -rf $TMP
RUN pip install msgpack==1.0.3 pygments==2.10.0 pycryptodome==3.11.0
# apsw
RUN FILENAME=$(csjg -f /root/sources.json -n apsw -F) && \
    URL=$(csjg -f /root/sources.json -n apsw -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && \
    curl -L "$URL" -o "$FILENAME" && unzip "$FILENAME" && cd $DIR && \
    python setup.py install && cd /root && rm -rf $TMP
RUN pip install webencodings==0.5.1 pillow==8.4.0 netifaces==0.11.0 psutil==5.8.0 ifaddr==0.1.7 \
    texttable==1.6.4 multivolumefile==0.2.3 brotli==1.0.9 pyzstd==0.15.0 \
    pyppmd==0.17.3 py7zr==0.16.3 zeroconf==0.37.0 toml==0.10.2 pyparsing==3.0.6 ply==3.11 \
    packaging==21.3 sip==6.6.2 PyQt-builder==1.13.0 PyQt6-sip==13.4.0 PyQt6==6.3.1 \
    PyQt6-WebEngine==6.3.1
# speech-dispatcher-client
RUN FILENAME=$(csjg -f /root/sources.json -n speech-dispatcher-client -F) && \
    URL=$(csjg -f /root/sources.json -n speech-dispatcher-client -u0) && \
    TMP=$(mktemp -d) && cd $TMP && \
    DIR=${FILENAME%.*} && DIR=${DIR%.*} && \
    curl -L "$URL" -o "$FILENAME" && tar -xzvf "$FILENAME" && cd $DIR && \
    CFLAGS=-fPIC CXXFLAGS=-fPIC ./configure --prefix=/usr && make -j $(nproc) && make install && \
    cd /root && rm -rf $TMP || make install && cd /root && rm -rf $TMP
RUN useradd -ms /bin/bash calibre && \
    usermod -aG sudo calibre && \
    echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers
USER calibre
