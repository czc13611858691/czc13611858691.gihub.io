# Czc's Blog

**克隆仓库地址**

```
git clone https://github.com/czc13611858691/czc13611858691.gihub.io.git
```

**安装nodejs**

[官网地址](https://nodejs.org/en/download/)

检查安装成功cmd指令

```
node -v
npm -v
```

**进入博客文件夹**

安装hexo-cli

```
npm install -g hexo-cli
```

```
hexo init blog
```

```
cd blog
```

```
hexo g
hexo s
```

浏览器输入

```
localhost:4000
```

**发布文章**

在blog文件夹下输入

```
hexo new "文章名"
hexo g -d
```

**给文章添加标签和分类**

示例如下:

```
categories:
- 测试分类
tags:
- 测试标签
```

**拉取仓库hexo new报错**

执行推荐命令如下

```
rm -rf node_modules && npm install --force
```

**hexo 报错**

```
Error: Cannot find module
```

```
npm install hexo --no-optional
```

**自动提交命令**

打开blog目录cmd

```
./hexo_g_d.bat
```

