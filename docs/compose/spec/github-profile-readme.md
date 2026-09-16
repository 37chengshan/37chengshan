---
feature: github-profile-readme
status: delivered
updated: 2026-09-16
branch: feat/profile-readme
commits: (orphan-initial)..(pending-final)
---

# GitHub Profile README（37chengshan）

## Report

**What was built** — 交付 `37chengshan` GitHub Profile README 全套：15 模块复刻 Prorise 骨架（渐变头图 / typing SVG / 社交徽章 / 双计数器 / 关于我三折叠 / skillicons / summary cards / trophy / 精选项目 / 贪吃蛇+profile-details / 名言收尾），叠加澄闪电紫主题、学生·深度 AI 开发者·Agent 编排人设，以及 `assets/goldenglow.jpg` 主视觉。配套 `.github/workflows/snake.yml`（Platane/snk → `output` 分支）与本规格。

**Verification** — 模块对照 15/15 PASS；用户名一致 19 处 PASS；HTML 标签平衡 PASS；YAML 解析 PASS；独立审查 critical=0。外链 HTTP 抽查因本机代理 `127.0.0.1:7890` 不可达标记 PRE-EXISTING（环境问题，非代码问题）。

**Journey log**
- Profile README 只能靠外链图服务 + 受限 HTML，真 3D/JS/WebGL 不可行；3D 需外挂站点
- 澄闪图已从 Downloads 拷入 `assets/goldenglow.jpg` 并相对路径引用
- `gh` token 失效 + 代理断，无法本地 push；交付为可推送文件包
- Platane/snk + ghaction-github-pages 的 `build_dir: dist` + `target_branch: output` 会把 SVG 落在 output 根，与 raw URL 对齐
- 社交徽章仍是占位链接（B站/掘金/知乎/LeetCode/Email），需用户填真实 ID

## [S1] Problem

用户希望在 GitHub 个人主页 `github.com/37chengshan` 展示一份与 `Prorise-cool` 同级、信息密度高且有个人辨识度的 Profile README。当前工作区为空，没有任何仓库内容或部署配置。需要交付可直接作为 `37chengshan/37chengshan` 仓库主分支内容的完整文件，并预留后续替换头图/角色图的扩展点。

## [S2] Design

### 定位

- 用户：学生 · 深度 AI 开发者
- 人设：在 AI 辅助下跨平台全栈交付（Web / App / 各类技术栈），并能自主研发 Skills 与 Agent 编排
- 兴趣：AGI · 机器人 · 明日方舟（澄闪 Goldenglow）
- 视觉：1:1 复刻 Prorise 模块骨架 + 个人创新（澄闪电紫主题色、Agent/Skills 专区、学生身份标识）

### 澄闪资产

- 源文件：用户提供的澄闪 Q 版图
- 仓库路径：`assets/goldenglow.jpg`（976×612 JPEG）
- 引用方式：README 相对路径 `assets/goldenglow.jpg`（Profile README 同仓相对路径可渲染）
- 用途：精选项目区左侧主视觉；未替换其他占位图前保持此文件

### 模块顺序（与 Prorise 对齐）

1. 顶部渐变细条（capsule-render soft gradient）
2. 挥动 Header（capsule-render waving）：用户名大字 + 中文座右铭
3. Hello 标题 + readme-typing-svg 轮播标语
4. 社交徽章行（shields.io for-the-badge）
5. 访问计数器 / followers / stars 三枚徽章
6. 渐变分隔线
7. 🌟 关于我：一句定位 + 三组 `<details>` 折叠技能（后端 / 前端跨端 / AI-Agent 与工程化）
8. 技能与工具：skillicons.dev 多行图标 + AI 工具流一行
9. 渐变分隔线
10. 社区贡献：github-profile-summary-cards（stats / repos-per-language / most-commit-language）
11. GitHub Trophy
12. 精选项目：两张卡片图位 + 「更多项目」徽章（先占位，用户可后换图床）
13. GitHub 活动：贪吃蛇 contribution grid（picture 深浅色切换）+ profile-details 卡片
14. 编程名言 typing-svg
15. 收尾感谢 + 斜体寄语 + 博客/个人入口位

### 个人创新点（相对 Prorise）

- **澄闪电紫主题**：waving header 使用 `#0b0b12 → #2a1040 → #6b2d8b → #c44dff → #e0aaff` 电紫渐变；typing / 名言 / 分隔线同色系
- **Agent & Skills 专区**：在「关于我」第三组折叠中突出 Claude Code Skills / Multi-Agent 编排 / Prompt 工程，而不是泛泛 DevOps
- **学生身份**：关于我首句写明「学生 · 深度 AI 开发者」，避免虚假全栈资深话术
- **澄闪视觉位**：精选项目区预留一张 Arknights 澄闪主题入口图（用户稍后提供照片；未提供前用 capsule-render 渐变占位 + TODO 注释）
- **双计数器**：保留 komarev + getloli（与 Prorise 一致），文案改为个人品牌

### 契约

| 项 | 值 |
|----|----|
| GitHub 用户名 | `37chengshan` |
| Profile 仓库 | `37chengshan/37chengshan` |
| 贪吃蛇输出 | `output` 分支 `github-contribution-grid-snake.svg` |
| 统计主题 | `radical`（与参考一致；可后续换） |
| Header 动画 | `fadeIn` |
| typing 字体 | `Fira Code` |

### 错误与边界

- 第三方服务（capsule-render / shields / skillicons / vercel cards / trophy / komarev / getloli / readme-typing-svg）均外链；README 中不内嵌失效兜底图，但结构上每块独立，单点挂掉不影响其他模块
- 用户名变更时只需全局替换 `37chengshan`
- 澄闪图已交付至 `assets/goldenglow.jpg` 并由 README 相对路径引用；换图时替换该文件即可
- 本机 `gh` token 失效且代理不可用，交付后需用户自行 push；Action 配置按 GitHub 官方语法写好，push 后自动跑

### 测试边界

- 本地无法完整渲染 GitHub README 外链图；验证方式：语法/链接格式检查、关键 URL 可达性抽查、文件结构与模块齐全性对照清单
- 不验证第三方服务长期可用性

## [S3] Out of Scope

- 不创建真实 GitHub 仓库、不 push、不改用户 GitHub 资料字段
- 不实现自定义域名博客站 / 真 3D 交互站（Profile README 无 JS/WebGL；3D 需外挂站点）
- 不修改本机 gh 登录态

## Tasks

- [x] T1: 初始化 git 工作区与 feature 分支 — acceptance: `.worktrees/profile-readme` 存在且在 `feat/profile-readme`（covers: S1）
- [x] T2: 编写本规格文档 — acceptance: 本文件存在于 worktree 且模块清单完整（covers: S1, S2）
- [x] T3: 实现 README.md — acceptance: worktree 根目录 `README.md` 覆盖 S2 全部 15 个模块，用户名全为 `37chengshan`（covers: S2）
- [x] T4: 配置贪吃蛇 Action — acceptance: `.github/workflows/snake.yml` 存在，生成 `output` 分支 SVG，与 README picture 标签路径一致（covers: S2）
- [x] T5: 校验与交付 — acceptance: 模块对照通过；关键外链 URL 形态正确；向用户说明 push 与换图步骤（covers: S2, S3）
