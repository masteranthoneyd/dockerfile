FROM yangbingdong/graalvm23:ubuntu24

WORKDIR /tmp/build
ENV MUSL_HOME=/root/musl-toolchain

SHELL ["bash", "--login", "-c"]
RUN curl -O https://musl.libc.org/releases/musl-1.2.4.tar.gz && \
    curl -O https://zlib.net/fossils/zlib-1.2.13.tar.gz && \
    tar -xzvf musl-1.2.4.tar.gz && \
    pushd musl-1.2.4 && \
    ./configure --prefix=$MUSL_HOME --static && \
    make && \
    make install && \
    popd && \
    ln -s $MUSL_HOME/bin/musl-gcc $MUSL_HOME/bin/x86_64-linux-musl-gcc

ENV PATH=$MUSL_HOME/bin:$PATH

RUN tar -xzvf zlib-1.2.13.tar.gz && \
    pushd zlib-1.2.13 && \
    CC=musl-gcc ./configure --prefix=$MUSL_HOME --static && \
    make && \
    make install && \
    popd

ARG UPX_VERSION=4.2.2
ARG UPX_ARCHIVE=upx-${UPX_VERSION}-amd64_linux.tar.xz
RUN apt install wget -y && \
    wget -q https://github.com/upx/upx/releases/download/v${UPX_VERSION}/${UPX_ARCHIVE} && \
    tar -xJf ${UPX_ARCHIVE} && \
    mv upx-${UPX_VERSION}-amd64_linux/upx /usr/bin && \
    cd / && \
    rm -rf /tmp/build && \
    sdk flush

WORKDIR /root

ENTRYPOINT ["/bin/bash","--login", "-c"]