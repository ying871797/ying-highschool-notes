# AGENTS.md

个人高中知识库：纯静态笔记仓库，通过 GitHub Pages 供远程查看。
流程与个人偏好（方案审批、分支流程、语言约定）见全局
`~/.config/opencode/AGENTS.md`，本文件只补充仓库特有事实。

## 仓库事实

- **无构建、无依赖、无测试命令**——没有 package.json，也没有 lint/test。
  任何「验证」= 在浏览器中打开该 HTML 确认渲染正常。
- 内容 = 根目录下的自包含单文件笔记。每篇内联全部 CSS/JS，**不引用
  任何外部资源（CDN/字体/图片外链）**；新笔记保持这一点，否则离线或
  Pages 环境下样式丢失。
- 分支是 **master**（不是 main）。**GitHub Pages 从 master 根目录发布，
  仓库内容即站点内容**——不进仓库的文件线上看不到。
- 中文文件名在 git 输出中默认显示为八进制转义（`\345\214\226…`）。
  `git config core.quotepath false` 后可读；从 git status/log 输出
  识别文件名时先考虑这一层转义。
- 仓库完全公开：方案文档目录 `.proposals/` 已在 .gitignore 中排除，
  不会随仓库泄露；新增敏感内容前先想这一点。

## 新增笔记

- 命名沿用现有风格：中文「主题+文体」，如 `化学工艺流程笔记.html`、
  `思辨性训练笔记-系统版.html`。
- **新增笔记必须登记到 `index.html` 导航页**（入口链接 + 标题 + 一句简介），
  否则远程访问时发现不了。
- Markdown 笔记可入库，但 **Pages 会原样吐出 .md 源码**（无 Jekyll front
  matter 时按静态文件复制），不适合直接阅读——要展示的笔记产出 HTML 版。
- 提交前在浏览器打开目检：渲染正常、无外链资源。

## 发布

- push 到 master 即发布（Pages 源 = master / root），无部署脚本、无 CI。
- 根目录 `.nojekyll` 关闭 Jekyll，避免其忽略/改写文件；删它会导致
  Jekyll 重新接管（不要删）。
- 首次发布前的一次性准备：远程仓库 + Settings → Pages 启用
  Deploy from a branch: master / root。
