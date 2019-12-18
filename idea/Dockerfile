FROM ubuntu:18.04
LABEL maintainer="tstav@163.com" version="1.0" description="ubuntu environment"

#aliyun
RUN sed -i "s/archive.ubuntu.com/mirrors.aliyun.com/g" /etc/apt/sources.list
ENV DEBIAN_FRONTEND noninteractive
#jdk
ADD jdk-8u231-linux-x64.tar.gz /usr/local
ENV JAVA_HOME /usr/local/jdk1.8.0_231
ENV JRE_HOME ${JAVA_HOME}/jre
ENV CLASSPATH ${JAVA_HOME}/lib:${JRE_HOME}/lib
ENV PATH ${JAVA_HOME}/bin:$PATH

#idea
RUN apt-get update && apt-get install -y gedit --fix-missing && apt-get clean && rm -rf /var/lib/apt/lists/*
ADD ideaIC-2019.3.tar.gz /usr/local
ADD .IdeaIC2019.3 ~
ENV PATH /usr/local/idea-IC-193.5233.102/bin:$PATH
