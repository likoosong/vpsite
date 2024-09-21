# 快速安装并部署VitePress网站



相关的要求参见：https://vitepress.dev/guide/getting-started

## 新建目录并创建项目

假设我们要使用的目录是 vpsite

```shell
mkdir vpsite && cd vpsite
npm init -y
```

## 安装VitePress并运行

```bash
npm add -D vitepress
```

当前安装所使用的 VitePress 版本是：`1.3.4`

```bash
npx vitepress init
```

注意，为了后续方便操作，将 VitePress 创建在 `./docs`。

其中，我们还做了如下选项：

- 采用 JavaScript
- 选用缺省主题（Default Theme），但会对之定制化

创建选项如下

```tcl
┌  Welcome to VitePress!
│◇  Where should VitePress initialize the config?
│  ./docs
│
◇  Site title:
│  My Awesome Project
│
◇  Site description:
│  A VitePress Site
│
◇  Theme:
│  Default Theme + Customization
│
◇  Use TypeScript for config and theme files?
│  No
│
◇  Add VitePress npm scripts to package.json?
│  Yes
│
└  Done! Now run npm run docs:dev and start writing.

Tips:
- Since you've chosen to customize the theme, you should also explicitly install vue as a dev dependency.
```

按其中的提示，我们安装 Vue：

```bash
npm add -D vue
```

安装后，你可以查看目录结构：VitePress 项目在 `./docs`中，其中使用 `./docs/.vitepress`来存放 Theme 和配置文件。

```bash
.
├── docs
│   ├── .vitepress
│   │   ├── config.mjs
│   │   └── theme
│   │       ├── index.js
│   │       └── style.css
│   └── index.md
└── package.json
```

之后，我们将修改`config.mjs`配置，并扩展缺省主题。

## 运行与浏览网站

现在，你可以在本地运行文档网站，并在`http://localhost:5173/`查看。

```bash
npm run docs:dev
```

你可用如下命令来运行构建：

```bash
npm run docs:build
```

## 将构建的项目放在Github上

1. 习惯了白嫖，所以就要利用好免费资源，先将网站(blog) push到github开源仓库，以便下一步的操作。首先在github上创建一个项目（与本地的目录相同）如：vpsite

2. 在本地的vpsite目录下新建一个文件  .gitignore  加入以下文本

   ```text
   /node_modules
   **/dist
   **/cache
   ```

3. 将项目提交到github，这里需要先进行git bash，并且与github已经创建ssh-key等，

   ```
   git init
   git add .
   git commit -m "first commit"
   git branch -M main
   git remote add origin git@github.com:***koo****/vpsite.git
   git push -u origin main
   ```

   
## 在 Vercel 上部署你的 vitepress网站

在 Vercel 界面上，创建新项目。

选择导入我们刚刚新建的 Git Repo。（这里假设你已经做了 Vercel 和 Github 之间的连接。）

由于我们的vitepress是放在 `./docs/`目录，你可以不做任何设置，直接运行部署。

你的网站将可以部署成功。祝贺，你的网站成功上线了。

相关的部署参考见：[Deploy - Platform Guides](https://vitepress.dev/guide/deploy#netlify-vercel-cloudflare-pages-aws-amplify-render)