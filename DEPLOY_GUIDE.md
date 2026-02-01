# 🚀 Horae 摄影作品集 - 完整部署指南

## 方案：GitHub + Netlify + Netlify CMS（图形化管理）

---

## 📋 需要上传的文件清单

### 核心配置文件（必须上传）
```
horae-portfolio/
├── package.json              # 项目依赖配置
├── vite.config.ts            # Vite 构建配置
├── tsconfig.json             # TypeScript 配置
├── tsconfig.app.json         # TypeScript 应用配置
├── tsconfig.node.json        # TypeScript Node 配置
├── tailwind.config.js        # Tailwind CSS 配置
├── postcss.config.js         # PostCSS 配置
├── components.json           # shadcn/ui 组件配置
├── eslint.config.js          # ESLint 配置
├── index.html                # 入口 HTML 文件
├── README.md                 # 项目说明
└── .gitignore                # Git 忽略文件
```

### 源代码文件（必须上传）
```
src/
├── main.tsx                  # 应用入口
├── App.tsx                   # 主应用组件
├── App.css                   # 应用样式
├── index.css                 # 全局样式
├── components/
│   └── Navigation.tsx        # 导航栏组件
├── sections/
│   ├── Hero.tsx              # 首页区域
│   ├── Portfolio.tsx         # 作品集区域
│   ├── About.tsx             # 关于我区域
│   ├── Contact.tsx           # 联系方式区域
│   └── Footer.tsx            # 页脚区域
├── hooks/
│   └── (自定义 hooks)
├── lib/
│   └── utils.ts              # 工具函数
└── types/
    └── (类型定义)
```

### CMS 管理文件（必须上传）
```
public/
├── admin/
│   ├── index.html            # CMS 管理界面
│   └── config.yml            # CMS 配置文件
└── images/                   # 所有图片资源
    ├── hero/
    │   └── hero-bg.jpg
    ├── about/
    │   └── profile.jpg
    ├── portfolio/
    │   ├── nature/
    │   ├── architecture/
    │   └── life/
    └── uploads/              # CMS 上传的图片
```

### 内容数据文件（必须上传）
```
content/
├── hero.json                 # 首页内容
├── about.json                # 关于我内容
├── contact.json              # 联系方式
└── portfolio/
    ├── nature.json
    ├── architecture.json
    └── life.json
```

---

## 第一步：创建 GitHub 仓库

### 1.1 注册 GitHub 账号
1. 访问 https://github.com
2. 点击右上角 `Sign up`
3. 填写邮箱、密码、用户名完成注册
4. 验证邮箱

### 1.2 创建新仓库
1. 登录 GitHub
2. 点击右上角 `+` 号 → `New repository`
3. 填写信息：
   - **Repository name**: `horae-portfolio`（建议）
   - **Description**: `Horae 摄影作品集网站`
   - **Public**（选中，免费）
   - **Add a README file**: ❌ 不勾选
   - **Add .gitignore**: ❌ 不勾选
   - **Choose a license**: ❌ 不勾选
4. 点击 `Create repository`

### 1.3 上传文件到仓库

#### 方法 A：网页直接上传（适合少量文件）

1. 在仓库页面点击 `uploading an existing file`
2. 点击 `choose your files` 或拖拽文件
3. 按以下结构上传：

```
📁 先创建文件夹：
- 点击 "creating a new file"
- 文件名输入 "src/components/.gitkeep"（创建文件夹）
- 同样创建其他文件夹

📄 然后上传文件到对应位置
```

#### 方法 B：命令行上传（推荐，适合批量）

1. 在电脑上安装 Git：https://git-scm.com/downloads

2. 打开终端/命令行，执行：

```bash
# 克隆仓库到本地
git clone https://github.com/你的用户名/horae-portfolio.git
cd horae-portfolio

# 复制所有项目文件到这里
# ... 复制文件 ...

# 添加所有文件
git add .

# 提交
git commit -m "Initial commit"

# 推送到 GitHub
git push origin main
```

---

## 第二步：部署到 Netlify

### 2.1 注册 Netlify 账号
1. 访问 https://netlify.com
2. 点击 `Sign up` → 选择 `GitHub` 登录
3. 授权 Netlify 访问您的 GitHub

### 2.2 创建新站点
1. 登录 Netlify 控制台
2. 点击 `Add new site` → `Import an existing project`
3. 选择 `GitHub`
4. 找到并选择 `horae-portfolio` 仓库
5. 配置构建设置：
   - **Build command**: `npm run build`
   - **Publish directory**: `dist`
6. 点击 `Deploy site`

### 2.3 等待部署完成
- 部署大约需要 2-3 分钟
- 完成后会获得一个网址，如 `horae-portfolio-xxx.netlify.app`

