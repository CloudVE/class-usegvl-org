FROM bioconductor/bioconductor_docker:RELEASE_3_11


# Do not exclude man pages & other documentation
RUN rm /etc/dpkg/dpkg.cfg.d/excludes
# Reinstall all currently installed packages in order to get the man pages back
RUN apt-get update && \
    dpkg -l | grep ^ii | cut -d' ' -f3 | xargs apt-get install -y --reinstall && \
    rm -r /var/lib/apt/lists/*


RUN apt-get update \
	&& apt-get install -y --no-install-recommends apt-utils \
	&& apt-get install -y --no-install-recommends \
	fortune \
	cowsay \
	lolcat \
	openssh-client \
	man \
	ncbi-blast+

ENV PATH=${PATH}:/usr/games

ADD --chown=rstudio batslocal.tgz /opt/configs/readonly/rstudio/

RUN mkdir -p /gvl/projects/current && \
    usermod -d /gvl/projects/current rstudio

