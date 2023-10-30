FROM debian:11 as builder

RUN apt -y update && apt -y install \
    build-essential \
    vim \
    wget \
    gdb \
    lcov \
    pkg-config \
    libbz2-dev \
    libffi-dev \
    libgdbm-dev \
    libgdbm-compat-dev \
    liblzma-dev \
    libncurses5-dev \
    libreadline6-dev \
    libsqlite3-dev \
    libssl-dev \
    lzma \
    lzma-dev \
    tk-dev \
    uuid-dev \
    zlib1g-dev

ARG VERSION="3.11.6"
ARG N_BUILD_THREADS="4"

WORKDIR /working/

ADD https://github.com/python/cpython/archive/refs/tags/v${VERSION}.tar.gz .

RUN tar xzf v${VERSION}.tar.gz && \
    cd cpython-${VERSION} && \
    ./configure && \
    make -j ${N_BUILD_THREADS} && \
    make install

FROM debian:11

WORKDIR /

COPY --from=builder /usr/local/lib /usr/local/lib
COPY --from=builder /usr/local/bin /usr/local/bin

RUN cd /usr/local/bin && ln -s python3 python

CMD [ "/bin/bash" ]
