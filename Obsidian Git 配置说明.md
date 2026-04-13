# Obsidian Git 配置说明

## 1. 安装 Obsidian Git 插件

1. 打开 Obsidian → 设置 → 第三方插件
2. 关闭安全模式
3. 浏览社区插件 → 搜索 "Git"
4. 安装并启用

## 2. 配置 Git 仓库

在终端执行：

```bash
cd "/Users/tuntun/Documents/Obsidian Vault"
git init
git remote add origin https://github.com/web1286/inimf-obsidian-sync.git
```

## 3. Obsidian Git 插件设置

打开设置 → Obsidian Git：

| 设置项 | 值 |
|-------|-----|
| Vault backup interval (minutes) | 10 |
| Auto commit message | `vault backup: {{date}}` |
| Auto pull on startup | ✅ 启用 |
| Auto commit and push | ✅ 启用 |

## 4. 文章格式规范

在 `articles/` 目录下创建 `.md` 文件，使用 YAML frontmatter：

```markdown
---
title: "文章标题"
category: "行业研究"
tags: ["AI", "大模型"]
---

正文内容...

![本地图片](attachments/image.png)
![外链图片](https://example.com/image.jpg)
```

## 5. 图片存放

- 本地图片：放在 `attachments/` 目录
- Obsidian 粘贴图片时，会自动保存到 attachments

## 6. 同步流程

1. 在 Obsidian 写文章
2. 保存后，Obsidian Git 自动提交并推送到 GitHub
3. GitHub Webhook 触发 inimf.com API
4. 文章自动进入「库存信息」
5. 在 inimf.com 后台分发到各模块

## 7. 手动同步

如需立即同步，按 `Ctrl+P` → 输入 "Git: Commit all changes" → 然后 "Git: Push"

---

仓库地址：https://github.com/web1286/inimf-obsidian-sync
