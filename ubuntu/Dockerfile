FROM ubuntu:bionic

RUN apt-get update && \
    apt-get install build-essential curl file git ruby-full sudo locales wget apt-transport-https software-properties-common gnupg --no-install-recommends -y
    # rm -rf /var/lib/apt/lists/*

RUN localedef -i en_US -f UTF-8 en_US.UTF-8

RUN cd /tmp
RUN echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
RUN curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key --keyring /usr/share/keyrings/cloud.google.gpg add -
RUN wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb && \
    dpkg -i packages-microsoft-prod.deb && \
    apt-get update && \
    apt-get install -y powershell google-cloud-sdk

RUN useradd -m -s /bin/bash linuxbrew && \
    usermod -aG sudo linuxbrew && \
    echo 'linuxbrew ALL=(ALL) NOPASSWD:ALL' >>/etc/sudoers

USER linuxbrew
RUN /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

USER root
ENV PATH="/home/linuxbrew/.linuxbrew/bin:${PATH}"

USER linuxbrew
COPY install.ps1 ~/
CMD sudo -H pwsh -file ~/install.ps1
RUN brew install terraform terragrunt tflint terraformer zip unzip azure-cli jinja2-cli kubernetes-cli kube-linter kompose helm node npm nvm ansible google-go
RUN curl -s "https://get.sdkman.io" | bash
RUN /bin/sh . "$HOME/.sdkman/bin/sdkman-init.sh"