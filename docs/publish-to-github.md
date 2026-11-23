# 上传 GitHub 操作流程（维护者指南）

> 面向仓库维护者：从本地一份 Skill 文件夹，到推送到 GitHub 并打版本标签的完整流程。命令以 git 为准，Windows / macOS / Linux 通用；PowerShell 中可直接执行。

## 目录

1. [前置条件](#1-前置条件)
2. [上传前：敏感信息复核](#2-上传前敏感信息复核)
3. [整理本地仓库目录](#3-整理本地仓库目录)
4. [本地初始化与首次提交](#4-本地初始化与首次提交)
5. [创建远程空仓库](#5-创建远程空仓库)
6. [关联远程并推送](#6-关联远程并推送)
7. [打版本标签](#7-打版本标签可选但建议)
8. [核对远端内容](#8-核对远端内容)
9. [日常迭代再推送](#9-日常迭代再推送)
10. [注意事项清单](#10-注意事项清单)

---

## 1. 前置条件

- 本机已安装 git（`git --version` 可输出版本号）。
- GitHub 账号已在本机完成登录授权（首次推送会弹出登录或走凭据管理器）。
- 已配置提交身份：

```bash
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"
```

> 注意：公开仓库中，每次提交的用户名和邮箱会随提交记录可见。不想暴露私人邮箱时，使用 GitHub 提供的 `noreply` 邮箱（Settings → Emails）。

## 2. 上传前：敏感信息复核

提交前先扫描待分享内容，确认不含以下信息：

- 公司 / 单位名称、项目编号、客户名、具体机型装备编号
- 报价、金额、业绩合同、证书编号、专利号
- 人名、电话、邮箱、住址等联系方式
- API token、密码、密钥、内网地址、本机绝对路径
- 含真实报价或资质的方案样例、缓存文件、临时文件

发现上述内容先脱敏或删除，再进入下一步。

## 3. 整理本地仓库目录

在本地建一个仓库根目录，结构如下（Skill 文件夹原样复制进来，内部结构不动）：

```
bid-technical-proposal-skill/
├── README.md                        # 仓库说明（给人看）
├── INSTALL.md                       # 同事安装一页纸
├── .gitignore                       # 排除无需入库的文件
└── bid-technical-proposal/          # Skill 本体
    ├── SKILL.md
    ├── references/
    └── assets/
```

`.gitignore` 至少排除：

```gitignore
*.zip
.DS_Store
Thumbs.db
__pycache__/
*.pyc
*.tmp
*.log
```

要点：

- 仓库根的 README / INSTALL 是给人看的；Skill 文件夹内部保持纯净，不再放说明文档。
- Skill 文件夹名必须与 `SKILL.md` 里的 `name` 字段一致。

## 4. 本地初始化与首次提交

进入仓库根目录后逐条执行：

```bash
# 初始化 git 仓库，默认分支设为 main
git init -b main

# 暂存全部文件
git add .

# 核对暂存清单：应只有计划入库的文件，无 zip、缓存、临时文件
git status --short

# 提交
git commit -m "v1.0.0: 技术标撰写与核查 Skill（工作流、红线、核查清单、模板）"

# 查看提交记录，确认提交成功
git log --oneline
```

## 5. 创建远程空仓库

在 GitHub 上新建仓库（网页操作或通过授权连接器）：

- 填写仓库名（英文小写连字符，如 `bid-technical-proposal-skill`）。
- **不要勾选** "Initialize with README / .gitignore / license"：本地已有这些文件，远端再初始化会造成首次推送冲突。
- 按决策选择 Public（公开）或 Private（私有）。
- 创建后记下仓库地址，格式为：

```
https://github.com/<owner>/<repo>.git
```

## 6. 关联远程并推送

```bash
# 关联远程仓库（若已有 origin，先 git remote remove origin）
git remote add origin https://github.com/<owner>/<repo>.git

# 推送 main 分支，并建立本地与远端的跟踪关系
git push -u origin main
```

首次推送按提示完成登录授权。推送成功后，`main` 分支出现在远端仓库。

## 7. 打版本标签（可选但建议）

给正式发布版本打标签，方便团队锁定版本：

```bash
# 附注标签
git tag -a v1.0.0 -m "v1.0.0: 首次发布"

# 推送标签到远端（分支不会自动带标签，需单独 push）
git push origin v1.0.0
```

## 8. 核对远端内容

推送后核对：

- 仓库根目录存在 `README.md`、`INSTALL.md`、`.gitignore` 和 Skill 文件夹。
- Skill 子目录内 `SKILL.md`、`references/`、`assets/` 齐全。
- 被 `.gitignore` 排除的压缩包、缓存没有出现在远端。
- 网页打开仓库，README 正常渲染。

## 9. 日常迭代再推送

后续修改本地文件后，重复：

```bash
git add .
git commit -m "本次修改说明"
git push
```

发新版本时打新标签，例如 `v1.0.1`：

```bash
git tag -a v1.0.1 -m "v1.0.1: 修改说明"
git push origin v1.0.1
```

## 10. 注意事项清单

- **脱敏优先**：补真实案例前，项目编号、客户/单位名、机型、报价、业绩、证书编号一律不得入库。
- **可见性复核**：公开仓库任何人可见；投标方法论、评审口径属于竞争性经验，公开前确认不违反单位保密规定。不放心就用私有仓库。
- **LICENSE**：未添加开源协议时，默认保留所有权利，他人可见但不能合法复制、修改、分发；需要开放复用再补协议（如 MIT）。
- **两份副本同步**：运行时实际加载的是 Agent 环境 `.user_skills/` 下的 Skill 副本，仓库是分享副本；改了一边要同步另一边，避免分叉。
- **凭据安全**：token、密码不写进任何文件；授权走登录流程，不落地到仓库。
- **文件夹名一致**：克隆后不要改 Skill 文件夹名，否则可能无法被识别。
- **历史提交**：已推送的提交记录无法靠修改本地配置消除作者信息；需要匿名化时要重写历史或重建仓库。
