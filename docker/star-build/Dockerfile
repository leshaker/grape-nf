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
    build-essential \
    libmysqlclient18 \
    libpng-dev \
    libmysqlclient-dev \
    libssl-dev \
    vim-common

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
ADD http://hgdownload.soe.ucsc.edu/admin/exe/userApps.$_USERAPPS_VERSION.src.tgz /usr/local/
RUN tar xzf userApps.$_USERAPPS_VERSION.src.tgz && rm userApps.$_USERAPPS_VERSION.src.tgz
RUN cd userApps && make libs && \
    cd kent/src && make destBin && \
 	cd utils && make bedGraphToBigWig.userApps && \
ENV PATH /usr/local/userApps/bin:$PATH

# Clean up
RUN apt-get remove -y perl make build-essential libz-dev libncurses-dev libpng-dev libmysqlclient-dev libssl-dev vim-common && \
    apt-get autoremove -y 
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
