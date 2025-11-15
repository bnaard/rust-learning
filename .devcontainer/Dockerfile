FROM ubuntu:24.04

# non interactive frontend for locales
ENV DEBIAN_FRONTEND=noninteractive
ARG IMAGE_MAGICK_VERSION=7.1.1-41

# installing texlive and utils
RUN apt-get update && \
    apt-get -y install --no-install-recommends \
    pandoc \
    texlive-binaries \
    texlive-latex-recommended \
    texlive-latex-extra \
    texlive-extra-utils \
    texlive-fonts-recommended \
    texlive-fonts-extra \
    texlive-bibtex-extra \
    texlive-pictures \
    texlive-xetex \
    texlive-luatex \
    biber \
    latexmk \
    make \
    git \
    wget \
    procps \
    locales \
    curl \
    python3-pygments \
    sudo \
    inkscape \
    libpng-dev \
    libjpeg-dev \
    libtiff-dev \
    build-essential \ 
    checkinstall \
    libltdl-dev \
    && rm -rf /var/lib/apt/lists/*

# Download ImageMagick
RUN wget https://download.imagemagick.org/ImageMagick/download/ImageMagick.tar.gz \
    && tar -xvzf ImageMagick.tar.gz \
    && sudo rm -rf ImageMagick.tar.gz \
    && ls -d */ | grep '^ImageMagick*' \
    && cd $(ls -d */ | grep '^ImageMagick*') \
    && ./configure --with-modules  \
    && make \
    &&  make install \
    && ldconfig /usr/local/lib

RUN echo "shell_escape_commands = pagelayoutapi" >> /etc/texmf/texmf.d/00debian.cnf \
    && update-texmf

    # RUN wget -P /usr/local/bin https://github.com/friedemannbartels/latex-pagelayout/tree/main/scripts/pagelayoutapi \
#     && chmod +x /usr/local/bin/pagelayoutapi

# RUN sudo cpan -i App::cpanminus \
#     && sudo cpanm Log::Dispatch::File YAML::Tiny File::HomeDir Unicode::GCString Log::Log4perl

# generating locales
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen && \
    dpkg-reconfigure --frontend=noninteractive locales && \
    update-locale LANG=en_US.UTF-8
ENV LANGUAGE=en_US.UTF-8 LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8

# installing cpanm & missing latexindent dependencies
RUN curl -L http://cpanmin.us | perl - --self-upgrade && \
    cpanm Log::Dispatch::File YAML::Tiny File::HomeDir
