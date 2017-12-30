FROM alpine:3.7 as builder
LABEL maintainer "Kenny Yokoyama <r2dkennobi@tuta.io>"
ENV PATH="/root/.local/bin:$PATH:/root/.cabal/bin"
RUN apk add --no-cache ghc cabal curl musl-dev zlib-dev \
  && curl -sSL https://get.haskellstack.org/ | sh
RUN cabal update && cabal install shellcheck

FROM alpine:3.7
ENV PATH="/root/.local/bin:$PATH"
COPY --from=builder /root/.cabal/bin/shellcheck /usr/local/bin/
COPY --from=builder /usr/lib/libgmp.so.10 /usr/lib/
COPY --from=builder /usr/lib/libffi.so.6 /usr/lib/
COPY --from=builder /lib/ld-musl-x86_64.so.1 /lib/
CMD ["shellcheck"]
