
# ---------- Base Stage ----------
FROM ubuntu:22.04-slim AS base
SHELL ["/bin/bash", "-o", "pipefail", "-c"]
RUN apt-get update -y && apt-get upgrade -y && \
	apt-get install -y curl sudo && \
	useradd -ms /bin/bash ubuntu && \
	usermod -aG sudo ubuntu && \
	chown -R ubuntu:ubuntu /home/ubuntu && \
	apt-get clean && rm -rf /var/lib/apt/lists/*

ENV HOME=/home/ubuntu
WORKDIR $HOME

# ---------- Standard Environment ----------
FROM base AS standard
USER ubuntu
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash && \
	. "$HOME/.nvm/nvm.sh" && nvm install --lts && npm install -g @haxtheweb/create
CMD ["/bin/bash"]

# ---------- Dev Environment ----------
FROM base AS dev
USER ubuntu
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash && \
	. "$HOME/.nvm/nvm.sh" && nvm install --lts && npm install -g @haxtheweb/create yarn && \
	yarn global add symlink-dir @web/test-runner @web/test-runner-commands \
	@web/test-runner-puppeteer @web/test-runner-playwright lerna web-component-analyzer && \
	npm completion >> ~/.bashrc
CMD ["/bin/bash"]