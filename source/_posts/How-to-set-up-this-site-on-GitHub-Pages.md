---
title: How to set up this site on GitHub Pages
date: 2018-12-28 17:42:53
tags: build site
---

## Branches

- master 是部署分支，hexo打包之后部署到这个分支，不用新建 gh-pages，默认用 master分支
- development 是开发分支，在这个分支里写文章，然后部署到master。

## Steps

- 建一个新的 repo，名字叫 `username.github.io`。一定要这个名字，用 `username.github.io`去访问时才会解析到这个 repo
- master分支里就留个 `.gitignore`就行了，其他的不需要，而且 `hexo deploy`会覆盖掉
- 新建分支 development，然后 `hexo init`，添加基本的东西
- `npm install hexo-deployer-git --save` 添加库，用来部署的。
- `hexo s` `hexo g` `hexo d` 预览，打包，部署一条龙
- deploy配置，`repo`不需要非用`ssh`方式，`https`也是可以的，然而一帮人说不可以。

```yml
deploy:
  type: git
  repo: https://github.com/username/username.github.io.git
  branch: master
  message: update blogs
```