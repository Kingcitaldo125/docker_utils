FROM debian:11

RUN apt -y update && apt -y install build-essential

WORKDIR /boosttemp/

ARG BOOST_VER="1_87_0"
ARG BOOST_VER_DOT="1.87.0"

ADD https://archives.boost.io/release/${BOOST_VER_DOT}/source/boost_${BOOST_VER}.tar.gz .

RUN tar xzf boost_${BOOST_VER}.tar.gz && \
    cd boost_${BOOST_VER} && \
    ./bootstrap.sh && \
    ./b2 -j $(nproc) install

CMD [ "/bin/bash" ]
