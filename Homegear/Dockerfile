# Taken from https://github.com/Homegear/Homegear-Docker/blob/master/stable/Dockerfile
FROM debian:stretch

RUN apt-get update && apt-get -y install apt-transport-https wget ca-certificates apt-utils gnupg \
libzip4 libavahi-client3 libavahi-client-dev insserv
RUN \
	wget https://homegear.eu/packages/Release.key && apt-key add Release.key && rm Release.key; \
	echo 'deb https://homegear.eu/packages/Debian/ stretch/' >> /etc/apt/sources.list.d/homegear.list; \
	apt-get update && apt-get -y install libhomegear-node homegear homegear-nodes-core homegear-nodes-extra homegear-homematicbidcos homegear-homematicwired homegear-insteon homegear-max homegear-philipshue homegear-sonos homegear-kodi homegear-ipcam homegear-beckhoff homegear-knx homegear-enocean homegear-intertechno homegear-rsl homegear-rs2w homegear-mbus homegear-zwave homegear-ccu2 homegear-easyled homegear-easyled2 homegear-easycam homegear-influxdb; \
    rm -f /etc/homegear/dh1024.pem; \
    rm -f /etc/homegear/homegear.crt; \
    rm -f /etc/homegear/homegear.key; \
    cp -R /etc/homegear /etc/homegear.config; \
    cp -R /var/lib/homegear /var/lib/homegear.data; \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


COPY start.sh /start.sh
RUN chmod +x /start.sh
CMD /start.sh

EXPOSE 2001 2002 2003