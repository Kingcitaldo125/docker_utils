FROM debian:11

RUN apt -y update && apt -y install build-essential

WORKDIR /boosttemp/

ADD https://boostorg.jfrog.io/artifactory/main/release/1.77.0/source/boost_1_77_0.tar.gz .

RUN tar xzf boost_1_77_0.tar.gz && \
    cd boost_1_77_0 && \
    ./bootstrap.sh && \
    ./b2 -j $(nproc) && \
    ./b2 install

CMD [ "/bin/bash" ]
