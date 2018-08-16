# Jenkins conda dockerfile

Download: `docker pull fssc/jenkins-conda:populated0`

IMPORTANT NOTE. This mounts the present working directory as the home, and is writeable within the container. 
You can lose data that is in this directory if you delete it in the container. This was done to match the way
Jenkins runs docker containers.

Run as jenkins runs: 
`docker run --rm -u ${UID}:${GID} -w /home/jenkins -v $(pwd):/home/jenkins fssc/jenkins-conda:populated0 cat`

Get the container id and `exec` all the things.

<!---
> `docker exec <CONTAINER-ID> git clone https://github.com/fermi-lat/ScienceTools-conda-recipe.git`

> `docker exec <CONTAINER-ID> conda build -c conda-forge -c fermi_dev_externals ScienceTools-conda-recipe`

> `docker exec <CONTAINER-ID> conda create -n fermi -c conda-forge -c fermi_dev_externals --use-local fermitools -y`

> `docker exec <CONTAINER-ID> git clone https://github.com/fermi-lat/test-scripts.git`

--->

> `docker exec <CONTAINER-ID> conda install -n fermi -c conda-forge -c fermi_dev_externals fermitools-test-scripts -y`

`docker exec <CONTAINER-ID> /bin/bash -c "source activate fermi && test-scripts/ST-pulsar-test"`

`docker exec <CONTAINER-ID> /bin/bash -c "source activate fermi && "test-scripts/ST-AGN-thread-test"`

`docker exec <CONTAINER-ID> /bin/bash -c "source activate fermi && "test-scripts/ST-unit-test --bit64"`

