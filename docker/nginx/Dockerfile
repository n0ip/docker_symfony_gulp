FROM alpine:3.4

MAINTAINER Vincent Composieux <vincent.composieux@gmail.com>

RUN apk add --update nginx
RUN apk add --no-cache --repository http://nl.alpinelinux.org/alpine/edge/community shadow
RUN rm -rf /var/cache/apk/* && rm -rf /tmp/*

ADD nginx.conf /etc/nginx/
ADD www.conf /etc/nginx/conf.d/

ARG UID
ARG GUID
# RUN groupadd -g $GUID www-data
RUN adduser -u $UID -D -g '' -G www-data www-data
RUN groupmod -g $GUID www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
