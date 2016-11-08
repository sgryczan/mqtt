#
# HiveMQ DockerFile
#

# Pull base image. The unofficial docker openjdk-8 image will be used.
FROM java:8-jdk

#Install wget and unzip, download and install HiveMQ
RUN \
    apt-get install -y wget unzip &&\
    wget --content-disposition http://www.hivemq.com/download.php?token=7f1fdf38db26619b2bc83b2ae04fe4aa &&\
    unzip hivemq-*.zip -d /opt/ &&\
    mv /opt/hivemq-* /opt/hivemq

# Define working directory
WORKDIR /opt/hivemq

#Define HIVEMQ_HOME variable
ENV HIVEMQ_HOME /opt/hivemq

# Install config file
COPY config.xml /opt/hivemq/conf/config.xml

#Expose 1883
EXPOSE 1883
#Expose WebSocket forwarder
EXPOSE 8000

#Define default command. This is HiveMQ's run script.
CMD ["/opt/hivemq/bin/run.sh"]
