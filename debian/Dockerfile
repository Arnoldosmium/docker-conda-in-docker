FROM debian:stable-20190506-slim

RUN apt-get update && \
    apt-get install -y apt-transport-https bzip2 bash ca-certificates curl gnupg2 software-properties-common

RUN curl https://repo.anaconda.com/miniconda/Miniconda3-4.6.14-Linux-x86_64.sh -o /tmp/miniconda3.sh && \
    bash /tmp/miniconda.sh -b -p /opt/miniconda && \
    export PATH=/opt/miniconda/bin:$PATH && \
    conda config --add channels conda-forge && \
    conda install pytest conda-build -y

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - && \
    add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable" && \
    apt-get update && apt-get install -y docker-ce docker-ce-cli containerd.io && \
    service docker start && \
    docker ps -a