# bid-technical-proposal-skill

面向政企 / 装备采购投标**技术标**的 Agent Skill：招标条款拆解、技术方案撰写、技术偏离表编制与招标符合性核查。

## 适用场景

- 拆解招标文件评分点 / 废标项，并按 ★ / ▲ / 一般条款分级
- 生成带风险标注的技术标目录
- 编写技术方案正文
- 编制技术指标参数响应偏离表
- 核对偏离表与正文一致性、终审招标符合性

> 范围：仅技术标。报价、资格资质、业绩专利、体系证书等商务标内容只做缺项核对与风险提醒，不代拟。

## 目录结构

```
bid-technical-proposal/
├── SKILL.md                          # Skill 入口：触发描述、工作流导航、红线速览
├── references/
│   ├── workflow.md                   # 六步工作流
│   ├── redlines.md                   # 红线与高频雷区
│   ├── review-checklist.md            # 审核五准则与终审清单
│   └── domain-notes.md               # 装备品类、配套技术、章节要素
└── assets/
    ├── technical-proposal-outline.md  # 技术方案目录骨架模板
    ├── deviation-table-template.md   # 技术偏离表模板
    └── score-risk-matrix-template.md  # 评分点-风险对照表模板
```

## 安装

详细步骤见 [INSTALL.md](INSTALL.md)（同事一页纸安装说明）：

1. 克隆或下载本仓库。
2. 将 `bid-technical-proposal/` 整个文件夹复制到所用 Agent 环境的 `workspace/.user_skills/` 目录下。
3. 新开会话后自动加载；说出"写技术方案 / 做偏离表 / 核查符合性"等即可触发。

## 文档

- [INSTALL.md](INSTALL.md)：面向使用者的安装步骤、验证方法与常见问题。
- [docs/publish-to-github.md](docs/publish-to-github.md)：面向维护者的上传 GitHub 全流程、命令说明与注意事项。

## 使用与脱敏说明

- 模板中的【】占位需按具体项目填写；无凭据的资质、编号、业绩、报告一律标"待补/待核"，不要虚构。
- 向本仓库补充真实案例前，请先脱敏：项目编号、客户/单位名、具体机型、报价、业绩、证书编号不得入库。
- 本仓库内容为通用投标方法论与空白模板，不含任何真实项目数据。

## 版本

- v1.0.0：首次发布，技术标撰写与核查工作流、红线规则、核查清单与三套模板。
