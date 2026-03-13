# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Structure

This is a **pnpm monorepo** containing two separate packages:

- `packages/uni-app-vue3` - uni-app 项目，使用 Vue 3，支持多端开发（H5、微信小程序、支付宝小程序等）
- `packages/vue3` - 标准 Vue 3 + TypeScript + Vite 项目

## Common Commands

### uni-app-vue3 (packages/uni-app-vue3)

开发服务器需要指定平台：
```bash
cd packages/uni-app-vue3
pnpm dev:h5           # H5 开发
pnpm dev:mp-weixin    # 微信小程序开发
pnpm dev:mp-alipay    # 支付宝小程序开发
pnpm dev:custom       # 自定义平台 (使用 -p 参数)
```

构建生产版本：
```bash
pnpm build:h5         # H5 构建
pnpm build:mp-weixin  # 微信小程序构建
pnpm build:custom     # 自定义平台构建
```

### vue3 (packages/vue3)

标准 Vite 开发和构建：
```bash
cd packages/vue3
pnpm dev              # 启动开发服务器
pnpm build            # TypeScript 类型检查 + 构建
pnpm preview          # 预览生产构建
```

### Monorepo 操作

在根目录安装依赖：
```bash
pnpm install
```

## Architecture Notes

### uni-app-vue3

- 使用 `@dcloudio/vite-plugin-uni` Vite 插件进行 uni-app 编译
- 配置文件：
  - `src/pages.json` - 页面路由配置（uni-app 标准格式）
  - `src/manifest.json` - 应用配置
  - `src/main.js` - 使用 `createSSRApp` 创建应用实例
- 支持 SSR：通过 `dev:h5:ssr` 和 `build:h5:ssr` 命令
- Vue 版本：3.4.21
- Vite 版本：5.2.8

### vue3

- 标准 Vue 3 SFC (`<script setup>`) + TypeScript 项目
- Vue 版本：3.5.25
- Vite 版本：7.3.1
- TypeScript 配置使用项目引用（tsconfig.json references）

## Workspace Configuration

pnpm workspace 定义在 `pnpm-workspace.yaml`，模式为 `packages/*`。
