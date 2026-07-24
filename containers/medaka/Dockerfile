# ── draigonsnake medaka environment ──────────────────────────────────────────────
# Tools: medaka 1.11.3 (pinned), libdeflate
# Build from the repository root:
#   docker build -f containers/medaka/Dockerfile -t draigonsnake-medaka .
FROM mambaorg/micromamba:1.5.8-jammy

LABEL org.opencontainers.image.title="draigonsnake-medaka"
LABEL org.opencontainers.image.description="draigonsnake pipeline – long-read polishing with Medaka"
LABEL org.opencontainers.image.source="https://github.com/TTS577/draigonsnake"

USER root
RUN apt-get update && apt-get install -y --no-install-recommends \
        procps \
        bash \
    && rm -rf /var/lib/apt/lists/*

USER $MAMBA_USER
COPY --chown=$MAMBA_USER:$MAMBA_USER envs/draigonsnake_medaka.yaml /tmp/env.yaml
RUN micromamba install -y -n base -f /tmp/env.yaml \
    && micromamba clean --all --yes

ENV PATH="/opt/conda/bin:$PATH"
