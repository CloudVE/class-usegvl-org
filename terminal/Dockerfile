FROM cloudve/ttyd:latest


# Do not exclude man pages & other documentation
RUN rm /etc/dpkg/dpkg.cfg.d/excludes && \
# Reinstall all currently installed packages in order to get the man pages back
    apt-get update && \
    dpkg -l | grep ^ii | cut -d' ' -f3 | xargs apt-get install -y --reinstall && \
    rm -r /var/lib/apt/lists/* && \
    apt-get update \
	&& apt-get install -y --no-install-recommends apt-utils \
	&& apt-get install -y --no-install-recommends \
    sudo \
	fortune \
	cowsay \
	lolcat \
	openssh-client \
	man \
	ncbi-blast+ \
	git \
	wget \
	samtools \
	bowtie2 

RUN mkdir -p /gvl/projects && \
    cp -r /etc/skel/ /etc/profile/ && \
    adduser --disabled-password --home /gvl/projects/current --shell /bin/bash --gecos '' ubuntu && \
    echo 'ubuntu ALL=(ALL) NOPASSWD: ALL\n' > /etc/sudoers

ENV PATH=${PATH}:/usr/games

USER ubuntu

