FROM alpine:3.23.0@sha256:51183f2cfa6320055da30872f211093f9ff1d3cf06f39a0bdb212314c5dc7375

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

RUN apk upgrade --no-cache \
    && apk add --no-cache \
    age=1.2.1-r8 \
    coreutils=9.7-r1 \
    curl=8.14.1-r2 \
    fscryptctl=1.2.0-r0 \
    git=2.49.1-r0 \
    gnupg=2.4.7-r0 \
    jose=14-r0 \
    openssl=3.5.4-r0 \
    py3-pip=25.1.1-r0 \
    python3=3.12.12-r0 \
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
