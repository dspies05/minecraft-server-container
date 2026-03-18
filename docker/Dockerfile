FROM debian:latest

ARG JAVA_JDK=openjdk-21-jdk

WORKDIR /minecraft

RUN apt update
RUN apt install -y $JAVA_JDK
RUN apt install -y wget
RUN rm -rf /var/lib/apt/lists/*

ENV JAVA_XMS=2G
ENV JAVA_XMX=6G
ENV SERVER_JAR=https://piston-data.mojang.com/v1/objects/64bb6d763bed0a9f1d632ec347938594144943ed/server.jar

EXPOSE 25565/tcp
EXPOSE 25565/udp

ENTRYPOINT sh -c '\
  if [ ! -f server.jar ]; then \
    wget -O server.jar "$SERVER_JAR"; \
  fi; \
  echo "eula=true" eula.txt; \
  java -Xms$JAVA_XMS -Xmx$JAVA_XMX -jar server.jar nogui \
  '
