FROM debian:wheezy
MAINTAINER vmintam <vmintam@gmail.com>

RUN echo "deb http://nginx.org/packages/debian/ wheezy nginx" >> /etc/apt/sources.list.d/nginx.list
RUN apt-key adv --fetch-keys "http://nginx.org/keys/nginx_signing.key"

RUN apt-get update && apt-get -y dist-upgrade
RUN apt-get -y install nginx openssl ca-certificates
RUN mkdir /etc/nginx/sites

ADD nginx.conf /etc/nginx/nginx.conf
ADD upstreams.conf /etc/nginx/conf.d/upstreams.conf
ADD default.conf /etc/nginx/sites/default.conf

VOLUME ["/etc/nginx/sites", "/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx"]

EXPOSE 80
EXPOSE 443

ENTRYPOINT ["nginx"]
CMD []
