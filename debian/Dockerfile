FROM debian:stretch-20190506

USER 0

RUN whoami && \
    apt-get update && \
    apt-get install -y apt-transport-https bzip2 bash ca-certificates curl gnupg2 systemd software-properties-common

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - && \
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"

RUN mkdir -p /var/lib/docker && \
    apt-get update && apt-get install -y docker-ce docker-ce-cli containerd.io && \
    service docker start && \
    ls -al /run

RUN dockerd --host=unix:///var/run/docker.sock && \
    docker ps -a

RUN curl https://repo.anaconda.com/miniconda/Miniconda3-4.6.14-Linux-x86_64.sh -o /tmp/miniconda.sh && \
    bash /tmp/miniconda.sh -b -p /opt/miniconda && \
    export PATH=/opt/miniconda/bin:$PATH && \
    conda config --add channels conda-forge && \
    conda install pytest conda-build -y
