########################################################
# Dockerfile to build RSeQC 2.6.2 container images 
#
# Based on ubuntu 14.04
########################################################

FROM ubuntu:14.04

# File Author / Maintainer
MAINTAINER Max Schelker <max.schelker@hu-berlin.de>

# Update the repository sources list and install dependencies
RUN apt-get update && apt-get install -y \
	python-numpy \ 
	python-dev

ADD http://sourceforge.net/projects/rseqc/files/RSeQC-2.6.2.tar.gz/download /usr/local/RSeQC-2.6.2.tar.gz
WORKDIR /usr/local
RUN tar xzf RSeQC-2.6.2.tar.gz && rm RSeQC-2.6.2.tar.gz
WORKDIR /usr/local/RSeQC-2.6.2
RUN python setup.py install

ADD http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/gtfToGenePred /usr/local/bin
ADD http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/genePredToBed /usr/local/bin
WORKDIR /usr/local/bin
RUN chmod a+x *
ENV PATH /usr/local/bin:$PATH
