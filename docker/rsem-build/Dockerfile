########################################################
# Dockerfile to build RSEM v1.2.22 and 
# SAMtools 1.2-rglab-CRG container images 
#
# Based on ubuntu 14.04
########################################################

FROM leshaker/base

# File Author / Maintainer
MAINTAINER Max Schelker <max.schelker@hu-berlin.de>

# Program versions
ENV _SAMTOOLS_VERSION 1.2-rglab-CRG
ENV _HTSLIB_VERSION 1.2.1
ENV _RSEM_VERSION 1.2.22

# Update the repository sources list and install dependencies
RUN apt-get update && apt-get install -y \
	r-base 

# Install SAMtools
WORKDIR /usr/local/
ADD https://github.com/emi80/samtools/archive/$_SAMTOOLS_VERSION.tar.gz /usr/local/
ADD https://github.com/samtools/htslib/archive/$_HTSLIB_VERSION.tar.gz /usr/local/
RUN tar xzf $_SAMTOOLS_VERSION.tar.gz && rm $_SAMTOOLS_VERSION.tar.gz && mv samtools-$_SAMTOOLS_VERSION samtools
RUN tar xzf $_HTSLIB_VERSION.tar.gz && rm $_HTSLIB_VERSION.tar.gz && mv htslib-$_HTSLIB_VERSION htslib
WORKDIR /usr/local/samtools/
RUN make
ENV PATH /usr/local/samtools:$PATH

# Install RSEM
WORKDIR /usr/local/
ADD https://github.com/deweylab/RSEM/archive/v$_RSEM_VERSION.tar.gz /usr/local/
RUN tar xzf v$_RSEM_VERSION.tar.gz && rm v$_RSEM_VERSION.tar.gz && mv RSEM-$_RSEM_VERSION RSEM
WORKDIR /usr/local/RSEM/
RUN make
RUN make ebseq
ENV PATH /usr/local/RSEM:$PATH

# Clean up
RUN apt-get remove -y make libz-dev libncurses-dev && \
    apt-get autoremove -y 
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
