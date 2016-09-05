# Pull base image.
FROM golang:latest
MAINTAINER Sherylynn <352281674@qq.com>
ENV V2RAY_VERSION v1.24.3
#ENV V2RAY_VERSION custom
ENV V2RAY /v2ray
ENV V2RAY_CONTENT $V2RAY/content
ENV V2RAY_CONFIG_CONTENT $V2RAY_CONTENT/config
ENV V2RAY_LOG_CONTENT $V2RAY_CONTENT/logs
RUN mkdir $V2RAY
RUN go get -u github.com/v2ray/v2ray-core/...
#RUN go get -u ./...
RUN rm -f $GOPATH/bin/build
RUN go install github.com/v2ray/v2ray-core/tools/build
RUN $GOPATH/bin/build
RUN mv $GOPATH/bin/v2ray-$V2RAY_VERSION-linux-64/v2ray /usr/local/bin/

RUN mkdir -p $V2RAY_CONFIG_CONTENT && \
    mkdir -p $V2RAY_LOG_CONTENT
COPY server-config $V2RAY_CONFIG_CONTENT/config.json

VOLUME $V2RAY_CONTENT
EXPOSE 9099
EXPOSE 1081
CMD ["sh", "-c", "v2ray -config $V2RAY_CONFIG_CONTENT/config.json"]