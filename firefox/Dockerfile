FROM alpine:3.10

LABEL maintainer "me@gregsharpe.co.uk"

RUN apk -v --update add \
    bash

RUN apk -v --update add \
    firefox-esr \
    ttf-dejavu \
    ttf-freefont

RUN rm /var/cache/apk/*
