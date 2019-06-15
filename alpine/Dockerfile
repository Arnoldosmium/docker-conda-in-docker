FROM docker:18.09

USER 0

RUN apk add -y bzip2 bash curl systemd service && \
    curl https://repo.anaconda.com/miniconda/Miniconda3-4.6.14-Linux-x86_64.sh -o /tmp/miniconda.sh && \
    bash /tmp/miniconda.sh -b -p /opt/miniconda && \
    rm /tmp/miniconda.sh && \
    export PATH=/opt/miniconda/bin:$PATH && \
    conda config --add channels conda-forge && \
    conda install pytest conda-build -y

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["sh"]