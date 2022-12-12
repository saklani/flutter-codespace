FROM ubuntu:latest

RUN apt update 
RUN apt install -y wget curl git xz-utils zip unzip --no-install-recommends 

RUN apt-get -y autoremove 
RUN apt-get -y clean
RUN rm -rf /var/lib/apt/lists/* 

RUN mkdir /home/vscodespace
WORKDIR /home/vscodespace

ENV FLUTTER_CHANNEL="stable"
ENV FLUTTER_VERSION="3.3.9"
ENV FLUTTER_HOME=/home/vscodespace/flutter
ENV PATH=${PATH}:${FLUTTER_HOME}/bin
ENV PUB_CACHE=/home/vscodespace/.pub_cache


RUN curl -k --output flutter.tar.xz https://storage.googleapis.com/flutter_infra_release/releases/${FLUTTER_CHANNEL}/linux/flutter_linux_${FLUTTER_VERSION}-${FLUTTER_CHANNEL}.tar.xz
RUN tar xf flutter.tar.xz -C /home/vscodespace
