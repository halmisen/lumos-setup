# 📦 软件需求清单

## 🖥️ 系统要求
- **操作系统**: Windows 11 with WSL2
- **WSL发行版**: Ubuntu 24.04.3 LTS (Noble Numbat)
- **权限**: sudo 管理员权限
- **网络**: 互联网连接（用于下载软件包）

## 🛠️ 核心开发工具

### Python 开发环境
```yaml
python3: 3.12.3
pip3: 24.0
python3-dev: 3.12.3-0ubuntu2
python3-wheel: 0.42.0-2
```

### JavaScript 开发环境  
```yaml
nodejs: 18.19.1+dfsg-6ubuntu5
npm: 9.2.0
libnode109: 18.19.1+dfsg-6ubuntu5
```

### 编译工具链
```yaml
build-essential: 12.10ubuntu1
gcc: 4:13.2.0-7ubuntu1
gcc-13: 13.3.0-6ubuntu2~24.04
g++: 4:13.2.0-7ubuntu1
make: 4.3-4.1build2
```

### 版本控制
```yaml
git: 2.43.0
gh: 2.45.0-1ubuntu0.3  # GitHub CLI
```

## 📚 依赖库详情

### Python 构建依赖
- `libpython3.12-dev` - Python开发头文件
- `libexpat1-dev` - XML解析库开发文件
- `zlib1g-dev` - 压缩库开发文件
- `libssl-dev` - SSL/TLS库开发文件

### Node.js 运行时依赖
- `libcares2` - C-Ares DNS解析库
- `libuv1t64` - 跨平台异步I/O库  
- `libnode109` - Node.js核心库

### 编译器工具链
- `cpp` - C预处理器
- `libc6-dev` - C标准库开发文件
- `linux-libc-dev` - Linux内核头文件

## ⚙️ 配置文件

### NPM 配置 (`~/.npmrc`)
```ini
registry=https://registry.npmmirror.com/
```

### PIP 配置 (`~/.config/pip/pip.conf`)  
```ini
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
```

### Git 配置 (`~/.gitconfig`)
```ini
[user]
    name = fiver
    email = fiver@example.com
```

### Shell 配置 (`~/.bashrc` 新增部分)
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

## 📁 目录结构
```
/home/fiver/
├── .bashrc                 # Shell配置文件
├── .config/pip/pip.conf   # PIP配置文件
├── .npmrc                 # NPM配置文件
├── .gitconfig            # Git配置文件
├── projects/             # 项目目录
│   ├── python/           # Python项目
│   ├── nodejs/           # Node.js项目
│   └── web/              # 前端项目
├── tools/                # 开发工具
└── learning/            # 学习材料
```

## 🚀 安装命令摘要

```bash
# 系统更新
sudo apt update

# 核心开发工具
sudo apt install -y python3-pip nodejs npm gh

# 配置镜像源
npm config set registry https://registry.npmmirror.com
pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

# 配置Git
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"

# 创建目录结构  
mkdir -p ~/projects/{python,nodejs,web} ~/tools ~/learning
```

## 📊 磁盘使用情况

安装完成后预计占用空间：
- **Python环境**: ~150MB
- **Node.js环境**: ~70MB  
- **编译工具链**: ~280MB
- **GitHub CLI**: ~45MB
- **总计**: ~545MB

## 🔧 可选扩展工具

```bash
# 文本编辑器
sudo apt install -y vim nano

# 系统监控
sudo apt install -y htop tree

# 网络工具 (已包含)
curl wget

# 压缩工具
sudo apt install -y unzip zip
```

---

*本清单基于 Ubuntu 24.04.3 LTS 实际安装结果* 📋