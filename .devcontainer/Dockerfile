FROM mcr.microsoft.com/devcontainers/java:21-bookworm

ARG TZ
ENV TZ="$TZ"

ARG CLAUDE_CODE_VERSION=latest

# Set the default shell for the 'vscode' user
ENV SHELL /bin/zsh

# Install global packages
ENV NPM_CONFIG_PREFIX=/usr/local/share/npm-global
ENV PATH=$PATH:/usr/local/share/npm-global/bin

# Set the default editor and visual
ENV EDITOR nano
ENV VISUAL naoo

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      dnsutils \ 
      procps \
      sudo \
      fzf \
      zsh \
      man-db \
      unzip \
      gnupg2 \
      gh \
      iptables \
      ipset \
      iproute2 \
      aggregate \
      python3-venv \
      nodejs \
      npm \
      jq \
      nano \
      vim && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

    # Ensure default vscode user has access to /usr/local/share
RUN mkdir -p /usr/local/share/npm-global && \
  chown -R vscode:vscode /usr/local/share

ARG USERNAME=vscode

# Persist bash history.
RUN SNIPPET="export PROMPT_COMMAND='history -a' && export HISTFILE=/commandhistory/.bash_history" \
  && mkdir /commandhistory \
  && touch /commandhistory/.bash_history \
  && chown -R $USERNAME /commandhistory

# Set `DEVCONTAINER` environment variable to help with orientation
ENV DEVCONTAINER=true

# Create workspace and config directories and set permissions
RUN mkdir -p /workspace /home/vscode/.claude && \
  chown -R vscode:vscode /workspace /home/vscode/.claude

# Create Python virtual environment for programming languages course
RUN python3 -m venv /home/vscode/venv && \
  chown -R vscode:vscode /home/vscode/venv

# Add virtual environment activation to shell profiles
RUN echo "source /home/vscode/venv/bin/activate" >> /home/vscode/.bashrc && \
  echo "source /home/vscode/venv/bin/activate" >> /home/vscode/.zshrc

# Default powerline10k theme
ARG ZSH_IN_DOCKER_VERSION=1.2.0
RUN sh -c "$(wget -O- https://github.com/deluan/zsh-in-docker/releases/download/v${ZSH_IN_DOCKER_VERSION}/zsh-in-docker.sh)" -- \
  -p git \
  -p fzf \
  -a "source /usr/share/doc/fzf/examples/key-bindings.zsh" \
  -a "source /usr/share/doc/fzf/examples/completion.zsh" \
  -a "export PROMPT_COMMAND='history -a' && export HISTFILE=/commandhistory/.bash_history" \
  -x

# Install Claude
RUN npm install -g @anthropic-ai/claude-code@${CLAUDE_CODE_VERSION}

# Copy and set up firewall script
COPY init-firewall.sh /usr/local/bin/
USER root
RUN chmod +x /usr/local/bin/init-firewall.sh && \
  echo "vscode ALL=(root) NOPASSWD: /usr/local/bin/init-firewall.sh" > /etc/sudoers.d/vscode-firewall && \
  chmod 0440 /etc/sudoers.d/vscode-firewall

USER vscode
