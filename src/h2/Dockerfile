FROM openjdk:8-alpine

ENV H2_VERSION 1.4.192

COPY create-tables.sql /root/create-tables.sql

RUN \
  mkdir /opt 

COPY h2-$H2_VERSION.jar /opt/h2.jar

EXPOSE 8082 9092

ENTRYPOINT \
  java -cp /opt/h2.jar org.h2.tools.RunScript -url jdbc:h2:~/tiefvision -user sa -script /root/create-tables.sql && \
  java -cp /opt/h2.jar org.h2.tools.Server -tcp -tcpAllowOthers -web -webAllowOthers
