FROM buildpack-deps:stretch

RUN apt-get update && \
    apt-get install -y apt-transport-https bzip2 bash ca-certificates curl gnupg2 systemd software-properties-common && \
    curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - && \
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"

RUN apt-get update && apt-get install -y docker-ce docker-ce-cli containerd.io && \
    docker -v && dockerd -v

RUN curl https://repo.anaconda.com/miniconda/Miniconda3-4.6.14-Linux-x86_64.sh -o /tmp/miniconda.sh && \
    bash /tmp/miniconda.sh -b -p /opt/miniconda && \
    rm /tmp/miniconda.sh && \
    export PATH=/opt/miniconda/bin:$PATH && \
    conda config --add channels conda-forge && \
    conda install pytest conda-build -y

RUN curl https://raw.githubusercontent.com/docker-library/docker/91bbc4f7b06c06020d811dafb2266bcd7cf6c06d/18.09/modprobe.sh -o /usr/local/bin/modprobe && \
    chmod u+x /usr/local/bin/modprobe && \
    curl https://raw.githubusercontent.com/docker-library/docker/91bbc4f7b06c06020d811dafb2266bcd7cf6c06d/18.09/docker-entrypoint.sh -o /usr/local/bin/docker-entrypoint.sh && \
    chomd u+x /usr/local/bin/docker-entrypoint.sh && \
    export PATH=/usr/local/bin:$PATH

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["sh"]