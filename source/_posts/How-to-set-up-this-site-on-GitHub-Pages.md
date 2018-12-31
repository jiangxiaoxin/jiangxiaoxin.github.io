---
title: How to set up this site on GitHub Pages
date: 2018-12-28 17:42:53
tags: build site
---

## Branches

- master 是部署分支，hexo打包之后部署到这个分支，不用新建 gh-pages，默认用 master分支
- development 是开发分支，在这个分支里写文章，然后部署到master。

## Steps

- 建一个新的 repo，名字叫 `username.github.io`。**一定**要这个名字，用 `username.github.io` 去访问时才会解析到这个 repo
- `master` 分支里就留个 `.gitignore` 就行了，其他的不需要，而且 `hexo deploy` 会覆盖掉
- 安装 hexo 工具：`npm install -g hexo-cli`
- 新建分支 `development`，然后 `hexo init`，`npm install`，添加基本的东西
- `npm install hexo-deployer-git --save` 添加用来 git 部署的库。
- hexo 的默认工程会有一篇《hello world》文章，`hexo s` `hexo g` `hexo d` 预览，打包，部署一条龙。
- deploy 配置，`repo`不需要非用 `ssh`方式，`https`也是可以的，_然而一帮人说不可以_。上传的分支也不需要 `gh-pages`，直接用 `master` 就可以了。

```yml
deploy:
  type: git
  repo: https://github.com/username/username.github.io.git
  branch: master
  message: update blogs
```

- 我用的是流行的 `next` 主题，并没有 git 一起提交到代码库，多地部署时，要重新 clone 最新的主题包文件（也可以自己定一个固定的版本），不然就会报一个错误： `no layout: index.html`