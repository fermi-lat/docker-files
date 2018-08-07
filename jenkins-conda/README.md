# Jenkins conda dockerfile

Download: `docker pull fssc/jenkins-conda:latest`

IMPORTANT NOTE. This mounts the present working directory as the home, and is writeable within the container. 
You can lose data that is in this directory if you delete it in the container. This was done to match the way
Jenkins runs docker containers.

Run as jenkins runs: `docker run --rm -it -u ${UID}:${GID} -w /home/jenkins -v `pwd`:/home/jenkins fssc/jenkins-conda:`

`git clone https://github.com/fermi-lat/ScienceTools-conda-recipe.git`

`conda build -c conda-forge -c fermi_dev_externals ScienceTools-conda-recipe`
