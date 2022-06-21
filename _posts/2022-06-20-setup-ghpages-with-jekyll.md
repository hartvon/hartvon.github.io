---
layout: post
title:  "Setup Github Pages with Jekyll"
categories: Configuration
---

**1. 安装 Jekyll 静态网页生成器**

在 `Ubuntu or wsl` 中安装 Ruby 及其他依赖项：

```bash
$ sudo apt-get install ruby-full build-essential zlib1g-dev
```

向 `~/.bashrc` 中添加 gem 安装路径变量：

```bash
$ echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
$ echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
$ echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
$ source ~/.bashrc
```

安装 Jekyll 和 Bundler：

```bash
$ gem install jekyll bundler
```

**2. 初始化blog本地仓库**

切换到要建立blog仓库的上一级目录，新建一个名为 `myblog` 的 Jekyll 站点：

```bash
$ jekyll new myblog
```

在 github 中新建一个远程仓库：`<user>.github.io`，其中 `<user>` 为 github 用户名，
切换到 `myblog` 目录进行 git初始化并添加上述远程仓库：

```bash
$ cd myblog
$ git init
$ git remote add origin https://github.com/<user>/<user>.github.io.git
```

**3. 本地构建或远程构建**

- 本地构建

在 `myblog` 目录中输入命令：

```bash
$ bundle exec jekyll serve
```

便可以在本地端口中查看网页更新效果

- 远程构建

将本地仓库更新的内容推送到远程仓库：

```bash
$ git add .
$ git commit -m "commit msg"
$ git push -u origin master
```

便可以在 `https://<user>.github.io` 中查看网页更新效果

**Resources:**
- <https://jekyllrb.com/docs/installation/ubuntu/>
- <https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/>
- <https://blog.shahednasser.com/deploy-a-website-with-jekyll-and-github-pages/>
- <http://www.stephaniehicks.com/githubPages_tutorial/pages/githubpages-jekyll.html>