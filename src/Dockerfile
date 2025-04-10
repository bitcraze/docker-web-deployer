FROM ubuntu:24.04

LABEL org.opencontainers.image.authors="arnaud@bitcraze.io"

RUN apt-get update && apt-get install -y --no-install-recommends \
		python3 python3-yaml \
		git curl \
		ca-certificates \
		openssh-client \
  		jq \
		s3cmd \
	&& rm -rf /var/lib/apt/lists/*

# Install docker
ENV DOCKER_VERSION=19.03.1
RUN curl -fsSLO https://download.docker.com/linux/static/stable/x86_64/docker-${DOCKER_VERSION}.tgz && tar --strip-components=1 -xvzf docker-${DOCKER_VERSION}.tgz -C /usr/local/bin

# Install kubectl
ENV KUBECTL_VERSION=1.31.6
RUN curl -L https://dl.k8s.io/release/v${KUBECTL_VERSION}/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl \
 && chmod +x /usr/local/bin/kubectl

WORKDIR /module
