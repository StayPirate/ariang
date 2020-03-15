FROM alpine:latest

LABEL maintainer="Gianluca Gabrielli" mail="tuxmealux+dockerhub@protonmail.com"
LABEL description="Aria2c daemon."
LABEL website="https://github.com/StayPirate/alpine-ariang"

ARG GUID=1000
ARG ARIA2_USER=aria2

RUN addgroup -g $GUID $ARIA2_USER && \
    adduser -S -u $GUID -G $ARIA2_USER $ARIA2_USER && \
    apk update && \
    apk add --no-cache aria2 && \
    mkdir /aria2 && \
    mkdir -p /aria2/.config && \
    mkdir -p /aria2/Downloads && \
    touch /aria2/.aria2-session && \
    touch /aria2/.dht.dat && \
    chown -R $ARIA2_USER:$ARIA2_USER /aria2

COPY --chown=$ARIA2_USER:$ARIA2_USER aria2.conf /aria2/.config

#JSON-RPC
EXPOSE 6800/tcp
#DHT
EXPOSE 6882/udp
#Torrent
EXPOSE 50001/tcp

USER $ARIA2_USER

CMD ["aria2c", "--conf-path", "/aria2/.config/aria2.conf"]