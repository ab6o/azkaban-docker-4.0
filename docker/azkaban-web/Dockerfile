ARG BASE_VERSION=latest

FROM openjdk:8-stretch

COPY ./azkaban-4.0.0/azkaban-web-server/build/install/azkaban-web-server/ azkaban

WORKDIR /azkaban
COPY ./docker/azkaban-web/bootstrap.sh bin/
RUN chmod +x bin/bootstrap.sh

ENTRYPOINT [ "bin/bootstrap.sh" ]
