FROM ubuntu:18.04
LABEL maintainer="tstav@163.com" version="1.0" description="ubuntu environment"

#aliyun
RUN sed -i "s/archive.ubuntu.com/mirrors.aliyun.com/g" /etc/apt/sources.list
ENV DEBIAN_FRONTEND noninteractive
#install vim wget latex
RUN apt-get update && apt-get install -y vim wget texlive-full texmaker --fix-missing
#install anaconda3
RUN wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh -O ~/anaconda3.sh
RUN bash ~/anaconda3.sh -b -p /usr/local/anaconda3 && rm ~/anaconda3.sh
ENV PATH /usr/local/anaconda3/bin:$PATH
#set jupyter
RUN jupyter notebook --generate-config
RUN sed -i "s/#c.NotebookApp.ip = 'localhost'/c.NotebookApp.ip = '0.0.0.0'/g" /root/.jupyter/jupyter_notebook_config.py
RUN sed -i "s/#c.NotebookApp.notebook_dir = ''/c.NotebookApp.notebook_dir = '\/work'/g" /root/.jupyter/jupyter_notebook_config.py

#cmake
RUN wget https://cmake.org/files/v3.16/cmake-3.16.0-Linux-x86_64.tar.gz
RUN tar xzvf cmake-3.16.0-Linux-x86_64.tar.gz -C /usr/local && rm cmake-3.16.0-Linux-x86_64.tar.gz
ENV PATH /usr/local/cmake-3.16.0-Linux-x86_64/bin:$PATH
#for cuda dependence
RUN apt-get update && apt-get install -y gnupg gnupg2 gnupg1
#install cuda
RUN wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pin
RUN mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
RUN wget http://developer.download.nvidia.com/compute/cuda/10.2/Prod/local_installers/cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb
RUN dpkg -i cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb
RUN apt-key add /var/cuda-repo-10-2-local-10.2.89-440.33.01/7fa2af80.pub
RUN apt-get update && apt-get -y install cuda --fix-missing
RUN rm cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb

# Set timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
# Set locale
ENV LANG C.UTF-8 LC_ALL=C.UTF-8
