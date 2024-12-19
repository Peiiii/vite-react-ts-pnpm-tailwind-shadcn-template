# React + TypeScript + Vite

使用 Vite、React、TypeScript、PNPM、Tailwind 和 shadcn/ui 的模板项目，快速启动现代 Web 应用开发。

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
