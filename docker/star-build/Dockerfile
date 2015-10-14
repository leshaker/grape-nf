########################################################
# Dockerfile to build samtools 0.1.19 and STAR 2.4.2a 
# container images 
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
# RUN apt-get install make -y
RUN apt-get install git -y
# RUN apt-get install perl -y
# RUN apt-get install libz-dev
# RUN apt-get install ncurses-dev -y
# RUN apt-get install python -y
# RUN apt-get install python-dev -y
# RUN apt-get install python-pip -y
RUN apt-get install wget -y
RUN apt-get install pigz -y
# RUN apt-get install curl -y
RUN apt-get install samtools -y
# RUN apt-get install R -y

# WORKDIR /usr/local/
# RUN git clone --recursive https://github.com/samtools/samtools.git
# WORKDIR /usr/local/samtools
# RUN git checkout 1.2

# WORKDIR /usr/local/
# RUN git clone --recursive https://github.com/samtools/htslib.git
# WORKDIR /usr/local/htslib
# RUN git checkout 1.2.1
# WORKDIR /usr/local/samtools
# RUN make
# ENV PATH /usr/local/samtools:$PATH

# WORKDIR /usr/local/
# ENV _SAMTOOLS_VERSION 1.2-rglab-CRG
# RUN mkdir -p samtools 
# RUN curl -L https://github.com/emi80/samtools/releases/download/$_SAMTOOLS_VERSION/samtools-$_SAMTOOLS_VERSION.tar.bz2 | tar xj --strip-components=1 -C samtools 
# ENV PATH /usr/local/samtools:$PATH

# WORKDIR /usr/local/
# RUN git clone https://github.com/deweylab/RSEM.git
# WORKDIR /usr/local/RSEM
# RUN git checkout v1.2.22
# # RUN git checkout v1.2.21
# RUN make 
# # RUN make ebseq
# ENV PATH /usr/local/RSEM:$PATH 

WORKDIR /usr/local/
RUN git clone https://github.com/alexdobin/STAR.git
WORKDIR /usr/local/STAR
RUN git checkout STAR_2.4.2a
# RUN git checkout STAR_2.4.0k
# RUN git checkout STAR_2.4.0j
ENV PATH /usr/local/STAR/bin/Linux_x86_64:$PATH

# WORKDIR /usr/local/
# RUN wget http://sourceforge.net/projects/rseqc/files/RSeQC-2.6.2.tar.gz
# RUN tar xzf RSeQC-2.6.2.tar.gz
# RUN rm RSeQC-2.6.2.tar.gz
# WORKDIR /usr/local/RSeQC-2.6.2
# RUN pip install distribute
# # RUN pip install Cython
# RUN pip install numpy
# RUN python setup.py install

WORKDIR /usr/local/bin
# RUN wget http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/gtfToGenePred
# RUN wget http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/genePredToBed
RUN wget http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/bedGraphToBigWig
RUN chmod a+x *
ENV PATH /usr/local/bin:$PATH
