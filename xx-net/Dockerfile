# Pull base image.
FROM sherylynn/wget
MAINTAINER Sherylynn <352281674@qq.com>

# install packages
RUN apk --update add --no-cache libffi-dev py-pip
ENV XX_VERSION 3.2.6
ENV DOWNLOAD_URL https://codeload.github.com/XX-net/XX-Net/tar.gz/${XX_VERSION}
RUN mkdir -p /opt && \
    cd /opt && \
    wget -q --no-check-certificate ${DOWNLOAD_URL} && \
    tar -xzf ${XX_VERSION} && \
    rm ${XX_VERSION} && \
    ls
RUN apk --update add --no-cache tini
ENTRYPOINT ["/sbin/tini", "--"]
#    wget -q ${ANDROID_TOOLS_URL} && \
#    unzip -n ${ANDROID_TOOLS_FILENAME} -d android-sdk-linux/tools && \
#    rm ${ANDROID_TOOLS_FILENAME} && \
#    wget -q ${ANDROID_PLATFORM_URL} && \
#    unzip -n ${ANDROID_PLATFORM_FILENAME} -d  && \
#    rm ${ANDROID_PLATFORM_FILENAME} && \
ENV LANG zh_CN.UTF-8