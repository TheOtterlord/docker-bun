FROM ubuntu:latest

WORKDIR /app

ENV BUN_INSTALL="/root/.bun"

RUN apt-get update
RUN apt-get install curl unzip -y
RUN curl -fsSL https://bun.sh/install | bash
RUN ln -s $BUN_INSTALL/bin/bun /usr/local/bin/bun

RUN bun --version
