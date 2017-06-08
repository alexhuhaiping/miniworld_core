FROM ubuntu:16.04
MAINTAINER Nils Schmidt <miniworldproject@gmail.com>

RUN apt-get update && \
# python3
apt-get -y install python3 python3-pip && \
# apt dependencies
apt-get -y --no-install-recommends install git ebtables iproute2 qemu-kvm bridge-utils bison flex libdb-dev psmisc curl wget


# miniworld
ARG BRANCH=nightly
RUN mkdir /app
RUN git clone -b $BRANCH https://github.com/miniworld-project/miniworld_core.git app
WORKDIR /app
RUN (echo $PWD)
RUN pip3 install -r requirements.txt
RUN (cd examples && ./get_images.sh)

# iproute2
# RUN apt-get -y install pkg-config

CMD ["bash", "/app/start_server.sh"]

EXPOSE 5000