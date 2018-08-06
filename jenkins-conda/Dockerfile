FROM centos:6

MAINTAINER "Fermi LAT Collaboration"

RUN yum update -y && \
    yum install -y \
        bzip2 \
        git \
        make \
        mesa-libGL-devel \
        libXext-devel \
        libXrender-devel \
        libSM-devel \
        libX11-devel \
        patch \
        sudo \
        tar \
        which && \
yum clean all


RUN curl -s -L https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh > miniconda.sh && \
  bash miniconda.sh -b -p /miniconda && \
  rm miniconda.sh

RUN mkdir -p /.conda/pkgs && \
  touch /.conda/pkgs/urls.txt

RUN chmod -R a+rwx /miniconda /.conda && \
  chown -R nobody:nobody /miniconda /.conda

ENV PATH "/miniconda/bin:$PATH"

CMD [ "/bin/bash" ]
