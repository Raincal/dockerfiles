FROM alpine:latest

LABEL maintainer="raincal.chen@gmail.com"

ENV GOPATH="/go" \
  LocalPath="download" \
  RemotePath="one:/Download" \
  Commands="--ignore-existing --stats-log-level NOTICE"

RUN apk add --no-cache --update alpine-sdk ca-certificates go git fuse fuse-dev \
  && go get -u -v github.com/ncw/rclone \
  && cp /go/bin/rclone /usr/sbin/ \
  && rm -rf /go \
  && apk del alpine-sdk go git \
  && rm -rf /tmp/* /var/cache/apk/* /var/lib/apk/lists/* \
  && mkdir -p ~/.config/rclone

CMD ["rclone", "--version"]