# How to run:
#
# $ docker build -t rust-gcc .
# $ docker run -it --rm --user $(id -u) -e USER=$USER -v $(pwd):/project rust-gcc

FROM alpine:3.7 as builder
LABEL maintainer "Kenny Yokoyama <r2dkennobi@tuta.io>"
RUN apk add --no-cache gcc musl-dev rust cargo
WORKDIR /project
