# 🤖 Claude Code 配置指南

## 📖 关于本文件

这个 `CLAUDE.md` 文件包含了使用 Claude Code 进行开发时的最佳实践和配置建议。基于我们今天的实际搭建经验总结。

## 🛠️ 环境检查命令

当你使用 Claude Code 时，可以运行这些命令来快速检查环境状态：

```bash
# 检查系统信息
uname -a
cat /etc/os-release | grep PRETTY_NAME

# 检查开发工具版本
python3 --version && pip3 --version
node --version && npm --version
gcc --version | head -1
git --version
gh --version

# 检查镜像源配置
npm config get registry
pip3 config get global.index-url

# 检查目录结构
ls -la ~/projects/
pwd
```

## ⚙️ Claude Code 推荐设置

### 默认工作目录
```bash
# 设置 Claude Code 默认从项目目录开始
cd ~/projects
```

### 常用开发命令
```bash
# Python项目快速启动
alias pystart="cd ~/projects/python && python3"
alias pipi="pip3 install"

# Node.js项目快速启动  
alias nodestart="cd ~/projects/nodejs && node"
alias npmi="npm install"

# Git操作简化
alias gits="git status"
alias gita="git add ."
alias gitc="git commit -m"
alias gitp="git push"

# 项目创建模板
alias newpy="mkdir -p ~/projects/python/\$1 && cd ~/projects/python/\$1 && git init"
alias newnode="mkdir -p ~/projects/nodejs/\$1 && cd ~/projects/nodejs/\$1 && npm init -y && git init"
```

## 📝 建议的项目结构模板

### Python项目模板
```
my-python-project/
├── README.md
├── requirements.txt    # pip freeze > requirements.txt
├── main.py
├── src/
│   └── __init__.py
├── tests/
│   └── test_main.py
└── .gitignore
```

### Node.js项目模板  
```
my-node-project/
├── README.md
├── package.json
├── index.js
├── src/
│   └── app.js
├── tests/
│   └── app.test.js
└── .gitignore
```

## 🔧 Claude Code 开发流程

### 1. 新项目创建流程
```bash
# 1. 创建项目目录
cd ~/projects/python  # 或 nodejs/web
mkdir my-new-project && cd my-new-project

# 2. 初始化项目
git init
echo "# My New Project" > README.md

# 3. 根据项目类型创建文件
# Python项目:
echo "print('Hello World')" > main.py
echo "requests" > requirements.txt

# Node.js项目:
npm init -y
echo "console.log('Hello World');" > index.js

# 4. 首次提交
git add .
git commit -m "🎉 Initial commit"

# 5. 创建GitHub仓库
gh repo create my-new-project --public --source=. --push
```

### 2. 日常开发流程
```bash
# 1. 检查状态
git status

# 2. 添加更改
git add .

# 3. 提交更改  
git commit -m "✨ Add new feature: 功能描述"

# 4. 推送到GitHub
git push
```

## 🐛 常见问题及解决方案

### 问题1: 权限问题
```bash
# 如果遇到权限问题，检查文件所有权
ls -la
# 如果需要，修复权限
sudo chown -R $USER:$USER ~/projects/
```

### 问题2: Git配置问题
```bash
# 检查Git配置
git config --list | grep user

# 重新配置用户信息
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"
```

### 问题3: Python包安装失败
```bash
# 检查pip镜像源
pip3 config get global.index-url

# 如果镜像源有问题，重新设置
pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple

# 升级pip本身
python3 -m pip install --upgrade pip
```

### 问题4: Node.js包安装慢
```bash
# 检查npm镜像源
npm config get registry

# 重新设置淘宝镜像
npm config set registry https://registry.npmmirror.com

# 清除npm缓存
npm cache clean --force
```

## 🎯 Claude Code 使用技巧

### 1. 代码审查模式
当让Claude审查代码时，先运行：
```bash
# 显示项目结构
tree . 2>/dev/null || find . -type f -name "*.py" -o -name "*.js" -o -name "*.json" | head -20

# 显示关键文件内容
cat README.md requirements.txt package.json 2>/dev/null
```

### 2. 调试信息收集
遇到问题时，提供这些信息给Claude：
```bash
# 系统信息
uname -a
python3 --version
node --version

# 错误上下文
pwd
ls -la
git status

# 最近的操作历史
history | tail -10
```

### 3. 性能检查
```bash
# 检查磁盘使用
df -h ~/projects/

# 检查内存使用  
free -h

# 检查进程
ps aux | grep -E "(python|node)" | head -5
```

## 📊 环境验证清单

使用以下清单确保环境配置正确：

- [ ] Python 3.12.3 已安装
- [ ] pip3 24.0 已安装并配置镜像源
- [ ] Node.js v18.19.1 已安装  
- [ ] npm 9.2.0 已安装并配置镜像源
- [ ] GCC 13.3.0 编译器已安装
- [ ] Git 2.43.0 已安装并配置用户信息
- [ ] GitHub CLI 2.45.0 已安装并登录
- [ ] 项目目录结构已创建
- [ ] Shell别名和环境变量已配置
- [ ] 可以成功创建和推送Git仓库

## 🔮 未来扩展建议

### 可能需要的额外工具
```bash
# Docker (容器化开发)
sudo apt install -y docker.io

# 数据库工具
sudo apt install -y sqlite3 postgresql-client

# 监控工具
sudo apt install -y htop tree neofetch

# 编辑器 (如果不使用Claude Code内置编辑器)
sudo apt install -y vim code
```

---

*配置文件版本：v1.0 | 更新日期：2025年8月22日*
*基于 Lumos Setup 项目的实际配置经验* ✨