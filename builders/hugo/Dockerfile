FROM golang:1 AS go-toolchain

# Keep Node/npm as the final runtime so firebase-tools runs on its supported
# Node.js runtime. Copy only the Go toolchain from the Go image.
FROM node:slim

ARG HUGO_VERSION=0.166.0
ARG HUGO_SHA256=45228f5a52eb118b0ca168068f01d7df0447314a24056f1d29667ed9fc368308

COPY --from=go-toolchain /usr/local/go /usr/local/go

ENV GOROOT=/usr/local/go \
    GOPATH=/go \
    GOTOOLCHAIN=local \
    PATH=/usr/local/go/bin:/go/bin:${PATH} \
    NPM_CONFIG_UPDATE_NOTIFIER=false

RUN apt-get update \
    && apt-get install --yes --no-install-recommends \
      bash \
      ca-certificates \
      curl \
      findutils \
      git \
      gawk \
      tar \
    && rm -rf /var/lib/apt/lists/* \
    && mkdir -p /go \
    && curl --fail --location --silent --show-error \
      --output /tmp/hugo.tar.gz \
      "https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_${HUGO_VERSION}_Linux-64bit.tar.gz" \
    && printf '%s  %s\n' "${HUGO_SHA256}" /tmp/hugo.tar.gz | sha256sum --check --strict - \
    && tar -xzf /tmp/hugo.tar.gz -C /usr/local/bin hugo \
    && rm /tmp/hugo.tar.gz \
    && npm install --global --no-audit --no-fund firebase-tools@latest \
    && hugo version \
    && go version \
    && node --version \
    && firebase --version

WORKDIR /workspace

# node:slim has its own entrypoint wrapper. Cloud Build overrides it per step,
# but clear it here so the image also behaves like a normal build tool image.
ENTRYPOINT []
CMD ["bash"]
