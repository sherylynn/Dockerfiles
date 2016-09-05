# Pull base image.
FROM golang:alpine
MAINTAINER Sherylynn <352281674@qq.com>

# install openssl and the complete wget
RUN apk --update add --no-cache git
RUN go get github.com/xtaci/kcptun/client && \
    go get github.com/xtaci/kcptun/server
ENV LANG zh_CN.UTF-8