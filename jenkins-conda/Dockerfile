FROM centos:6

LABEL maintainer.name="Fermi LAT Collaboration" \
      maintainer.email="fermihelp@milkyway.gsfc.nasa.gov"

RUN yum update -y && \
    yum install -y \
        bzip2 \
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


RUN curl -s -L \
    https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh > \
    miniconda.sh && \
  bash miniconda.sh -b -p /miniconda && \
  rm miniconda.sh && \
  /miniconda/bin/conda install -c conda-forge \
    conda-build git toolchain toolchain_c_linux-64 toolchain_cxx_linux-64 \
    toolchain_fort_linux-64 -y && \
  mkdir -p /.conda/pkgs && \
  touch /.conda/pkgs/urls.txt && \
  chmod -R a+rwx /miniconda /.conda && \
  chown -R nobody:nobody /miniconda /.conda

COPY .gitconfig /.gitconfig

ENV PATH "/miniconda/bin:$PATH"

CMD [ "/bin/bash" ]
