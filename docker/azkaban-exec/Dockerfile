ARG BASE_VERSION=latest

FROM openjdk:8-stretch

COPY ./azkaban-4.0.0/azkaban-exec-server/build/install/azkaban-exec-server/ azkaban

WORKDIR /azkaban
COPY ./docker/azkaban-exec/bootstrap.sh bin/
RUN chmod +x bin/bootstrap.sh

ENTRYPOINT [ "bin/bootstrap.sh" ]
