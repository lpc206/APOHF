# 🤝 多人协作开发指南

## 📋 项目概述
这是一个独立的 APOHF (Prompt Optimization with Human Feedback) 项目，支持多人协作开发。

## 🌳 分支策略

### 主要分支
- **`main`**: 生产分支，始终保持稳定可发布状态
- **`develop`**: 开发分支，集成所有新功能

### 功能分支
- **`feature/功能名`**: 新功能开发
- **`bugfix/问题描述`**: Bug 修复
- **`hotfix/紧急修复`**: 生产环境紧急修复

## 👥 协作工作流

### 1. 初始设置（每个开发者只需做一次）

```bash
# 克隆仓库
git clone https://github.com/lpc206/APOHF.git
cd APOHF

# 设置用户信息
git config user.name "你的姓名"
git config user.email "你的邮箱"

# 切换到开发分支
git checkout develop
```

### 2. 开发新功能

```bash
# 从 develop 分支创建功能分支
git checkout develop
git pull origin develop
git checkout -b feature/你的功能名

# 开发代码...
# 提交更改
git add .
git commit -m "feat: 添加新功能描述"

# 推送功能分支
git push origin feature/你的功能名
```

### 3. 合并功能（通过 Pull Request）

1. 在 GitHub 上创建 Pull Request
2. 从 `feature/你的功能名` 到 `develop`
3. 请求代码审查
4. 审查通过后合并

### 4. 发布到生产环境

```bash
# 从 develop 合并到 main
git checkout main
git pull origin main
git merge develop
git push origin main

# 创建版本标签
git tag -a v1.0.0 -m "Release version 1.0.0"
git push origin v1.0.0
```

## 🚫 避免冲突的规则

### 1. 分支命名规范
- `feature/用户名-功能描述` (如: `feature/alice-api-optimization`)
- `bugfix/用户名-问题描述` (如: `bugfix/bob-memory-leak`)
- `hotfix/紧急问题描述` (如: `hotfix/security-patch`)

### 2. 提交信息规范
```
类型: 简短描述

详细描述（可选）

类型包括:
- feat: 新功能
- fix: Bug 修复
- docs: 文档更新
- style: 代码格式调整
- refactor: 代码重构
- test: 测试相关
- chore: 构建过程或辅助工具的变动
```

### 3. 文件分工建议
```
项目结构分工示例:
├── Induction/
│   ├── experiments/          # 用户A负责
│   ├── automatic_prompt_engineer/  # 用户B负责
│   └── data/                 # 共同维护
├── docs/                     # 文档维护者
├── tests/                    # 测试负责人
└── scripts/                  # 工具脚本
```

## 🔄 日常协作流程

### 每日开始工作前
```bash
# 切换到 develop 分支
git checkout develop

# 拉取最新代码
git pull origin develop

# 创建或切换到你的功能分支
git checkout feature/你的功能名
# 或创建新分支
git checkout -b feature/新功能名

# 将 develop 的最新更改合并到你的分支
git merge develop
```

### 提交代码前
```bash
# 检查状态
git status

# 添加文件
git add .

# 提交（使用规范的提交信息）
git commit -m "feat: 添加用户认证功能"

# 推送到远程
git push origin feature/你的功能名
```

### 完成功能后
1. 推送分支到 GitHub
2. 创建 Pull Request 到 `develop` 分支
3. 请求代码审查
4. 解决审查意见
5. 合并后删除功能分支

## 🛠️ 实用命令

### 查看分支
```bash
# 查看所有分支
git branch -a

# 查看远程分支
git branch -r
```

### 同步代码
```bash
# 拉取所有分支的最新代码
git fetch origin

# 查看分支差异
git diff develop origin/develop
```

### 解决冲突
```bash
# 如果合并时有冲突
git merge develop
# 手动解决冲突后
git add .
git commit -m "resolve: 解决合并冲突"
```

### 撤销操作
```bash
# 撤销最后一次提交（保留更改）
git reset --soft HEAD~1

# 撤销工作区更改
git restore .

# 撤销已添加的文件
git restore --staged .
```

## 📝 代码审查清单

### 提交前自检
- [ ] 代码能正常运行
- [ ] 添加了必要的注释
- [ ] 遵循项目代码风格
- [ ] 没有调试代码残留
- [ ] 提交信息清晰明确

### 审查他人代码
- [ ] 逻辑是否正确
- [ ] 是否有潜在的 Bug
- [ ] 代码可读性如何
- [ ] 是否符合项目规范
- [ ] 性能是否有问题

## 🚨 紧急情况处理

### 生产环境 Bug
```bash
# 从 main 分支创建 hotfix
git checkout main
git checkout -b hotfix/紧急问题描述

# 修复问题
# ...

# 提交修复
git commit -m "hotfix: 修复生产环境问题"

# 合并到 main 和 develop
git checkout main
git merge hotfix/紧急问题描述
git push origin main

git checkout develop
git merge hotfix/紧急问题描述
git push origin develop

# 删除 hotfix 分支
git branch -d hotfix/紧急问题描述
```

## 📞 协作沟通

### 建议的沟通方式
1. **GitHub Issues**: 讨论功能需求和 Bug 报告
2. **Pull Request**: 代码审查和讨论
3. **项目看板**: 跟踪任务进度
4. **定期会议**: 同步进度和解决问题

### 冲突解决原则
1. **沟通优先**: 遇到问题先沟通
2. **代码审查**: 重要更改必须经过审查
3. **测试验证**: 确保更改不破坏现有功能
4. **文档更新**: 重要更改要更新文档

---

## 🎯 快速开始

新加入的开发者可以按以下步骤快速开始：

1. 克隆仓库并设置环境
2. 阅读项目文档
3. 创建自己的功能分支
4. 提交第一个 Pull Request
5. 参与代码审查

记住：**沟通是协作的关键！** 有问题随时讨论。
