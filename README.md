# React + TypeScript + Vite + PNPM + Tailwind + Shadcn

使用 Vite、React、TypeScript、PNPM、Tailwind 和 Shadcn 的模板项目，快速启动现代 Web 应用开发。

## 使用模板

使用 degit 克隆模板（推荐）：

```bash
pnpm dlx degit Peiiii/vite-react-ts-pnpm-tailwind-shadcn-template my-app
cd my-app
pnpm install
```

或者直接从 GitHub 克隆：

```bash
git clone https://github.com/Peiiii/vite-react-ts-pnpm-tailwind-shadcn-template.git my-app
cd my-app
pnpm install
```

## 安装

```bash
pnpm install
```

### 添加 tailwindcss

```bash
pnpm add tailwindcss postcss autoprefixer -D
pnpm dlx tailwindcss init -p
```

配置 tailwind.config.js:

```javascript
/** @type {import('tailwindcss').Config} */
export default {
  content: ["./index.html", "./src/**/*.{ts,tsx,js,jsx}"],
  theme: {
    extend: {},
  },
  plugins: [],
};
```

在 src/index.css 中添加:

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

### 配置导入别名

1. 安装 vite-tsconfig-paths：

```bash
pnpm add -D vite-tsconfig-paths
```

2. 更新 vite.config.ts：

```typescript
import react from "@vitejs/plugin-react";
import { defineConfig } from "vite";
import tsconfigPaths from "vite-tsconfig-paths";

export default defineConfig({
  plugins: [react(), tsconfigPaths()],
});
```

3. 配置 tsconfig.json 和 tsconfig.app.json：

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
```

### 添加 shadcn/ui

```bash
# 添加必要依赖
pnpm add -D @types/node

# 添加 shadcn/ui
pnpm dlx shadcn@latest init
```

配置 components.json 时的选项:

- Style: New York
- Base color: Zinc
- CSS variables for colors: Yes

添加组件示例:

```bash
pnpm dlx shadcn@latest add button
```

现在你可以这样导入组件：

```typescript
import { Button } from "@/components/ui/button";
```

## 开发

```bash
pnpm dev
```

## 构建

```bash
pnpm build
```

## 预览

```bash
pnpm preview
```

## 添加 Workspaces 支持

### 1. 配置 pnpm-workspace.yaml

在项目根目录创建 `pnpm-workspace.yaml` 文件：

```yaml
packages:
  # 所有在 packages/ 目录下的包
  - "packages/*"
  # 所有在 apps/ 目录下的包
  - "apps/*"
```

### 2. 调整项目结构

推荐的项目结构：

```
.
├── apps/
│   ├── web/           # Web 应用
│   └── admin/         # 管理后台
├── packages/
│   ├── ui/            # 共享 UI 组件
│   └── utils/         # 共享工具函数
├── pnpm-workspace.yaml
└── package.json
```

### 3. 工作区命令示例

```bash
# 在所有工作区安装依赖
pnpm install

# 在特定工作区添加依赖
pnpm --filter @your-scope/web add lodash

# 在所有工作区运行脚本
pnpm -r dev

# 在特定工作区运行脚本
pnpm --filter @your-scope/web dev
```
