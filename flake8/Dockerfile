FROM alpine:3.7
LABEL maintainer "Kenny Yokoyama <r2dkennobi@tuta.io>"

ENV FLAKE8_VERSION 3.5.0

RUN apk add --no-cache python3 && \
  python3 -m pip install flake8=="$FLAKE8_VERSION"

ENTRYPOINT ["/usr/bin/flake8"]
