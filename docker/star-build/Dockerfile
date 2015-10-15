########################################################
# Dockerfile to build STAR 2.4.2a and SAMtools 1.2
# container images 
#
# Based on ubuntu 14.04
########################################################

FROM leshaker/base

# File Author / Maintainer
MAINTAINER Max Schelker <max.schelker@hu-berlin.de>

# Program versions
ENV _SAMTOOLS_VERSION 1.2
ENV _HTSLIB_VERSION 1.2.1
ENV _STAR_VERSION STAR_2.4.2a
ENV _USERAPPS_VERSION v323

# Update the repository sources list and install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
	libkrb5-dev

# Install SAMtools
WORKDIR /usr/local/
ADD https://github.com/samtools/samtools/archive/$_SAMTOOLS_VERSION.tar.gz /usr/local/
ADD https://github.com/samtools/htslib/archive/$_HTSLIB_VERSION.tar.gz /usr/local/
RUN tar xzf $_SAMTOOLS_VERSION.tar.gz && rm $_SAMTOOLS_VERSION.tar.gz && mv samtools-$_SAMTOOLS_VERSION samtools
RUN tar xzf $_HTSLIB_VERSION.tar.gz && rm $_HTSLIB_VERSION.tar.gz && mv htslib-$_HTSLIB_VERSION htslib
WORKDIR /usr/local/samtools/
RUN make
ENV PATH /usr/local/samtools:$PATH

# Install STAR
WORKDIR /usr/local/
ADD https://github.com/alexdobin/STAR/archive/$_STAR_VERSION.tar.gz /usr/local/
RUN tar xzf $_STAR_VERSION.tar.gz && rm $_STAR_VERSION.tar.gz && mv STAR-$_STAR_VERSION STAR
ENV PATH /usr/local/STAR/bin/Linux_x86_64:$PATH

# Install UCSC tools
WORKDIR /usr/local/
ADD http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/bedGraphToBigWig /usr/local/bin/
RUN chmod a+x bin/*
ENV PATH /usr/local/bin:$PATH

# Clean up
RUN apt-get remove -y perl make libz-dev libncurses-dev && \
	apt-get autoremove -y 
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
