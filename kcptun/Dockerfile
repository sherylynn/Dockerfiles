# Pull base image.
FROM golang:alpine
MAINTAINER Sherylynn <352281674@qq.com>

# install openssl and the complete wget
RUN apk --update add --no-cache git

RUN go get github.com/xtaci/kcptun/client && \
    go get github.com/xtaci/kcptun/server && \
    mkdir config
EXPOSE 29900/udp
EXPOSE 12948

COPY server.json /config/config.json

CMD ["sh", "-c", "v2ray -c /config/config.json"]
#还不清楚怎么运行好