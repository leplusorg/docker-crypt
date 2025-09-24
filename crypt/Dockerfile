FROM alpine:3.22.1@sha256:4bcff63911fcb4448bd4fdacec207030997caf25e9bea4045fa6c8c44de311d1

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

RUN apk upgrade --no-cache \
    && apk add --no-cache \
    age=1.2.1-r7 \
    coreutils=9.7-r1 \
    curl=8.14.1-r1 \
    fscryptctl=1.2.0-r0 \
    git=2.49.1-r0 \
    gnupg=2.4.7-r0 \
    jose=14-r0 \
    openssl=3.5.3-r0 \
    py3-pip=25.1.1-r0 \
    python3=3.12.11-r0 \
    xmlsec=1.3.7-r0 \
    && apk cache --no-cache clean \
    && rm -rf /var/cache/apk/*

RUN adduser \
  --home "${USER_HOME}" \
  --uid "${USER_ID}" \
  --gecos "${USER_GECOS}" \
  --disabled-password \
  "${USER_NAME}"

USER "${USER_NAME}"

ENV HOME="${USER_HOME}"

WORKDIR "${HOME}"
