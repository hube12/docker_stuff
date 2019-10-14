FROM alpine
MAINTAINER Hube

ENV BUILD_PACKAGES bash curl-dev ruby-dev build-base linux-headers openssl
ENV RUBY_PACKAGES ruby ruby-io-console ruby-bundler ruby-rdoc ruby-rake nodejs npm

# Update and install all of the required packages.
# At the end, remove the apk cache
RUN apk update && \
    apk upgrade -q && \
    apk add ca-certificates wget && \
    apk add $BUILD_PACKAGES -q && \
    apk add $RUBY_PACKAGES -q && \
    rm -rf /var/cache/apk/*

RUN wget https://www.phusionpassenger.com/latest_stable_tarball && \
    mkdir /passenger && \
    tar -xzf latest_stable_tarball -C /passenger



RUN /passenger/$(ls /passenger)/bin/passenger-install-nginx-module --languages nodejs --auto