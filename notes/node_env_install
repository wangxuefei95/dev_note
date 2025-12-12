#!/bin/bash

source_terminal() {
  if [ -n "$ZSH_VERSION" ]; then
    [ -f ~/.zshrc ] && source ~/.zshrc
  elif [ -n "$BASH_VERSION" ]; then
    [ -f ~/.bashrc ] && source ~/.bashrc
  fi
}

source_terminal
node_version="22.11.0"
npm_registry="https://mirrors.huaweicloud.com/repository/npm/"

# 判断nvm是否已安装
if command -v nvm >/dev/null 2>&1; then
  echo "nvm already installed"
else
  echo "nvm installing..."
  bash -c "$(curl -fsSL https://gitee.com/RubyMetric/nvm-cn/raw/main/install.sh)"
  export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
    [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion" # This loads nvm bash_completion
fi

# 检查 Node 22.11.0 是否已安装
if nvm list | grep -q $node_version; then
  echo "Node $node_version already installed"
else
  echo "Installing Node $node_version..."
  nvm install $node_version
fi

# 使用指定版本的 Node.js
nvm use $node_version
nvm alias default $node_version
# 设置 npm 镜像源
npm config set registry $npm_registry
npm config get registry

# 判断pnpm是否已安装
if command -v pnpm >/dev/null 2>&1;
then
  echo "pnpm already installed"
else
  echo "pnpm installing..."
  npm install -g pnpm
fi

# 判断pm2是否已安装
if command -v pm2 >/dev/null 2>&1;
then
  echo "pm2 already installed"
else
  echo "pm2 installing..."
  npm install -g pm2@latest
fi

# 判断http-server是否已安装
if command -v http-server >/dev/null 2>&1;
then
  echo "http-server already installed"
else
  echo "http-server installing..."
  npm install -g http-server
fi

source_terminal
# 安装完成
echo "install completed."
