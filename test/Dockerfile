FROM node:0.10
MAINTAINER vmintam <vmintam@gmail.com>
LABEL "rating"="Five stars" "class"="First class"
USER root
ENV AP /data/app
ENV SCPATH /etc/supervisor/conf.d
RUN apt-get -y update

#the daemon
RUN apt-get install -y supervisor
RUN mkdir -p /var/log/supervisor

#supervisord config
ADD ./supervisord/conf.d/* $SCPATH/

#Application Code
ADD *.js* $AP/

WORKDIR $AP/

RUN npm install

CMD ["supervisord", "-n"]



