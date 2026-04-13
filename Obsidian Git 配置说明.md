# Obsidian Git 配置说明

## ✅ 已完成配置

### 1. Git 仓库初始化
- Git 仓库已初始化
- 远程仓库已配置: `https://github.com/web1286/inimf-obsidian-sync.git`
- Git 用户信息已设置

### 2. 目录结构已创建
```
Obsidian Vault/
├── articles/          # 存放文章
├── attachments/       # 存放图片
└── .gitignore         # Git 忽略配置
```

### 3. Obsidian Git 插件配置
配置文件已创建: `.obsidian/plugins/obsidian-git/data.json`

**关键设置**:
- 自动备份间隔: 10 分钟
- 启动时自动拉取: ✅
- 自动提交推送: ✅
- 推送前拉取: ✅

### 4. 示例文章已创建
`articles/示例文章.md` - 用于测试同步功能

---

## 📋 待完成（需要 Obsidian 中操作）

### 1. 安装 Obsidian Git 插件
1. 打开 Obsidian
2. 设置 → 第三方插件
3. 关闭安全模式
4. 浏览社区插件 → 搜索 "Git"
5. 安装并启用

### 2. 首次推送 ✅ 已完成
首次推送已成功完成，本地与远程仓库已同步。

**Git 状态**: ✅ 已配置完成，可正常使用

---

## 📝 文章格式规范

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

### 支持的 YAML 字段
| 字段 | 说明 | 必填 |
|-----|------|------|
| title | 文章标题 | ✅ |
| category | 分类 | ❌ |
| tags | 标签数组 | ❌ |
| source_url | 原文链接 | ❌ |
| cover_image_url | 封面图 URL | ❌ |
| cover | 封面图 URL（别名） | ❌ |

---

## 🔄 同步流程

1. **在 Obsidian 写文章** → 保存到 `articles/` 目录
2. **自动提交** → Obsidian Git 每 10 分钟自动 commit
3. **自动推送** → 自动 push 到 GitHub
4. **Webhook 触发** → GitHub 通知 inimf.com API
5. **解析入库** → API 解析 Markdown，图片转存 R2
6. **进入库存** → 文章进入 inimf.com「库存信息」
7. **后台分发** → 在 inimf.com 分发到各模块

---

## 🖼️ 图片处理

| 类型 | 存放位置 | 同步后 |
|-----|---------|--------|
| 本地图片 | `attachments/` 目录 | 自动上传 R2，替换为 CDN 链接 |
| 外链图片 | 任意 URL | 自动下载转存 R2 |

---

## 🚀 手动同步

如需立即同步：
1. 按 `Ctrl+P`
2. 输入 "Git: Commit all changes"
3. 然后输入 "Git: Push"

---

## 📎 相关信息

- **GitHub 仓库**: https://github.com/web1286/inimf-obsidian-sync
- **Webhook URL**: `https://inimf.com/api/v1/obsidian/webhook`
- **API 状态**: 待部署（执行 `deploy-obsidian-api.sh`）

---

## ⚠️ 注意事项

1. **首次配置后重启 Obsidian**，确保插件加载配置
2. **检查网络连接**，确保能访问 GitHub
3. **图片大小建议** < 5MB，避免同步超时
4. **文章标题唯一**，相同标题会覆盖旧文章
