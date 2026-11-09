# Base image updated by Renovate, update versionCompatibility on Alpine base bump
ARG BUILD_FROM=ghcr.io/home-assistant/base-python:3.13-alpine3.23-2026.10.3@sha256:e6d0458187f7180f303404a3a6bfb4a5a413410a1042b16fca33178cd3bd71f7

FROM $BUILD_FROM

ARG UNIVERSAL_SILABS_FLASHER=0.1.3

RUN \
    set -x \
    && apk add --no-cache \
        py3-pip \
        python3 \
    && pip3 install \
        --no-cache-dir \
        --prefer-binary \
        universal-silabs-flasher=="${UNIVERSAL_SILABS_FLASHER}"

COPY rootfs /

# use s6-overlay as init system
WORKDIR /
ENTRYPOINT ["/init"]

LABEL \
    org.opencontainers.image.title="Home Assistant App: Silicon Labs Flasher" \
    org.opencontainers.image.description="Silicon Labs firmware flasher add-on" \
    org.opencontainers.image.source="https://github.com/home-assistant/app-silabs-flasher" \
    org.opencontainers.image.licenses="Apache License 2.0"
