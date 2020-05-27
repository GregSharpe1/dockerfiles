FROM alpine

LABEL maintainer "Greg Sharpe <me@gregsharpe.co.uk>"

ENV CIVO_CLI_VERSION ""

# Install the base packages for Ruby
RUN apk update
RUN apk upgrade
RUN apk add curl bash wget

# Install ruby and ruby-bundler
RUN apk add ruby ruby-bundler

# Clear Container cache
RUN rm -rf /var/cache/apk/*

# Install civo-cli
#RUN gem install civo_cli
#
#ENTRYPOINT ["civo"]
#CMD ["--help"]
