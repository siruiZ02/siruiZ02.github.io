# Sirui Li · 个人主页

ETH NSG 风格的多页面学术主页，用 Jekyll 写成，GitHub Pages 原生支持，不需要配置 GitHub Actions。

## 一、上传（只需要做一次）

1. 在 GitHub 新建仓库，名字必须是 `你的用户名.github.io`，设为 **Public**，不要勾选 "Add a README"。
2. 进入仓库页面，点 **uploading an existing file**（或 Add file → Upload files）。
3. 把解压后文件夹里的**所有内容**（不是外面那层文件夹本身）拖进去，包括 `_config.yml`、`_data`、`_includes`、`_layouts`、`assets` 等。
   以下划线开头的文件夹一个都不能漏。
4. 点 **Commit changes**。
5. 进入 **Settings → Pages**：Source 选 **Deploy from a branch**，Branch 选 **main**，文件夹选 **/ (root)**，Save。
6. 等 1~2 分钟，打开 `https://你的用户名.github.io`。

> 以后每次在 GitHub 上修改文件并 Commit，网站都会自动在 1~2 分钟内更新。
> 如果没更新，去仓库的 **Actions** 标签页看 "pages build and deployment" 有没有红叉，点进去能看到报错的文件和行号。

## 二、要改哪里

| 想改什么 | 改哪个文件 |
|---|---|
| 网址里的用户名、名字、职位、头像下面那列链接 | `_config.yml` |
| 顶部导航栏有哪些页面 | `_config.yml` 里的 `nav` |
| 首页的自我介绍（Bio） | `index.md`（Markdown 格式） |
| 新闻 | `_data/news.yml` |
| 论文（首页 Selected + Publications 页） | `_data/publications.yml` |
| 报告 / 分享 | `_data/talks.yml` |
| 头像 | 照片命名为 `photo.jpg` 放进 `assets/img/` |
| CV、论文 PDF、slides | 放进 `assets/pdf/`，然后在对应文件里写 `/assets/pdf/文件名.pdf` |
| 颜色 | `assets/css/style.css` 开头的 `--accent` |

**加一篇论文**：在 `_data/publications.yml` 里复制一整块（从 `- title:` 到下一块之前），改内容。
`selected: true` 会上首页；你的名字会自动加粗。

**加一个新页面**（比如 Projects）：
1. 复制 `talks.html`，改名为 `projects.html`，把开头的 `title` 和 `permalink` 改成 `Projects` 和 `/projects/`，下面内容换成你自己的 HTML。
   想用 Markdown 写的话，就建 `projects.md`，开头保留同样的三行 `---` front matter，下面直接写 Markdown。
2. 在 `_config.yml` 的 `nav` 里加一行 `- title: Projects` / `url: /projects/`。

## 三、YAML 小坑

- 缩进只能用**空格**，不能用 Tab；同一块里的字段对齐。
- 文字里有冒号 `:`、`#`、引号时，整段用双引号包起来，例如 `title: "Agents: A Survey"`。
- 改完 `_config.yml` 一定要看一眼 Actions 有没有报错，这个文件写错整个网站都会挂。

## 四、本地预览（可选）

装好 Ruby 后：

```bash
bundle install
bundle exec jekyll serve
```

打开 http://localhost:4000 。不想装也没关系，直接改 GitHub 上的文件就行。
