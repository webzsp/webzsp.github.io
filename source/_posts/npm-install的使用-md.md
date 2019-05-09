---
layout: _post
title: npm-install的使用.md
date: 2019-05-09 15:38:22
tags: 随笔
---

# 前端npm-install的使用
随着前端和node的发展,node附带的包管理器已经成为前端必备的工具了,但是很多人基本上只会使用npm install 来安装第三方包.报错了就直接删除掉整个node-modules 文件夹,在执行一次npm-install.
# 1 npm 中的包
我们经常使用的就是npm install <packageName> 来安装第三方包,但是包[官方文档](https://docs.npmjs.com/about-packages-and-modules)中是这样定义的:

A package is any of the following:

* a) A folder containing a program described by a package.json file.
* b) A gzipped tarball containing (a).
* c) A URL that resolves to (b).
* d) A <name>@<version> that is published on the registry with (c).
* e) A <name>@<tag> that points to (d).
* f) A <name> that has a latest tag satisfying (e).
* g) A git url that, when cloned, results in (a).

翻译过来就是
* a) 一个包含package.json的文件夹
* b) 可以理解为a的压缩版.
* c) b的网络地址.
* d) 一个格式为 \<name>@\<version> 的字符串，可指向 npm 源上已发布的可访问 url，且该 url 满足条件 (c)	.
* e) 一个格式为\<name>@\<tag> 的字符串，在 npm 源上该\<tag>指向某 \<version> 得到 \<name>@\<version>，后者满足条件 (d)
* f) 一个字符串,默认添加@latest标签所得到的\<name>@latest 满足e.
* g) 一个 git url, 该 url 所指向的代码库满足条件 (a);

可以发现a条件是根本,其他条件都是在a的基础上来更精确更方便的访问到包.
# 1.1 使用本地包
没啥用
# 2 npm insatll 常用命令
