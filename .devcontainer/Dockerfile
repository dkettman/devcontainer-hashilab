FROM alpine:3.23

ENV TERRAFORM_VERSION=1.7.4
ENV PACKER_VERSION=1.10.3
ENV VAULT_VERSION=1.16.1
ENV CONSUL_VERSION=1.17.2

RUN apk add --no-cache \
    python3 \
    py3-pip \
    pipx \
    curl \
    unzip \
    bash

RUN pipx install --include-deps ansible && \
    pipx inject --include-apps ansible ansible-lint && \
    pipx runpip ansible install hvac && \
    pipx ensurepath --force --all-shells

RUN curl -fsSL https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -o terraform.zip && \
    unzip terraform.zip && \
    mv terraform /usr/local/bin/ && \
    rm terraform.zip

RUN curl -fsSL https://releases.hashicorp.com/packer/${PACKER_VERSION}/packer_${PACKER_VERSION}_linux_amd64.zip -o packer.zip && \
    unzip packer.zip && \
    mv packer /usr/local/bin/ && \
    rm packer.zip

RUN curl -fsSL https://releases.hashicorp.com/vault/${VAULT_VERSION}/vault_${VAULT_VERSION}_linux_amd64.zip -o vault.zip && \
    unzip vault.zip && \
    mv vault /usr/local/bin/ && \
    rm vault.zip

RUN curl -fsSL https://releases.hashicorp.com/consul/${CONSUL_VERSION}/consul_${CONSUL_VERSION}_linux_amd64.zip -o consul.zip && \
    unzip consul.zip && \
    mv consul /usr/local/bin/ && \
    rm consul.zip

WORKDIR /workspace

CMD ["sh"]
