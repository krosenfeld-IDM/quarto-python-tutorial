FROM ghcr.io/mamba-org/micromamba

USER root

# Install Quarto and Git
RUN apt-get update && \
    apt-get install -y git curl && \
    curl -LO https://quarto.org/download/latest/quarto-linux-amd64.deb && \
    apt install -y ./quarto-linux-amd64.deb && \
    rm -rf /var/lib/apt/lists/*

USER mambauser

RUN micromamba create -n quarto-env python=3.10 -c conda-forge -y
SHELL ["micromamba", "run", "-n", "quarto-env", "/bin/bash", "-c"]

RUN micromamba install jupyterlab matplotlib plotly pandas -c conda-forge -y

SHELL ["/bin/bash", "-c"]
