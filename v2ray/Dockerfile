# Pull base image.
FROM golang:alpine
MAINTAINER Sherylynn <352281674@qq.com>

# install openssl and the complete wget
RUN apk --update add --no-cache git

ENV V2RAY_VERSION custom
RUN go get -u v2ray.com/core/...
#RUN go get -u ./...
RUN rm -f $GOPATH/bin/build
RUN go install v2ray.com/core/tools/build
RUN $GOPATH/bin/build
RUN mv $GOPATH/bin/v2ray-$V2RAY_VERSION-linux-64/v2ray /usr/local/bin/
COPY server-config.json /config.json

VOLUME $V2RAY_CONTENT
EXPOSE 9099
EXPOSE 1081
CMD ["sh", "-c", "v2ray -config /config.json"]