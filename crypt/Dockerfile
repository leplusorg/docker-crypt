FROM alpine:3.21.3@sha256:a8560b36e8b8210634f77d9f7f9efd7ffa463e380b75e2e74aff4511df3ef88c

HEALTHCHECK NONE

ENTRYPOINT []

ARG USER_NAME=default
ARG USER_HOME=/home/default
ARG USER_ID=1000
ARG USER_GECOS=Default

SHELL ["/bin/ash", "-euo", "pipefail", "-c"]

# hadolint ignore=DL3019
RUN apk -U upgrade \
    && apk add \
    age=1.2.1-r2 \
    fscryptctl=1.2.0-r0 \
    gnupg=2.4.7-r0 \
    jose=13-r0 \
    openssl=3.3.3-r0 \
    py3-pip=24.3.1-r0 \
    python3=3.12.9-r0 \
    xmlsec=1.3.7-r0 \
    && if apk -u list | grep -q -e . ; then \
      apk -u list ; \
      exit 1 ; \
    fi \
    && rm -rf /var/cache/apk/*

RUN adduser \
  --home "${USER_HOME}" \
  --uid "${USER_ID}" \
  --gecos "${USER_GECOS}" \
  --disabled-password \
  "${USER_NAME}"

ENV HOME="${USER_HOME}"

USER "${USER_NAME}"

WORKDIR "${HOME}"
