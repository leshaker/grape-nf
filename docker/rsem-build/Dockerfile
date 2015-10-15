########################################################
# Dockerfile to build RSEM v1.2.22 and 
# SAMtools 1.2-rglab-CRG container images 
#
# Based on ubuntu 14.04
########################################################

FROM ubuntu:14.04

# File Author / Maintainer
MAINTAINER Max Schelker <max.schelker@hu-berlin.de>

# Update the repository sources list and install dependencies
RUN apt-get update && apt-get install -y \
	gcc \
	g++ \
	make \
	git \
	perl \
	libz-dev \
	ncurses-dev \
	pigz \
	curl \
	r-base 

WORKDIR /usr/local/
ENV _SAMTOOLS_VERSION 1.2-rglab-CRG
RUN mkdir -p samtools 
RUN curl -L https://github.com/emi80/samtools/releases/download/$_SAMTOOLS_VERSION/samtools-$_SAMTOOLS_VERSION.tar.bz2 | tar xj --strip-components=1 -C samtools
WORKDIR /usr/local/samtools
RUN make
ENV PATH /usr/local/samtools:$PATH

WORKDIR /usr/local/
RUN git clone https://github.com/deweylab/RSEM.git
WORKDIR /usr/local/RSEM
RUN git checkout v1.2.22
# RUN git checkout v1.2.21
RUN make 
# RUN make ebseq
ENV PATH /usr/local/RSEM:$PATH
