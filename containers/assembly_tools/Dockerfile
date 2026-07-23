# ── draigonsnake assembly tools environment ─────────────────────────────────────
# Tools: quast, multiqc
# Build from the repository root:
#   docker build -f containers/assembly_tools/Dockerfile -t draigonsnake-assembly-tools .
FROM mambaorg/micromamba:1.5.8-jammy

LABEL org.opencontainers.image.title="draigonsnake-assembly-tools"
LABEL org.opencontainers.image.description="draigonsnake pipeline – assembly QC (QUAST) and report aggregation (MultiQC)"
LABEL org.opencontainers.image.source="https://github.com/TTS577/draigonsnake"

USER root
RUN apt-get update && apt-get install -y --no-install-recommends \
        procps \
        bash \
    && rm -rf /var/lib/apt/lists/*

USER $MAMBA_USER
COPY --chown=$MAMBA_USER:$MAMBA_USER envs/draigonsnake-assembly_tools.yaml /tmp/env.yaml
RUN micromamba install -y -n base -f /tmp/env.yaml \
    && micromamba clean --all --yes

ENV PATH="/opt/conda/bin:$PATH"
