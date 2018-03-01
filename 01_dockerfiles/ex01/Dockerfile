FROM    debian:latest

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

#add group and user
RUN     groupadd -g 118 teamspeak && \
        useradd -u 118 -g 118 -d ${TS_DIRECTORY} teamspeak && \
        mkdir /data && \
        chown -R teamspeak:teamspeak ${TS_DIRECTORY} /data

#port qui communique avec l'exterieur
EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011
EXPOSE 41144

WORKDIR ${TS_DIRECTORY}

ENTRYPOINT ["./ts3server_minimal_runscript.sh", "createinifile=1"]

#docker build -t alamy/debian:latest $PWD
#docker run --name teamspeak -e TS3SERVER_LICENSE=accept -p 9987:9987/udp -p 30033:30033 -p 10011:10011 -p 41144:41144 alamy/debian

