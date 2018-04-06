FROM archlinux/base
LABEL maintainer "Kenny Yokoyama <r2dkennobi@tuta.io>"

ENV CLANG_VERSION=6.0.0-1

RUN pacman -Syy && pacman -S clang="$CLANG_VERSION" --noconfirm

ENTRYPOINT ["clang"]
