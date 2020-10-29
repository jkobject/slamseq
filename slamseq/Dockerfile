FROM nfcore/base:1.9
LABEL authors="Tobias Neumann" \
      description="Docker image containing all software requirements for the nf-core/slamseq pipeline"

# Install the conda environment
COPY environment.yml /
# Add conda installation dir to PATH (instead of doing 'conda activate')
ENV PATH /opt/conda/envs/nf-core-slamseq-1.0.0/bin:$PATH

RUN conda env create -f /environment.yml && conda clean -a &&\



# Dump the details of the installed packages to a file for posterity
      conda env export --name nf-core-slamseq-1.0.0 > nf-core-slamseq-1.0.0.yml &&\

      touch .Rprofile &&\
      touch .Renviron &&\

      apt-get update &&\
      apt-get install -y \
      bc \
      gcc \
      make \
      libncurses5-dev \
      zlib1g-dev \
      libbz2-dev \
      g++ \
      liblzma-dev &&\

      # installing samtools wget https://github.com/samtools/samtools/releases/download/1.11/samtools-1.11.tar.bz2 && bzip2 -d samtools-1.11.tar.bz2 && tar xf samtools-1.11.tar && rm samtools-1.11.tar && cd samtools-1.11 && ./configure --enable-plugins && make && make install && cd ..
      wget https://github.com/samtools/samtools/releases/download/1.11/samtools-1.11.tar.bz2 &&\
      bzip2 -d samtools-1.11.tar.bz2 &&\
      tar xf samtools-1.11.tar &&\
      rm samtools-1.11.tar &&\
      cd samtools-1.11 &&\
      ./configure --enable-plugins &&\
      make &&\
      make install &&\
      cd .. &&\
      # echo "export PATH=/samtools-1.11/bin:$PATH" >> ~/.bashrc &&\

# installing bedtools wget https://github.com/arq5x/bedtools2/releases/download/v2.29.2/bedtools-2.29.2.tar.gz && tar -xzf bedtools-2.29.2.tar.gz && rm bedtools-2.29.2.tar.gz && cd bedtools2 && make && make install && cd .. 
      wget https://github.com/arq5x/bedtools2/releases/download/v2.29.2/bedtools-2.29.2.tar.gz &&\
      tar -xzf bedtools-2.29.2.tar.gz &&\
      rm bedtools-2.29.2.tar.gz &&\
      cd bedtools2 &&\
      make &&\
      make install &&\
      cd ..