# Base image updated by Renovate, update versionCompatibility on Alpine base bump
ARG BUILD_FROM=ghcr.io/home-assistant/base-python:3.14-alpine3.24-2026.11.1@sha256:46e6dcc59946421e1b6e3736cde545dab88d53f72654824230a38cbbaf0088ab

FROM $BUILD_FROM

ARG UNIVERSAL_SILABS_FLASHER=1.3.0

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
    org.opencontainers.image.description="Silicon Labs firmware flasher app" \
    org.opencontainers.image.source="https://github.com/home-assistant/app-silabs-flasher" \
    org.opencontainers.image.licenses="Apache License 2.0"
