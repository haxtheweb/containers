FROM ubuntu:latest
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
RUN apt update -y && apt upgrade -y && apt install curl -y
USER ubuntu

ENV HOME=/home/ubuntu
WORKDIR $HOME
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash && \
 \. "$HOME/.nvm/nvm.sh" && nvm install --lts && npm install -g @haxtheweb/create

CMD ["/bin/bash"]