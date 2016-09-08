# Pull base image.
FROM sherylynn/wget
MAINTAINER Sherylynn <352281674@qq.com>

RUN apk --update add --no-cache py-pip
RUN pip install shadowsocks && \
    pip install supervisor
# 还不清楚怎么运行好
ADD supervisord.conf /etc/supervisord.conf
ADD client_linxux_amd64 /usr/bin/kcptun-c
ADD server_linxux_amd64 /usr/bin/kcptun-s

RUN chmod +x /usr/bin/kcptun-c && \
    chmod +x /usr/bin/kcptun-s

EXPOSE 8087/tcp
EXPOSE 8989/tcp
EXPOSE 8989/udp
EXPOSE 29900/udp
CMD ["/usr/bin/supervisord"]