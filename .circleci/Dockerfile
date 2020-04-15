FROM alpine/git:latest
ENV HELM_VERSION=3.1.2

RUN wget https://get.helm.sh/helm-v${HELM_VERSION}-linux-amd64.tar.gz -O helm.tar.gz && \
  tar -xvzf helm.tar.gz && \
  cp linux-amd64/helm /usr/local/bin/helm && \
  rm -rf helm.tar.gz linux-amd64/