FROM ubuntu:18.04
LABEL maintainer="tstav@163.com" version="1.0" description="ubuntu environment"

#aliyun
RUN sed -i "s/archive.ubuntu.com/mirrors.aliyun.com/g" /etc/apt/sources.list
ENV DEBIAN_FRONTEND noninteractive
#install vim wget latex
RUN apt-get update && apt-get upgrade -y && apt-get install -y texlive-full texmaker vim wget git g++ --fix-missing
#install anaconda3
RUN wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh -O ~/anaconda3.sh
RUN bash ~/anaconda3.sh -b -p /usr/local/anaconda3 && rm ~/anaconda3.sh
ENV PATH /usr/local/anaconda3/bin:$PATH
#set jupyter
RUN jupyter notebook --generate-config
RUN sed -i "s/#c.NotebookApp.ip = 'localhost'/c.NotebookApp.ip = '0.0.0.0'/g" /root/.jupyter/jupyter_notebook_config.py
RUN sed -i "s/#c.NotebookApp.notebook_dir = ''/c.NotebookApp.notebook_dir = '\/work'/g" /root/.jupyter/jupyter_notebook_config.py

#cmake
ADD cmake-3.16.0-Linux-x86_64.tar.gz /usr/local
ENV PATH /usr/local/cmake-3.16.0-Linux-x86_64/bin:$PATH

# Set timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
# Set locale
ENV LANG C.UTF-8 LC_ALL=C.UTF-8
#install jdk
ADD jdk-8u231-linux-x64.tar.gz /usr/local
ENV JAVA_HOME /usr/local/jdk1.8.0_231
ENV JRE_HOME ${JAVA_HOME}/jre
ENV CLASSPATH ${JAVA_HOME}/lib:${JRE_HOME}/lib
ENV PATH ${JAVA_HOME}/bin:$PATH
#install idea
ADD ideaIC-2019.3.tar.gz /usr/local
ADD .IdeaIC2019.3 ~
ENV PATH /usr/local/idea-IC-193.5233.102/bin:$PATH
#cuda
RUN apt-get update && apt-get install -y gnupg2 && \
    wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pin && \
    mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600　&& \
    wget http://developer.download.nvidia.com/compute/cuda/10.2/Prod/local_installers/cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb && \ 
    dpkg -i cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb && \
    apt-key add /var/cuda-repo-10-2-local-10.2.89-440.33.01/7fa2af80.pub && \
    apt-get update && apt-get -y install cuda && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm /var/cuda-repo-10-2-local-10.2.89-440.33.01/*.deb && \
    rm cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb