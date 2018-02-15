FROM centos:7

MAINTAINER "Fermi LAT Collaboration"

RUN yum update -y && \
    yum install -y \
                   bzip2 \
                   make \
                   patch \
                   sudo \
                   tar \
                   which \
                   libXext-devel \
                   libXrender-devel \
                   libSM-devel \
                   libX11-devel \
                   mesa-libGL-devel && \
yum clean all


RUN curl -s -L https://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh > miniconda.sh && \
  bash miniconda.sh -b -p ${HOME}/miniconda && \
  rm miniconda.sh && \
  export PATH=${HOME}/miniconda/bin:$PATH && \
  conda install --yes -c conda-forge -c fermi_dev_externals ape

RUN echo "export PATH=${HOME}/miniconda/bin:$PATH" >> ${HOME}/.bashrc

# RUN ${HOME}/miniconda/bin/conda install --yes -c conda-forge -c fermi_dev_externals WHATEVER_WE_NAME_SCIENCETOOLS!!!!!
# RUN ${HOME}/miniconda/bin/conda install --yes -c conda-forge -c fermi_dev_externals ape


CMD [ "/bin/bash" ]
