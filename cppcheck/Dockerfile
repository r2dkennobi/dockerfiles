FROM alpine:3.7
LABEL maintainer "Kenny Yokoyama <r2dkennobi@tuta.io>"

ENV CPPCHECK_VERSION 1.81-r0

RUN apk add --no-cache cppcheck=="$CPPCHECK_VERSION"

CMD ["/usr/bin/cppcheck"]
