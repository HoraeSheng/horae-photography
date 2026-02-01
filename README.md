# Horae 摄影作品集

一个极简主义风格的个人摄影作品集网站，使用 React + TypeScript + Tailwind CSS 构建。

## 在线预览

访问您的网站：`https://您的域名.netlify.app`

访问 CMS 管理后台：`https://您的域名.netlify.app/admin`

## 技术栈

- **框架**: React 19 + TypeScript
- **构建工具**: Vite 7
- **样式**: Tailwind CSS 3.4
- **UI 组件**: shadcn/ui
- **CMS**: Netlify CMS
- **部署**: Netlify

## 项目结构

```
├── content/              # CMS 管理的内容数据
│   ├── hero.json         # 首页内容
│   ├── about.json        # 关于我
│   ├── contact.json      # 联系方式
│   └── portfolio/        # 作品集数据
├── public/
│   ├── admin/            # CMS 管理界面
│   └── images/           # 图片资源
├── src/
│   ├── components/       # 组件
│   ├── sections/         # 页面区域
│   └── ...
└── ...
```

## 本地开发

```bash
# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 构建
npm run build
```

## 内容管理

通过 Netlify CMS 管理网站内容：

1. 访问 `https://您的域名.netlify.app/admin`
2. 使用 Netlify Identity 登录
3. 在图形化界面中编辑内容
4. 点击发布，网站自动更新

## 部署指南

详见 [DEPLOY_GUIDE.md](./DEPLOY_GUIDE.md)

## 许可证

MIT
