# 📁 项目结构说明

## 🏗️ 目录结构

```
APOHF/
├── Induction/                          # 核心代码目录
│   ├── automatic_prompt_engineer/      # 自动提示词工程模块
│   │   ├── __init__.py
│   │   ├── config.py                   # 配置管理
│   │   ├── llm.py                      # 大语言模型接口
│   │   ├── evaluate.py                 # 评估模块
│   │   └── template.py                 # 模板管理
│   │
│   ├── experiments/                    # 实验相关代码
│   │   ├── run_dbandits_po.py         # 主要运行脚本
│   │   ├── LlamaForMLPRegression.py   # 算法实现
│   │   ├── configs/                    # 配置文件
│   │   ├── data/                       # 数据处理
│   │   └── evaluation/                 # 评估脚本
│   │
│   ├── environment.yml                 # Conda 环境配置
│   └── key                            # API 密钥文件（不提交）
│
├── docs/                              # 文档目录
│   ├── API.md                         # API 文档
│   ├── TUTORIAL.md                    # 使用教程
│   └── EXAMPLES.md                    # 示例代码
│
├── tests/                             # 测试目录
│   ├── test_algorithms.py             # 算法测试
│   ├── test_api.py                    # API 测试
│   └── test_utils.py                  # 工具函数测试
│
├── scripts/                           # 工具脚本
│   ├── setup.py                       # 环境设置脚本
│   ├── run_experiments.py             # 批量实验脚本
│   └── data_preprocessing.py          # 数据预处理
│
├── .gitignore                         # Git 忽略文件
├── .github/                           # GitHub 配置
│   ├── workflows/                     # CI/CD 工作流
│   └── ISSUE_TEMPLATE/                # Issue 模板
│
├── COLLABORATION_GUIDE.md             # 协作指南
├── PROJECT_STRUCTURE.md               # 项目结构说明
├── README.md                          # 项目说明
└── requirements.txt                   # Python 依赖
```

## 👥 分工建议

### 🔵 开发者 A - 算法核心
**负责目录:**
- `Induction/experiments/LlamaForMLPRegression.py`
- `Induction/experiments/run_dbandits_po.py`
- `tests/test_algorithms.py`

**主要职责:**
- DisLinUCB 算法优化
- 新算法实现
- 性能调优
- 算法测试

### 🟢 开发者 B - API 和接口
**负责目录:**
- `Induction/automatic_prompt_engineer/llm.py`
- `Induction/automatic_prompt_engineer/config.py`
- `tests/test_api.py`

**主要职责:**
- LLM 接口优化
- API 集成
- 配置管理
- 接口测试

### 🟡 共同维护
**共同负责:**
- `Induction/experiments/data/` - 数据处理
- `docs/` - 文档维护
- `scripts/` - 工具脚本
- `README.md` - 项目文档

## 🚦 开发规则

### 文件修改权限
1. **核心算法文件**: 需要 PR 审查
2. **配置文件**: 需要讨论后修改
3. **文档文件**: 可以直接修改
4. **测试文件**: 对应模块负责人维护

### 分支命名规范
```
feature/开发者名-功能描述
├── feature/alice-dislinucb-optimization
├── feature/bob-api-integration
├── feature/alice-new-algorithm
└── feature/bob-config-management
```

### 提交规范
```
类型(范围): 简短描述

详细描述

示例:
feat(algorithm): 优化 DisLinUCB 算法性能
fix(api): 修复 OpenRouter 连接问题
docs(readme): 更新安装说明
test(algorithm): 添加算法单元测试
```

## 🔄 工作流程

### 1. 功能开发流程
```bash
# 1. 创建功能分支
git checkout develop
git pull origin develop
git checkout -b feature/你的名字-功能描述

# 2. 开发功能
# 编写代码...

# 3. 提交代码
git add .
git commit -m "feat(scope): 功能描述"
git push origin feature/你的名字-功能描述

# 4. 创建 Pull Request
# 在 GitHub 上创建 PR 到 develop 分支

# 5. 代码审查和合并
# 审查通过后合并到 develop
```

### 2. 冲突解决流程
```bash
# 如果有冲突，先同步最新代码
git checkout develop
git pull origin develop
git checkout feature/你的分支
git merge develop

# 解决冲突后提交
git add .
git commit -m "resolve: 解决合并冲突"
git push origin feature/你的分支
```

## 📋 任务管理

### GitHub Issues 使用
- **Bug 报告**: 使用 `bug` 标签
- **功能请求**: 使用 `enhancement` 标签
- **文档**: 使用 `documentation` 标签
- **问题讨论**: 使用 `question` 标签

### 项目看板
- **To Do**: 待开发任务
- **In Progress**: 开发中任务
- **Review**: 代码审查中
- **Done**: 已完成任务

## 🧪 测试策略

### 测试分类
1. **单元测试**: 测试单个函数/类
2. **集成测试**: 测试模块间交互
3. **端到端测试**: 测试完整流程
4. **性能测试**: 测试算法性能

### 测试要求
- 新功能必须有对应测试
- 测试覆盖率不低于 80%
- 所有测试必须通过才能合并

## 📚 文档维护

### 文档类型
1. **API 文档**: 自动生成 + 手动维护
2. **用户指南**: 使用教程和示例
3. **开发文档**: 架构设计和开发指南
4. **更新日志**: 版本更新记录

### 文档更新规则
- 新功能必须更新相关文档
- API 变更必须更新 API 文档
- 重要更改需要更新 README

## 🔧 开发环境

### 推荐工具
- **IDE**: VS Code / PyCharm
- **Git GUI**: GitHub Desktop / SourceTree
- **Python**: 3.8+
- **包管理**: conda / pip

### 环境设置
```bash
# 克隆仓库
git clone https://github.com/lpc206/APOHF.git
cd APOHF

# 创建虚拟环境
conda env create -f Induction/environment.yml
conda activate APOHF

# 安装开发依赖
pip install -r requirements-dev.txt
```

---

这个结构设计确保了：
1. **清晰的职责分工**
2. **最小化文件冲突**
3. **高效的协作流程**
4. **良好的代码质量**
