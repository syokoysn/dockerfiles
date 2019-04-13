FROM ubuntu:19.04

RUN apt-get update && apt update  &&\
    apt-get install -y sudo &&\
    apt-get install -y apt-utils

RUN sudo apt install -y mecab  &&\
    sudo apt install -y libmecab-dev &&\
    sudo apt install -y mecab-ipadic-utf8

RUN sudo apt install -y git &&\
    sudo apt install -y make &&\
    sudo apt install -y curl &&\
    sudo apt install -y xz-utils &&\
    sudo apt install -y file

# setting mecab
RUN mkdir /lib/mecab/dic
WORKDIR /tmp
RUN git clone --depth 1 https://github.com/neologd/mecab-ipadic-neologd.git
WORKDIR mecab-ipadic-neologd

RUN pwd
RUN bin/install-mecab-ipadic-neologd -n -u --prefix /usr/lib/mecab/dic/mecab-ipadic-neologd -y

WORKDIR /


RUN pwd
RUN sed -i -e '/dicdir /c dicdir  = /usr/lib/mecab/dic/mecab-ipadic-neologd'  /etc/mecabrc 

