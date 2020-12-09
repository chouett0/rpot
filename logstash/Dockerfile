FROM docker.elastic.co/logstash/logstash-oss:6.3.0

USER root
COPY ./update-geoip.sh /usr/local/bin/update-geoip.sh

COPY ./*.mmdb* /tmp/
#COPY ./GeoLite2-City.mmdb /tmp/GeoLite2-City.mmdb
#COPY ./GeoLite2-Country.mmdb  /tmp/GeoLite2-Country.mmdb

WORKDIR /tmp
RUN mkdir -p /etc/logstash/conf.d/translate/
COPY *.csv /etc/logstash/conf.d/translate/
USER logstash
RUN /usr/local/bin/update-geoip.sh
