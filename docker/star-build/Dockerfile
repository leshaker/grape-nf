########################################################
# Dockerfile to build STAR 2.4.2a and SAMtools 0.1.19
# container images 
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
	git \
	wget \
	pigz \
	samtools

WORKDIR /usr/local
RUN git clone https://github.com/alexdobin/STAR.git
WORKDIR /usr/local/STAR
RUN git checkout STAR_2.4.2a
# RUN git checkout STAR_2.4.0k
# RUN git checkout STAR_2.4.0j
ENV PATH /usr/local/STAR/bin/Linux_x86_64:$PATH

ADD http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/bedGraphToBigWig /usr/local/bin
WORKDIR /usr/local/bin
RUN chmod a+x *
ENV PATH /usr/local/bin:$PATH
