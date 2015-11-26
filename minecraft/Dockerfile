# Setup a minecrafter server
#
# TODO: 
#   Pull / generate server.propertires from a secure location so passwords can be included
#       - including port number?
#
FROM ubuntu

MAINTAINER henry.escobar@gmail.com version 1.0

RUN apt-get update 
RUN apt-get install -y wget default-jdk  
RUN apt-get clean && rm -rf /var/lib/apt/lists/* 

RUN useradd -c 'minecraft user' -m -d /home/minecraft -s /bin/bash minecraft
RUN cd /home/minecraft && \
    wget -O minecraft_server.jar \
    https://s3.amazonaws.com/Minecraft.Download/versions/1.8.8/minecraft_server.1.8.8.jar 

COPY ./eula.txt /home/minecraft/eula.txt
COPY ./minecraft-server-properties /home/minecraft/server.properties
RUN chown minecraft /home/minecraft/server.properties
 
USER minecraft
    
EXPOSE 65415

WORKDIR /home/minecraft
CMD ["java", "-Xmx2048M","-Xms2048M","-jar","/home/minecraft/minecraft_server.jar","nogui"]
