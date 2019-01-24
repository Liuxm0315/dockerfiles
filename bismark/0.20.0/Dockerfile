# Base Image
FROM debian:jessie

# Metadata
LABEL base.image="debian:jessie"
LABEL version="1"
LABEL software="bismark"
LABEL software.version="0.20.0"
LABEL description="Bismark is a program to map bisulfite treated sequencing reads to a genome of interest and perform methylation calls in a single step. The output can be easily imported into a genome viewer, such as SeqMonk, and enables a researcher to analyse the methylation levels of their samples straight away. It's main features are: a, Bisulfite mapping and methylation calling in one single step; b, Supports single-end and paired-end read alignments; c, Supports ungapped and gapped alignments; d, Alignment seed length, number of mismatches etc. are adjustable; e, Output discriminates between cytosine methylation in CpG, CHG and CHH * context"
LABEL website="https://www.bioinformatics.babraham.ac.uk/projects/bismark/"
LABEL documentation="https://github.com/FelixKrueger/Bismark/tree/master/Docs"
LABEL license="GNU GPL v3.0"
LABEL tags="epigenomics"

# Maintainer
LABEL maintainer="Xingmin Liu <xliu@diagnoa.com>"

RUN apt-get update && apt-get install -y build-essential wget samtools unzip 
#RUN apt-get update &&  apt-get install  -y build-essential zlib1g-dev libncurses5-dev libncursesw5-dev git wget unzip python-pip python-dev

# Install Bowtie2
RUN mkdir /src && \
	cd /src && \
	wget -O bowtie2.zip https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.3.2/bowtie2-2.3.2-linux-x86_64.zip/download && \
	unzip bowtie2.zip && \
	ln -s /src/bowtie2-2.3.2/bowtie2* /usr/local/bin

# Install Bismark
RUN cd /src && \
	wget https://github.com/FelixKrueger/Bismark/archive/0.18.2.tar.gz && \
	tar zxf 0.18.2.tar.gz && \
	ln -s /src/Bismark-0.18.2/bismark* /usr/local/bin/

WORKDIR /data/

CMD ["bismark"]

