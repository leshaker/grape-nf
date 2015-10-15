########################################################
# Dockerfile to build RSeQC 2.6.2 container images 
#
# Based on ubuntu 14.04
########################################################

FROM leshaker/base

# File Author / Maintainer
MAINTAINER Max Schelker <max.schelker@hu-berlin.de>

# Program versions
ENV _RSEQC_VERSION RSeQC-2.6.2
ENV _USERAPPS_VERSION v323

# Update the repository sources list and install dependencies
RUN apt-get update && apt-get install -y \
	python-numpy \ 
	python-dev \
	libkrb5-dev

# Install UCSC tools
WORKDIR /usr/local/
ADD http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/genePredToBed /usr/local/bin/
ADD http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/gtfToGenePred /usr/local/bin/
RUN chmod a+x bin/*
ENV PATH /usr/local/bin:$PATH

# Install RSeQC
ADD http://sourceforge.net/projects/rseqc/files/$_RSEQC_VERSION.tar.gz/download /usr/local/$_RSEQC_VERSION.tar.gz
WORKDIR /usr/local/
RUN tar xzf $_RSEQC_VERSION.tar.gz && rm $_RSEQC_VERSION.tar.gz
WORKDIR /usr/local/$_RSEQC_VERSION
RUN python setup.py install

# Clean up
RUN apt-get remove -y perl gcc make python-dev && \
    apt-get autoremove -y 
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
