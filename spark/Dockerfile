#specifying our base docker-image 
FROM openjdk:8-alpine
MAINTAINER Ali Sarchami

ARG SPARK_VERSION=2.2.1
ARG SCALA_VERSION=2.12.2
ARG SBT_VERSION=1.0.4

RUN apk update && \
    apk add coreutils bash supervisor curl git python python-dev gfortran py-pip build-base vim && \
    mkdir /opt && \
    wget -qO - http://downloads.lightbend.com/scala/${SCALA_VERSION}/scala-${SCALA_VERSION}.tgz | tar -xz -C /opt/ && \
    wget -qO - https://github.com/sbt/sbt/releases/download/v${SBT_VERSION}/sbt-${SBT_VERSION}.tgz | tar -xz -C /opt/ && \
    wget -qO - http://apache.claz.org/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop2.7.tgz | tar -xz -C /opt/ && \
    ln -s /opt/scala-${SCALA_VERSION} /opt/scala && \
    ln -s /opt/spark-${SPARK_VERSION}-bin-hadoop2.7 /opt/spark && \
    wget -O /root/.vimrc https://raw.githubusercontent.com/asarchami/vimrc/master/vimrc.vim

COPY conf/ /opt/conf

EXPOSE 8080 4040

CMD ["/opt/spark/bin/spark-shell", "--master", "local[*]"] 
