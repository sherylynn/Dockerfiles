# Pull base image.
FROM alpine
MAINTAINER Sherylynn <352281674@qq.com>

# install openssl and the complete wget
RUN apk --update add openssl wget \
 && rm -rf /var/cache/apk/*

ENV LANG zh_CN.UTF-8