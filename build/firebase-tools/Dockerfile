ARG NODE_BASE_IMAGE

FROM ${NODE_BASE_IMAGE}

ARG FIREBASE_TOOLS_VERSION

RUN test -n "${FIREBASE_TOOLS_VERSION}" \
    && node --version \
    && npm --version \
    && npm install --global --no-audit --no-fund \
        "firebase-tools@${FIREBASE_TOOLS_VERSION}" \
    && firebase --version \
    && rm -rf /root/.npm
