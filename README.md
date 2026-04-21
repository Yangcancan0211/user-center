# user-center
基于 Vue 3、TypeScript 和 Ant Design Vue 开发的一个简单的 “用户管理系统” ，实现了用户注册、登录、查询等基础功能。

> **💡 提示**：由于本项目目前为纯前端展示版，登录验证逻辑已在前端 Mock 处理，无需启动后端即可体验完整功能。

## 🛠️ 技术栈

- **核心框架**: Vue 3.5+ (Composition API)
- **构建工具**: Vite 5.x (已优化打包路径)
- **路由管理**: Vue Router 4.x (包含全局权限守卫)
- **状态管理**: Pinia 2.x (支持持久化插件)
- **UI 组件库**: Ant Design Vue 4.x
- **样式方案**: Windi CSS / CSS Modules
- **开发语言**: TypeScript 5.x

## 📂 项目结构

```text
├── src/
│   ├── access/        # 权限控制模块 (RBAC 核心逻辑)
│   ├── api/           # 接口请求层 (预留 RESTful 接口)
│   ├── components/    # 通用业务组件
│   ├── layouts/       # 页面基础布局 (侧边栏、顶栏)
│   ├── router/        # 路由配置与动态权限守卫
│   ├── store/         # Pinia 状态管理 (包含用户信息)
│   └── pages/         # 业务页面 (登录、用户管理、个人中心)
├── public/            # 静态资源
├── vite.config.ts     # Vite 核心配置 (已配置 base: './')
├── package.json       # 项目依赖与脚本
└── README.md          # 项目说明文档
```

## 🚀 快速开始

### 环境准备

- Node.js >= 18.0.0
- npm >= 9.0.0

### 安装步骤

1. **克隆项目**
   ```bash
   git clone https://github.com/Yangcancan0211/user-center-frontend
   cd user-center-frontend
   ```

2. **安装依赖**
   ```bash
   npm install
   ```

3. **启动项目**
   ```bash
   npm run dev
   ```

4. **项目打包**
   ```bash
   npm run build
   ```

## ✨ 核心功能实现

### 1. 权限拦截 (Permission Guard)
项目在 `router/index.ts` 中集成了全局前置守卫。系统会自动校验 `localStorage` 中的登录态，并根据 `userRole` 判断用户是否有权进入 `/admin` 路径下的管理页面。

### 2. 打包路径优化 (Vite Config)
针对静态部署环境，在 `vite.config.ts` 中配置了 `base: './'`。该配置确保了项目在 GitHub Pages 或私有静态服务器上部署时，JS 和 CSS 资源能被正确加载，解决了常见的 **404 Not Found** 报错。

### 3. 状态持久化
通过 Pinia 管理用户信息，并结合本地缓存技术。即使用户刷新浏览器，登录状态和权限信息也不会丢失，保证了良好的用户体验。

## ❓ 常见问题

### 1. 打包后双击 index.html 报错
**现象：** 提示跨域或资源加载失败。
**原因：** 浏览器出于安全考虑，限制了以 `file://` 协议运行脚本。
**解决方法：** 建议使用 `npx serve dist` 启动一个本地静态服务器查看效果，或直接部署至 GitHub Pages。

### 2. 后端接口对接
本项目已封装标准的 Axios 请求层。若需对接真实后端，只需修改 `api/` 目录下的接口地址，并确保后端已开启 CORS 跨域支持。

