########################################################
# Dockerfile to build STAR 2.4.2a and SAMtools 0.1.19
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
RUN apt-get install git -y
RUN apt-get install wget -y
RUN apt-get install pigz -y
RUN apt-get install samtools -y

WORKDIR /usr/local/
RUN git clone https://github.com/alexdobin/STAR.git
WORKDIR /usr/local/STAR
RUN git checkout STAR_2.4.2a
# RUN git checkout STAR_2.4.0k
# RUN git checkout STAR_2.4.0j
ENV PATH /usr/local/STAR/bin/Linux_x86_64:$PATH

WORKDIR /usr/local/bin
RUN wget http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/bedGraphToBigWig
RUN chmod a+x *
ENV PATH /usr/local/bin:$PATH
