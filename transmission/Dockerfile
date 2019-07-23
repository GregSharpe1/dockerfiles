FROM lsiobase/alpine:3.8

ARG BUILD_DATE
ARG VERSION

# test
RUN \
 apk add --no-cache \
	curl \
	jq \
	openssl \
	p7zip \
	rsync \
	tar \
	transmission-cli \
	transmission-daemon \
	unrar \
	unzip

EXPOSE 9091 51413
VOLUME /config /downloads /watch
