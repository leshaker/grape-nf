########################################################
# Dockerfile to build base container images 
#
# Based on ubuntu 14.04
########################################################

FROM ubuntu:14.04

# File Author / Maintainer
MAINTAINER Max Schelker <max.schelker@hu-berlin.de>

# Update the repository sources list and install dependencies
RUN apt-get update && apt-get install -y \
	gcc \
	make \
    libncurses-dev \
    pigz \
	libz-dev

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
