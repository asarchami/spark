#specifying our base docker-image 
FROM java:8-alpine
MAINTAINER Ali Sarchami

ADD http://apache.claz.org/spark/spark-2.2.1/spark-2.2.1-bin-hadoop2.7.tgz /opt/spark-2.2.1-bin-hadoop2.7.tgz
RUN apk update && \
    apk add coreutils bash supervisor && \
    tar -xzf /opt/spark-2.2.1-bin-hadoop2.7.tgz -C /opt/ && \
    ln -s /opt/spark-2.2.1-bin-hadoop2.7 /opt/spark

COPY master.conf /opt/conf/master.conf
COPY slave.conf /opt/conf/slave.conf

EXPOSE 8080 4040

CMD ["/opt/spark/bin/spark-shell", "--master", "local[*]"] 
