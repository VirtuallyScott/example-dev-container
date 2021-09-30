FROM alpine:edge

RUN apk update
RUN apk add --no-cache bash build-base ruby curl sudo gzip ncurses glib file procps git ruby-bigdecimal ruby-etc libc6-compat make ruby-irb ruby-json ruby-test-unit gcc ca-certificates wget libc6-compat libgcc gcompat

RUN adduser -D -s /bin/bash linuxbrew && \
    #usermod -aG sudo linuxbrew && \
    echo 'linuxbrew ALL=(ALL) NOPASSWD:ALL' >>/etc/sudoers && \
    su -l linuxbrew

#CMD /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
#ENV PATH=$HOME/.linuxbrew/bin:$HOME/.linuxbrew/sbin:$PATH
#RUN brew update && \
#    brew docter

#USER root
#ENV PATH=$HOME/.linuxbrew/bin:$HOME/.linuxbrew/sbin:$PATH

#USER linuxbrew
#RUN brew install terraform terragrunt tflint terraformer zip unzip azure-cli jinja2-cli kubernetes-cli kube-linter kompose helm node npm nvm ansible google-go


