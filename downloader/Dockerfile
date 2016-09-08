# Pull base image.
FROM sherylynn/wget
MAINTAINER Sherylynn <352281674@qq.com>

# 输入下载地址
ENV DOWNLOAD_URL http://dl-cdn.alpinelinux.org/alpine/v3.4/releases/x86_64/alpine-extended-3.4.3-x86_64.iso
ENV DOWNLOAD_PATH /alpine.iso
RUN wget -q --no-check-certificate ${DOWNLOAD_URL} -O ${DOWNLOAD_PATH}