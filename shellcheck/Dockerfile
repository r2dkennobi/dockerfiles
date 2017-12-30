FROM r2dkennobi:alpin-haskell
LABEL maintainer "Kenny Yokoyama <r2dkennobi@tuta.io>"

RUN apk add --no-cache musl-dev zlib-dev
RUN cabal update && cabal install shellcheck

CMD ["shellcheck"]
