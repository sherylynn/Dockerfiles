# Pull base image.
FROM mwendler/wget
MAINTAINER Sherylynn <352281674@qq.com>

# 输入下载地址
ENV LANG en_US.UTF-8
ENV DOWNLOAD_URL https://qemu.weilnetz.de/w64/qemu-w64-setup-20160823.exe
RUN ls && \
    wget -q ${DOWNLOAD_URL}