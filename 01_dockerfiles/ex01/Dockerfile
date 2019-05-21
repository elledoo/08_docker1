#docker build . -t debian/teamspeak 
#docker run --name teamspeak -p=9987:9987/udp -p=10011:10011 -p=30033:30033 debian/teamspeak

FROM debian:latest

ENV TSV=3.7.1

RUN apt-get -y update && apt-get -y upgrade &&\
	apt-get -y install bzip2 ca-certificates
	
ADD https://files.teamspeak-services.com/releases/server/3.7.1/teamspeak3-server_linux_amd64-3.7.1.tar.bz2 . 

RUN tar xvf teamspeak3-server_linux_amd64-3.7.1.tar.bz2 && \
	mkdir -p /home/teamspeak && \
	mv teamspeak3-server_linux_amd64/* /home/teamspeak/ && \
	rm -rf teamspeak3-server_linux_amd64-3.7.1.tar.bz2 && \
	cd /home/teamspeak/ && \
	touch .ts3server_license_accepted
EXPOSE	9987/udp 30033 10011

ENTRYPOINT ["/home/teamspeak/ts3server_minimal_runscript.sh"]
