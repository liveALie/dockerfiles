FROM ubuntu:18.04
LABEL maintainer="tstav@163.com" version="1.0" description="ubuntu environment"

#aliyun
RUN sed -i "s/archive.ubuntu.com/mirrors.aliyun.com/g" /etc/apt/sources.list
ENV DEBIAN_FRONTEND noninteractive
#install vim
RUN apt-get update && apt-get install -y vim wget snapd snapcraft --fix-missing
RUN wget https://download.jetbrains.8686c.com/idea/ideaIU-2019.3.tar.gz
RUN tar xzvf ideaIU-2019.3.tar.gz -C /usr/local && rm ideaIU-2019.3.tar.gz
#jdk
RUN wget --no-check-certificate --no-cookies --http-user= --http-password= --header "Cookie: oraclelicense=accept-securebackup-cookie" https://download.oracle.com/otn/java/jdk/8u231-b11/5b13a193868b4bf28bcb45c792fce896/jdk-8u231-linux-x64.tar.gz
RUN tar xzvf jdk-8u231-linux-x64.tar.gz -C /usr/local && rm jdk-8u231-linux-x64.tar.gz
ENV JAVA_HOME /usr/local/jdk1.8.0_231
ENV JRE_HOME ${JAVA_HOME}/jre
ENV CLASSPATH ${JAVA_HOME}/lib:${JRE_HOME}/lib
ENV PATH ${JAVA_HOME}/bin:$PATH