ARG NODE_BASE_IMAGE=node:24-trixie-slim

FROM ${NODE_BASE_IMAGE}

ARG NPM_VERSION=12.1.0
ARG FIREBASE_TOOLS_VERSION

RUN test -n "${NPM_VERSION}" \
    && test -n "${FIREBASE_TOOLS_VERSION}" \
    && apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get upgrade -y \
    && rm -rf /var/lib/apt/lists/* \
    && npm install --global --no-audit --no-fund --engine-strict \
        "npm@${NPM_VERSION}" \
    && node --version \
    && npm --version \
    && npm install --global --no-audit --no-fund --engine-strict \
        --allow-scripts=protobufjs,re2 \
        "firebase-tools@${FIREBASE_TOOLS_VERSION}" \
    && firebase --version \
    && rm -rf /root/.npm
