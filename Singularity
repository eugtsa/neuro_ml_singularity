Bootstrap: docker
From: neurodebian:latest

%help

    Container with Anaconda 3 (Conda 2019.3) and full neuro ml environment from neurodebian.
    This installation is based on Python 3.7

%files
  ./requirements.txt /requirements.txt

%post
  
  apt-get update
  DEBIAN_FRONTEND=noninteractive apt-get -yq install \
    build-essential \
    wget \
    unzip \
    git

  rm -rf /var/lib/apt/lists/*
  apt-get clean
  
  wget -c https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh
    /bin/bash Anaconda3-2019.03-Linux-x86_64.sh -bfp /usr/local

  #Conda configuration of channels from .condarc file

  conda config --add channels defaults
  conda config --add channels conda-forge
  conda config --add channels pytorch
  conda update conda

  #Install environment
  conda install snakeviz
  conda install --file requirements.txt
