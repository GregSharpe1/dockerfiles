FROM alpine:3.10
LABEL maintainer "Greg Sharpe me@gregsharpe.co.uk"

ENV JX_VERSION "2.0.666"

RUN apk -v --update add \
    curl \
    tar \
    bash

RUN curl -L "https://github.com/jenkins-x/jx/releases/download/v2.0.666/jx-linux-amd64.tar.gz" | tar -zx

#ENTRYPOINT ["jx"]
#CMD ["--help"]
