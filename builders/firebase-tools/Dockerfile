FROM node:24-trixie-slim

ARG FIREBASE_TOOLS_VERSION

RUN npm install --global --no-audit --no-fund "firebase-tools@${FIREBASE_TOOLS_VERSION}" \
    && firebase --version \
    && npm cache clean --force
