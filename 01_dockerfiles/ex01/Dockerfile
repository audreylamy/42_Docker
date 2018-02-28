FROM debian:latest
MAINTAINER alamy <alamy@student.42.fr>

ENV     TS_VERSION=3.0.13.8
ENV     TS_DIRECTORY=/opt/teamspeak

#install bzip2 qui permettra de decompresser teamspeak
RUN     apt-get -y update && \
        apt-get install -y bzip2 && \
        apt-get clean

#install teamspeak
ADD    http://dl.4players.de/ts/releases/${TS_VERSION}/teamspeak3-server_linux_amd64-${TS_VERSION}.tar.bz2 ./

RUN    tar jxf teamspeak3-server_linux_amd64-${TS_VERSION}.tar.bz2 && \
       mv teamspeak3-server_linux_amd64 ${TS_DIRECTORY} && \
       rm teamspeak3-server_linux_amd64-${TS_VERSION}.tar.bz2

RUN     groupadd -g 118 teamspeak && \
        useradd -u 118 -g 118 -d ${TS_DIRECTORY} teamspeak && \
        mkdir /data && \
        chown -R teamspeak:teamspeak ${TS_DIRECTORY} /data

EXPOSE 9987
EXPOSE 30033
EXPOSE 10011

WORKDIR ${TS_DIRECTORY}

CMD     teamspeak
