<h1 align=center>Docker Bun</h1>

Containerise your Bun apps with Docker! This is an unofficial docker image repository, covering the common base images. PRs to improve the images are welcome.

## Example Dockerfile

```Dockerfile
FROM ghcr.io/theotterlord/bun:alpine

WORKDIR /app

COPY package.json bun.lockb bunfig.toml ./

RUN bun install
# skip installing devDependencies in production
# RUN bun install --production

# copy app source
COPY . .

# run entrypoint file with bun
CMD ["bun", "index.js"]
```
