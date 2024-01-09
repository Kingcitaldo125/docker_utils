FROM debian:11 as builder

ARG arch

WORKDIR /condainstall/

ADD https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-${arch}.sh .

RUN bash ./Miniconda3-latest-Linux-${arch}.sh -b

FROM debian:11

COPY --from=builder /root/ /root/

WORKDIR /

ENV PATH="$PATH:/root/miniconda3/bin"

CMD [ "conda" ]
