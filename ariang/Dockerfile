FROM alpine:latest

COPY Caddyfile /

WORKDIR /usr/local/www

RUN apk update && \
    apk add --no-cache bash curl sudo gnupg && \
    curl https://getcaddy.com | bash -s personal && \
    mkdir -p /usr/local/www && \
    curl -o master.zip https://codeload.github.com/mayswind/AriaNg-DailyBuild/zip/master && \
    unzip master.zip -d . && \
    mv AriaNg-DailyBuild-master/* . && \
    rm -r AriaNg-DailyBuild-master master.zip

EXPOSE 80

WORKDIR /

CMD ["caddy"]