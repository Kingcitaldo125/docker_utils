FROM debian:11 as compiler

ARG VERSION="go1.17.10"

RUN apt -y update && apt -y install build-essential git

WORKDIR /builddir/

ADD https://dl.google.com/go/go1.4-bootstrap-20171003.tar.gz .

RUN tar xzf go1.4-bootstrap-20171003.tar.gz && cd go/src/ && ./make.bash

RUN git clone https://go.googlesource.com/go goroot

ARG GOROOT_BOOTSTRAP="/builddir/go"

RUN cd goroot/ && git checkout $VERSION && cd src/ && ./make.bash
RUN cp goroot/bin/* /usr/bin/

FROM debian:11

COPY --from=compiler /usr/ /usr/

CMD [ "go" ]

