FROM alpine:3.10
LABEL maintainer "Greg Sharpe me@gregsharpe.co.uk"

ENV CLOUDFOUNDRY_CLI_VERSION ""

RUN apk -v --update add \
    curl \
    tar

RUN curl -L "https://cli.run.pivotal.io/stable?release=linux64-binary&source=github" | tar -zx

ENTRYPOINT ["cf"]
CMD ["--help"]
