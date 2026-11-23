# 安装说明（一页纸）

**这是什么**：投标技术标辅助 Skill，用于拆解招标评分点/废标项、编写技术方案、编制偏离表、核查招标符合性。安装后在豆包/Agent 对话中直接使用，无需额外配置。

---

## 一、获取文件（二选一）

**方式 A：Git 克隆（已装 Git）**

```bash
git clone https://github.com/CKtpy/bid-technical-proposal-skill.git
```

**方式 B：下载压缩包**

在仓库页面点 **Code → Download ZIP**，解压到任意临时目录。

## 二、放入 Skill 目录

1. 打开本仓库的 `bid-technical-proposal` 文件夹（注意：是里面这一层，不是外层仓库目录）。
2. 把**整个 `bid-technical-proposal` 文件夹**复制到本机的 `.user_skills` 目录下。

目录位置（Windows 常见路径）：

```
C:\Users\<你的用户名>\AppData\Local\Doubao\User Data\Default\.doubao\agent_mode\workspace\.user_skills\
```

macOS / Linux 一般在用户目录下的 `~/.doubao/agent_mode/workspace/.user_skills/`，具体以本机实际目录为准。

找不到目录时，最稳妥的方法：在豆包对话里直接问"我的 .user_skills 目录在哪"，按返回的路径放入。

放入后结构应为：

```
.user_skills\
└── bid-technical-proposal\
    ├── SKILL.md
    ├── references\
    └── assets\
```

## 三、验证是否生效

1. **新开一个对话**（已打开的会话不会自动加载新 Skill）。
2. 输入类似："帮我拆一下这份招标文件的评分点和废标项"，或"按招标要求写技术方案"。
3. 若流程按条款分级、偏离表模板等方式展开，即安装成功。

## 四、日常使用

- 直接上传招标文件，说明要做的事：拆条款 / 写方案 / 做偏离表 / 核查符合性。
- 模板里的【】占位按本项目实际填写；没有凭据的资质、编号、业绩、报告，标"待补/待核"，不要编造。
- 技术标正文不含报价；报价、资质、业绩等由商务标另行处理。

## 五、常见问题

| 问题 | 处理 |
|------|------|
| 复制后没触发 | 确认是新开会话；确认文件夹名仍是 `bid-technical-proposal`，未被改名 |
| 目录结构乱了 | 必须保留 `references`、`assets` 子文件夹，不要把文件散到外面 |
| 已有同名旧版本 | 先备份旧文件夹，再覆盖 |
| 想升级 | 重新下载/克隆后，用新的 `bid-technical-proposal` 文件夹覆盖即可 |

## 六、注意事项

- 本 Skill 只提供通用方法论和空白模板，不含任何真实项目数据；补充真实案例前请先脱敏（项目编号、客户名、机型、报价、业绩、证书编号不得入库）。
- 安装过程中如遇目录权限或加载问题，联系仓库维护人。
