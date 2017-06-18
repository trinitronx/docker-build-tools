FROM alpine:3.6

MAINTAINER James Cuzella @trinitronx https://keybase.io/trinitronx/

RUN set -x                  && \
    apk --update upgrade    && \
    apk add ca-certificates && \
    apk add build-base && \
    rm -rf /var/cache/apk/*

