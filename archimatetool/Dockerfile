FROM ubuntu:14.04

MAINTAINER michimau <mauro.michielon@eea.europa.eu>

RUN apt-get update && apt-get install -y firefox \
                      openjdk-7-jre \
                      curl

ENV ARCHI_VERSION=3.3.2

RUN curl -o /archi.tar.gz http://www.archimatetool.com/downloads/latest/Archi-lnx32_64-$ARCHI_VERSION.tar.gz
RUN tar -zxvf /archi.tar.gz

# Replace 1000 with your user / group id
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer

USER developer
ENV HOME /home/developer

CMD /Archi/Archi64
