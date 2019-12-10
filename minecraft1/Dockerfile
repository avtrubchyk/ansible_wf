# This Docker file buils a minecraft server WG FORGE

FROM centos:7

MAINTAINER Andrei Trubchyk “avtrubchyk@gmail.com”

RUN yum clean all && \
    yum -y install java-1.8.0-openjdk-headless \
    yum -y install wget \
    yum -y install git \
    yum -y install gcc

RUN mkdir -p minecraft/{server,tools}

RUN wget -O minecraft/server/minecraft_server.jar \
https://launcher.mojang.com/v1/objects/3dc3d84a581f14691199cf6831b71ed1296a9fdf/server.jar

RUN echo "eula=true" > eula.txt


RUN cd /minecraft/tools && \
    git clone https://github.com/Tiiffi/mcrcon.git && \
    cd mcrcon && \
    gcc -std=gnu11 -pedantic -Wall -Wextra -O2 -s -o mcrcon mcrcon.c


ENV ONLINE_MODE=false ENABLE_RCON=true RCON_PASS=88888888

CMD java -Xms512m -Xmx1024m -jar minecraft/server/minecraft_server.jar nogui

EXPOSE 25565 25575
