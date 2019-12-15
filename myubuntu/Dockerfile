FROM ubuntu:18.04
LABEL maintainer="tstav@163.com" version="1.0" description="ubuntu environment"

#aliyun
COPY sources.list /etc/apt/sources.list
ENV DEBIAN_FRONTEND noninteractive
#install vim
RUN apt-get update && apt-get install -y vim wget texlive-full texmaker --fix-missing

RUN wget https://repo.anaconda.com/archive/Anaconda3-2019.10-Linux-x86_64.sh -O ~/anaconda3.sh
RUN bash ~/anaconda3.sh -b -p /usr/local/anaconda3 && rm ~/anaconda3.sh
ENV PATH /usr/local/anaconda3/bin:$PATH

RUN jupyter notebook --generate-config
COPY jupyter_notebook_config.py /root/.jupyter

RUN apt-get update && apt-get install -y gnupg gnupg2 gnupg1

RUN wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/cuda-ubuntu1804.pin
RUN mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
RUN wget http://developer.download.nvidia.com/compute/cuda/10.2/Prod/local_installers/cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb
RUN dpkg -i cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb
RUN apt-key add /var/cuda-repo-10-2-local-10.2.89-440.33.01/7fa2af80.pub
RUN apt-get update && apt-get -y install cuda
RUN rm cuda-repo-ubuntu1804-10-2-local-10.2.89-440.33.01_1.0-1_amd64.deb