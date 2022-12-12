FROM ubuntu:latest

ENV LC_ALL=en_US.UTF-8
ENV LANG=en_US.UTF-8

# Installing packages needed to run and install flutter
RUN apt update 
RUN apt install -y wget curl git xz-utils zip unzip ca-certificates --no-install-recommends 

# Cleaning up unnecessary dependencies
RUN	apt-get -y autoremove 
RUN apt-get -y clean
RUN rm -rf /var/lib/apt/lists/* 

# Setup directory where flutter will be installed
RUN mkdir /home/vscodespace
WORKDIR /home/vscodespace

# Setup flutter config needed
ENV FLUTTER_CHANNEL="stable"
ENV FLUTTER_VERSION="3.3.9"
ENV FLUTTER_HOME=/home/vscodespace/flutter
ENV PATH=${PATH}:${FLUTTER_HOME}/bin
ENV PUB_CACHE=/home/vscodespace/.pub_cache

# Fetch and install flutter
RUN curl -k --output flutter.tar.xz https://storage.googleapis.com/flutter_infra_release/releases/${FLUTTER_CHANNEL}/linux/flutter_linux_${FLUTTER_VERSION}-${FLUTTER_CHANNEL}.tar.xz
RUN tar xf flutter.tar.xz -C /home/vscodespace

# Fix dubious ownership error
RUN git config --global --add safe.directory ${FLUTTER_HOME}
