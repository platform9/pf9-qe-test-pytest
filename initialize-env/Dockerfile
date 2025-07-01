FROM ubuntu:22.04

RUN apt-get update && apt-get install -y \
    curl \
    tar \
    bash \
    git

# Set environment variables (optional)
ARG BASH_DEBUG
ENV BASH_DEBUG=${BASH_DEBUG}

# Create working directory
WORKDIR /workspace

# Copy repo if needed (or mount at runtime)
# COPY ./my_repo ./my_repo

# Source bashrc and run script
RUN bash -c '\
    set -eo pipefail && \
    curl -fSL https://artifactory.platform9.horse:443/artifactory/pf9-bins/python/3.9.18/python3.9.18.tgz -o python3.9.18.tgz && \
    tar -zxvf python3.9.18.tgz'

ENV LD_LIBRARY_PATH=/opt/pf9/python/lib
ENV PYTHON_BIN=/opt/pf9/python/bin/python3
ENV SUITE_DIRS=test_suites/kaapi/byoh

# Default command (optional override)
CMD ["/bin/bash"]
