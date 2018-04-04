FROM debian:9
MAINTAINER Kridsada Thanabulpong <sirn@omise.co>

ENV LANG=C.UTF-8

RUN set -xe && \
    apt-get update && \
    apt-get install -y --no-install-recommends \
            apt-transport-https \
            build-essential \
            ca-certificates \
            curl \
            dirmngr \
            gnupg \
            && \
    apt-get clean

ENV S6_VERSION="1.21.4.0"

RUN set -xe && \
    S6_DOWNLOAD_URL="https://github.com/just-containers/s6-overlay/releases/download/v${S6_VERSION}/s6-overlay-amd64.tar.gz" && \
    S6_DOWNLOAD_SHA256="e903f138dea67e75afc0f61e79eba529212b311dc83accc1e18a449d58a2b10c" && \
    curl -fsL -o s6-overlay.tar.gz "${S6_DOWNLOAD_URL}" && \
    echo "${S6_DOWNLOAD_SHA256}  s6-overlay.tar.gz" |sha256sum -c - && \
    tar -xzC / -f s6-overlay.tar.gz && \
    rm s6-overlay.tar.gz

ENTRYPOINT ["/init"]