---

## 第三步：启用 Netlify Identity（用户登录）

### 3.1 开启 Identity 服务
1. 在 Netlify 控制台，点击您的站点
2. 点击顶部 `Identity` 标签
3. 点击 `Enable Identity`
4. 点击 `Settings and usage`
5. 在 `Registration` 下选择 `Invite only`（推荐，更安全）
6. 在 `External providers` 下可以开启 GitHub/Google 登录

### 3.2 添加管理员用户
1. 在 Identity 页面点击 `Invite users`
2. 输入您的邮箱
3. 点击 `Send invite`
4. 查收邮件，点击链接设置密码

### 3.3 开启 Git Gateway
1. 在 Identity 页面点击 `Services`
2. 找到 `Git Gateway` 点击 `Enable Git Gateway`
3. 确认授权

---

## 第四步：配置自定义域名（可选）

### 4.1 购买域名
推荐平台：
- 阿里云：https://wanwang.aliyun.com
- 腾讯云：https://dnspod.cloud.tencent.com
- GoDaddy：https://godaddy.com

### 4.2 在 Netlify 添加域名
1. 在 Netlify 控制台点击 `Domain settings`
2. 点击 `Add custom domain`
3. 输入您的域名，如 `horae.com`
4. 按照提示在域名服务商处添加 DNS 记录

---

## 第五步：使用 CMS 管理内容

### 5.1 访问 CMS 后台
1. 在浏览器访问：`您的网址/admin`
   - 例如：`horae-portfolio.netlify.app/admin`
2. 点击 `Login with Netlify Identity`
3. 输入邮箱密码登录

### 5.2 CMS 功能介绍

#### 📷 作品集管理
- **添加新栏目**：点击 `New 📷 作品集`
- **编辑现有栏目**：点击列表中的项目
- **上传图片**：在图片字段点击 `Choose different image`
- **删除栏目**：点击项目 → 右上角 `Delete entry`

#### 👤 关于我
- 修改个人简介、头像
- 更新统计数据

#### 📧 联系方式
- 修改邮箱地址
- 更新社交媒体链接

#### 🏠 首页
- 修改首页文字内容
- 更换背景图片

### 5.3 保存和发布
1. 编辑完成后点击右上角 `Save`
2. 点击 `Publish` → `Publish now`
3. 等待约 1 分钟，网站自动更新

---

## 📁 完整的 .gitignore 文件

创建 `.gitignore` 文件，内容如下：

```gitignore
# Dependencies
node_modules
.pnp
.pnp.js

# Build
dist
dist-ssr
*.local

# Editor
.vscode/*
!.vscode/extensions.json
.idea
.DS_Store
*.suo
*.ntvs*
*.njsproj
*.sln
*.sw?

# Logs
logs
*.log
npm-debug.log*
yarn-debug.log*
yarn-error.log*
pnpm-debug.log*
lerna-debug.log*

# Environment
.env
.env.local
.env.*.local
```

---

## 🔄 更新网站的两种方式

### 方式一：通过 CMS（推荐日常更新）
1. 访问 `您的网址/admin`
2. 编辑内容 → 保存 → 发布
3. 自动部署，无需其他操作

### 方式二：通过 GitHub（代码修改）
1. 打开 GitHub 仓库
2. 找到要编辑的文件
3. 点击 `✏️` 编辑图标
4. 修改后点击 `Commit changes`
5. Netlify 自动重新部署

---

## 🛠️ 常见问题

### Q1: 部署失败怎么办？
- 检查 `package.json` 是否存在
- 确认 `Build command` 是 `npm run build`
- 确认 `Publish directory` 是 `dist`
- 查看 Netlify 部署日志找错误

### Q2: CMS 登录不了？
- 确认 Identity 已启用
- 确认 Git Gateway 已启用
- 确认您已被邀请为管理员

### Q3: 图片上传失败？
- 检查 `media_folder` 路径设置
- 确认仓库有写入权限

### Q4: 如何添加新的作品集栏目？
1. 进入 CMS → 📷 作品集
2. 点击 `New 📷 作品集`
3. 填写信息：
   - ID: 英文标识（如 `travel`）
   - 标题: 中文名称
   - 英文标题: 英文名称
   - 描述: 栏目介绍
   - 排序偏移: 0, 60, 或 120
   - 图片列表: 上传 4-6 张图片
4. 保存并发布

---

## 📞 需要帮助？

- Netlify 文档：https://docs.netlify.com
- Netlify CMS 文档：https://www.netlifycms.org/docs
- GitHub 文档：https://docs.github.com

---

**完成！您现在拥有了一个可以自主管理的摄影作品集网站！** 🎉
