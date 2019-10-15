FROM alpine
MAINTAINER Hube h66R10@gmail.com

ENV BUILD_PACKAGES bash curl-dev ruby-dev build-base linux-headers openssl
ENV RUBY_PACKAGES ruby ruby-io-console ruby-bundler ruby-rdoc ruby-rake nodejs npm

# Update and install all of the required packages.
# At the end, remove the apk cache
RUN apk update && \
    apk upgrade -q && \
    apk add ca-certificates wget --no-cache && \
    apk add $BUILD_PACKAGES --no-cache -q && \
    apk add $RUBY_PACKAGES --no-cache -q && \
    rm -rf /var/cache/apk/*

RUN wget https://www.phusionpassenger.com/latest_stable_tarball && \
    mkdir /passenger && \
    tar -xzf latest_stable_tarball -C /passenger && \
    rm -rf latest_stable_tarball


RUN /passenger/$(ls /passenger)/bin/passenger-install-nginx-module --languages nodejs --auto
