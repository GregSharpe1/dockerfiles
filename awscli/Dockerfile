FROM alpine:3.6

LABEL maintainer="me@gregsharpe.co.uk"

ENV AWS_CLI_VERSION "1.16.189"

RUN apk -v --update add \
        git \
        python \
        py-pip \
        bash \
        jq \
        && pip install --upgrade awscli==${AWS_CLI_VERSION} \
        && apk -v --purge del py-pip \
        && mkdir /project \
        && rm /var/cache/apk/*

ENTRYPOINT ["aws"]

CMD [ "help" ]
