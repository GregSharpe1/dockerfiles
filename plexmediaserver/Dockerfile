FROM ubuntu:18.04
LABEL maintainer "Greg Sharpe <me@gregsharpe.co.uk"

RUN \
    echo "----- Install runtime packages -----" && \
    apt-get update && \
    apt-get install -y \
        gnupg2 \
        wget && \
    echo "----- Install PlexMediaServer -----" && \
    wget -q https://downloads.plex.tv/plex-keys/PlexSign.key -O - | apt-key add - && \
    sh -c 'echo "deb https://downloads.plex.tv/repo/deb/ public main" >> /etc/apt/sources.list.d/plex.list' \
    apt-get update && \
    apt-get install plexmediaserver

EXPOSE 32400
