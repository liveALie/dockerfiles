FROM ubuntu:18.04
LABEL maintainer="tstav@163.com" version="1.0" description="ubuntu environment"

#aliyun
COPY sources.list /etc/apt/sources.list
ENV DEBIAN_FRONTEND noninteractive
#install vim
RUN apt-get update && apt-get install -y vim wget firefox --fix-missing
ADD jdk-8u231-linux-x64.tar.gz /usr/local
ENV JAVA_HOME /usr/local/jdk1.8.0_231
ENV JRE_HOME ${JAVA_HOME}/jre
ENV CLASSPATH ${JAVA_HOME}/lib:${JRE_HOME}/lib
ENV PATH ${JAVA_HOME}/bin:$PATH
ADD ideaIC-2019.3.tar.gz /usr/local