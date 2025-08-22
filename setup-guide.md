# 🛠️ WSL Ubuntu 开发环境完整安装指南

> 基于我们今天的实际操作经验 - 从零开始设置完美的开发环境

## 📋 安装步骤清单

### ✅ 第1步：更新系统包管理器
```bash
sudo apt update
```
**说明**：更新软件包列表，确保能安装最新版本的软件

### ✅ 第2步：安装 Python 包管理器
```bash
sudo apt install -y python3-pip
```
**包含内容**：
- pip3 (Python包管理器)  
- build-essential (编译工具链)
- python3-dev (Python开发头文件)

**验证**：
```bash
python3 --version  # 应显示 Python 3.12.3
pip3 --version     # 应显示 pip 24.0
```

### ✅ 第3步：安装 Node.js 和 npm
```bash
sudo apt install -y nodejs npm
```
**验证**：
```bash
node --version  # 应显示 v18.19.1
npm --version   # 应显示 9.2.0
```

### ✅ 第4步：配置 Shell 环境 
编辑 `~/.bashrc` 文件，添加以下内容：

```bash
# Development Environment Settings
export NODE_ENV=development
export PATH="$HOME/.local/bin:$PATH"

# Better prompt
PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# Useful aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias grep='grep --color=auto'
alias pip='pip3'
alias proj='cd ~/projects'

# Auto navigate to projects
cd ~/projects
```

### ✅ 第5步：配置包镜像源
```bash
# 设置 npm 淘宝镜像
npm config set registry https://registry.npmmirror.com

# 设置 pip 清华镜像  
pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```

### ✅ 第6步：创建项目目录结构
```bash
cd ~
mkdir -p projects/{python,nodejs,web} tools learning
```

### ✅ 第7步：安装 GitHub CLI
```bash
sudo apt install -y gh
```

### ✅ 第8步：配置 Git 用户信息
```bash
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱@example.com"
```

### ✅ 第9步：登录 GitHub CLI
```bash
gh auth login
# 按提示操作完成GitHub账号绑定
```

## 🎯 验证安装完成

运行以下命令确认所有工具正常：

```bash
# 检查版本
python3 --version && pip3 --version
node --version && npm --version  
gcc --version | head -1
gh --version

# 测试运行
python3 -c "print('Python works!')"
node -e "console.log('Node.js works!')"

# 检查镜像源
npm config get registry
pip3 config get global.index-url
```

## 🚀 日常使用流程

### 创建新项目
```bash
# Python项目
cd ~/projects/python
mkdir my-project && cd my-project
echo "print('Hello World')" > main.py
git init && git add . && git commit -m "Initial commit"
gh repo create my-project --public --source=. --push

# Node.js项目  
cd ~/projects/nodejs
mkdir my-app && cd my-app
npm init -y
echo "console.log('Hello Node!');" > index.js
git init && git add . && git commit -m "Initial commit"  
gh repo create my-app --public --source=. --push
```

### 日常开发流程
```bash
# 1. 编写代码
vim main.py  # 或使用你喜欢的编辑器

# 2. 提交更改
git add .
git commit -m "描述你的更改"

# 3. 推送到GitHub
git push
```

## ⚠️ 常见问题解决

### 问题1：sudo需要密码
**解决**：在命令前添加密码
```bash
echo "你的密码" | sudo -S 命令
```

### 问题2：npm安装慢
**解决**：确认镜像源已设置
```bash
npm config get registry  # 应显示淘宝镜像
```

### 问题3：pip安装失败
**解决**：检查镜像源配置
```bash
pip3 config get global.index-url  # 应显示清华镜像
```

## 🎉 完成标志

当你看到以下输出时，说明环境配置成功：

```
✅ Python 3.12.3
✅ pip 24.0 from /usr/lib/python3/dist-packages/pip (python 3.12)  
✅ v18.19.1
✅ 9.2.0
✅ gcc (Ubuntu 13.3.0-6ubuntu2~24.04) 13.3.0
✅ gh version 2.45.0
```

---

*记录于 2025年8月22日 - 首次完美安装体验* 🌟