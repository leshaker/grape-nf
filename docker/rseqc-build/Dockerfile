########################################################
# Dockerfile to build RSeQC 2.6.2 container images 
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
RUN apt-get install python -y
RUN apt-get install python-dev -y
RUN apt-get install python-pip -y
RUN apt-get install python-numpy -y
RUN apt-get install wget -y
RUN apt-get install pigz -y

WORKDIR /usr/local/
RUN wget http://sourceforge.net/projects/rseqc/files/RSeQC-2.6.2.tar.gz
RUN tar xzf RSeQC-2.6.2.tar.gz
RUN rm RSeQC-2.6.2.tar.gz
WORKDIR /usr/local/RSeQC-2.6.2
RUN python setup.py install

WORKDIR /usr/local/bin
RUN wget http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/gtfToGenePred
RUN wget http://hgdownload.cse.ucsc.edu/admin/exe/linux.x86_64/genePredToBed
RUN chmod a+x *
ENV PATH /usr/local/bin:$PATH
