FROM alpine

LABEL maintainer="Ronny Standtke"

ENV TZ=Europe/Berlin \
    CheckInterval=10 \
    InfluxDbIp=192.168.178.2 \
    InfluxDbCollectdPort=25826 \
    FritzBoxIp=192.168.178.1 \
    FritzBoxUser=collectd \
    FritzBoxPassword=mypassword

RUN apk update \
    && apk upgrade \
    && apk add --no-cache tzdata collectd collectd-python collectd-network py3-pip libxml2-dev libxslt-dev gcc musl-dev python3-dev \
    && pip install fritzcollectd

ADD collectd.conf /etc/collectd/collectd.conf
ADD start.sh /start.sh
RUN chmod +x /start.sh

ENV DEBUG=false

CMD ["/start.sh"]