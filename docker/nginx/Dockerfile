FROM nginx:1.16.0-alpine

# 設定ファイルをコンテナ内にコピー
COPY ./conf.d/default.conf /etc/nginx/conf.d/default.conf

RUN apk --update add --no-cache tzdata && \
    cp /usr/share/zoneinfo/Asia/Tokyo /etc/localtime && \
    apk del tzdata
