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

# Install devtoolset 2.
RUN yum update -y && \
    yum install -y \
        centos-release-scl \
        yum-utils && \
    yum-config-manager --add-repo http://people.centos.org/tru/devtools-2/devtools-2.repo && \
    yum update -y && \
    yum install -y \
        devtoolset-2-binutils \
        devtoolset-2-gcc \
        devtoolset-2-gcc-gfortran \
        devtoolset-2-gcc-c++ && \
yum clean all

RUN curl -s -L \
    https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh > \
    miniconda.sh && \
  bash miniconda.sh -b -p /miniconda && \
  rm miniconda.sh && \
  /miniconda/bin/conda install -c conda-forge \
    conda-build \
    anaconda-client \
    git \
    jinja2 \
    setuptools \
    toolchain \
    toolchain_c_linux-64 \
    toolchain_cxx_linux-64 \
    toolchain_fort_linux-64 -y && \
  /miniconda/bin/conda clean -tipsy && \
  mkdir -p /.conda/pkgs && \
  touch /.conda/pkgs/urls.txt && \
  chmod -R a+rwx /miniconda /.conda && \
  chown -R nobody:nobody /miniconda /.conda

COPY .gitconfig /.gitconfig
COPY entrypoint /opt/fermi/bin/entrypoint

ENTRYPOINT ["/opt/fermi/bin/entrypoint"]

CMD [ "/bin/bash" ]
