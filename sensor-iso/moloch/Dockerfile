FROM debian:buster-slim

# Copyright (c) 2021 Battelle Energy Alliance, LLC.  All rights reserved.

LABEL maintainer="malcolm.netsec@gmail.com"

ENV DEBIAN_FRONTEND noninteractive

ENV ARKIME_VERSION "2.7.1"
ENV ARKIMEDIR "/opt/moloch"

RUN sed -i "s/buster main/buster main contrib non-free/g" /etc/apt/sources.list && \
  apt-get -q update && \
  apt-get install -q -y --no-install-recommends \
    build-essential \
    curl \
    git-core \
    iproute2 \
    meson \
    ninja-build \
    patch \
    python3-dev \
    python3-pip \
    python3-setuptools \
    python3-wheel \
    ruby \
    ruby-dev \
    rubygems \
    sudo \
    wget && \
  gem install --no-ri --no-rdoc fpm && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ADD build-moloch-deb.sh /usr/local/bin/
ADD patch /moloch-src-patch
ADD etc /moloch-etc

ENTRYPOINT ["/bin/bash", "/usr/local/bin/build-moloch-deb.sh"]
