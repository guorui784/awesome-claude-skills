<!--
 * @Author: guorui
 * @Description: 
 * @Date: 2026-01-12 09:46:15
 * @LastEditTime: 2026-01-12 09:48:48
 * @FilePath: \awesome-claude-skills\artifacts-builder\SKILL.zh.md
-->
````markdown
---
name: artifacts-builder
description: 使用现代前端技术（React、Tailwind CSS、shadcn/ui）创建复杂多组件 claude.ai HTML 工件的工具集合。用于需要状态管理、路由或 shadcn/ui 组件的复杂工件 — 不适用于简单的单文件 HTML/JSX 工件。
license: 完整条款见 LICENSE.txt
---

# 工件构建器

要构建功能强大的前端 claude.ai 工件，请按以下步骤操作：
1. 使用 `scripts/init-artifact.sh` 初始化前端仓库
2. 编辑生成的代码开发你的工件
3. 使用 `scripts/bundle-artifact.sh` 将所有代码打包到单个 HTML 文件
4. 向用户展示工件
5. （可选）测试该工件

**技术栈**：React 18 + TypeScript + Vite + Parcel（打包）+ Tailwind CSS + shadcn/ui

## 设计与样式指南

非常重要：为避免常见的“AI 糟糕设计”（“AI slop”），请避免使用过度居中的布局、紫色渐变、统一的圆角以及 Inter 字体。

## 快速开始

### 第 1 步：初始化项目

运行初始化脚本以创建一个新的 React 项目：
```bash
bash scripts/init-artifact.sh <project-name>
cd <project-name>
```

该脚本会创建一个配置完善的项目，包含：
- ✅ React + TypeScript（通过 Vite）
- ✅ Tailwind CSS 3.4.1，带 shadcn/ui 主题系统
- ✅ 已配置的路径别名（`@/`）
- ✅ 预安装的 40+ 个 shadcn/ui 组件
- ✅ 包含所有 Radix UI 依赖
- ✅ 为打包配置的 Parcel（通过 `.parcelrc`）
- ✅ Node 18+ 兼容（自动检测并固定 Vite 版本）

### 第 2 步：开发你的工件

编辑生成的文件以构建工件。关于常见开发任务，请参见下文 **Common Development Tasks（常见开发任务）** 的指导。

### 第 3 步：打包为单个 HTML 文件

将 React 应用打包为单个 HTML 工件：
```bash
bash scripts/bundle-artifact.sh
```

此操作会生成 `bundle.html` —— 一个自包含的工件，所有 JavaScript、CSS 及依赖都被内联。该文件可以直接在 Claude 会话中作为工件共享。

**要求**：你的项目根目录必须包含 `index.html`。

**脚本执行内容**：
- 安装打包依赖（parcel、@parcel/config-default、parcel-resolver-tspaths、html-inline）
- 创建带路径别名支持的 `.parcelrc` 配置
- 使用 Parcel 构建（不生成 source maps）
- 使用 html-inline 将所有资源内联到单个 HTML

### 第 4 步：与用户共享工件

最后，将打包后的 HTML 文件在对话中分享给用户，以便他们查看此工件。

### 第 5 步：测试/可视化工件（可选）

注意：这是完全可选的步骤，仅在必要或被请求时执行。

要测试/可视化工件，可使用可用工具（包括其他 Skill 或内置工具，如 Playwright 或 Puppeteer）。通常应避免在一开始就测试工件，因为这会增加从请求到看到最终工件之间的延迟。建议在呈现工件后、用户提出或出现问题时再进行测试。

## 参考

- **shadcn/ui 组件**：https://ui.shadcn.com/docs/components

````
