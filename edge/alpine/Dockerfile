ARG GLIBC_RELEASE=2.34-r0

FROM alpine:latest as base

WORKDIR /app

# Install glibc (https://gist.github.com/larzza/0f070a1b61c1d6a699653c9a792294be)
RUN apk --no-cache add wget ca-certificates libstdc++
ARG APK_GLIBC_VERSION=2.34-r0
ARG APK_GLIBC_FILE="glibc-${APK_GLIBC_VERSION}.apk"
ARG APK_GLIBC_BIN_FILE="glibc-bin-${APK_GLIBC_VERSION}.apk"
ARG APK_GLIBC_BASE_URL="https://github.com/sgerrand/alpine-pkg-glibc/releases/download/${APK_GLIBC_VERSION}"
RUN wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub \
  && wget "${APK_GLIBC_BASE_URL}/${APK_GLIBC_FILE}"     \
  && apk --no-cache add "${APK_GLIBC_FILE}"             \
  && wget "${APK_GLIBC_BASE_URL}/${APK_GLIBC_BIN_FILE}" \
  && apk --no-cache add "${APK_GLIBC_BIN_FILE}"         \
  && rm glibc-*

ENV BUN_INSTALL="/root/.bun"

RUN apk add curl unzip bash
RUN curl -fsSL https://bun.sh/install | bash
RUN ln -s $BUN_INSTALL/bin/bun /usr/local/bin/bun

RUN bun --version
