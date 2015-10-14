########################################################
# Dockerfile to build RSEM v1.2.22 and 
# SAMtools 1.2-rglab-CRG container images 
#
# Based on ubuntu 14.04
########################################################

FROM ubuntu:14.04

# File Author / Maintainer
MAINTAINER Max Schelker <max.schelker@hu-berlin.de>

# Update the repository sources list
RUN apt-get update -y

# install dependencies
RUN apt-get install gcc -y
RUN apt-get install g++ -y
RUN apt-get install make -y
RUN apt-get install git -y
RUN apt-get install perl -y
RUN apt-get install libz-dev
RUN apt-get install ncurses-dev -y
RUN apt-get install pigz -y
RUN apt-get install curl -y
RUN apt-get install r-base -y

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
