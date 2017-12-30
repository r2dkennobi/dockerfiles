FROM alpine:3.7
LABEL maintainer "Kenny Yokoyama <r2dkennobi@tuta.io>"

ENV PATH="/root/.local/bin:$PATH:/root/.cabal/bin"

RUN apk add --no-cache ghc cabal curl \
  && curl -sSL https://get.haskellstack.org/ | sh

CMD ["sh"]
