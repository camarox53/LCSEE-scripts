#
# docker build -t loud/eclipse .
#
# docker run -e DISPLAY -v /home/loud:/home/loud --net=host loud/eclipse
#
#
FROM ubuntu:15.04
MAINTAINER David Krovich <david.krovich@mail.wvu.edu>
RUN apt-get update && apt-get install -y \
  openjdk-8-jdk \
  openjdk-8-demo \
  openjdk-8-jre \
  openjdk-8-source \
  libopenjfx-java \
  libopenjfx-java-doc \
  libopenjfx-jni \
  openjfx \
  openjfx-source \
  wget


RUN apt-get install -y libgtk2.0-0 libcanberra-gtk-module

RUN apt-get install -y wget

RUN wget http://mirror.cc.vt.edu/pub/eclipse/technology/epp/downloads/release/luna/SR2/eclipse-java-luna-SR2-linux-gtk-x86_64.tar.gz -O /tmp/eclipse.tar.gz 

RUN echo 'Installing eclipse' && \
    tar -xf /tmp/eclipse.tar.gz -C /opt && \
    rm /tmp/eclipse.tar.gz

RUN mkdir -p /home/loud && \
    echo "loud:x:1000:1000:loud,,,:/home/loud:/bin/bash" >> /etc/passwd && \
    echo "loud:x:1000:" >> /etc/group && \
    chown loud:loud -R /home/loud


USER loud
ENV HOME /home/loud
WORKDIR /home/loud
CMD /opt/eclipse/eclipse
