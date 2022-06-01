---
title: Hexo博客搭建
date: 2022-05-28 12:39:10
tags: Hexo
categories: Blog
top_img: /images/hello.jpg
cover: /images/hello.jpg
---
# 前言
{% note default flat %}
Hexo 是一个基于NodeJS的静态博客网站生成器，使用Hexo不需开发，只要进行一些必要的配置即可生成一个个性化的博客网站，并且完美支持Markdown格式，非常方便。
{% endnote %}
## 环境搭建
### 安装git
- windows可直接到<a href=https://git-scm.com/downloads>Git官网</a>自行下载安装，一路Next，安装完成后，需要将Git命令行工具添加到环境变量中，不在赘述。linux可通过终端命令行安装，如下：
```bash
yum -y install git
```
### 安装Node.js
- windows可直接到<a href=https://nodejs.org/en/>Node.js官网</a>自行下载安装，一路Next,下载完成后需将.exe文件加入环境变量，不在赘述。

### linux安装Node.js
- 在官网下载指定的包后上传至linux指定位置，然后进入系统目录，执行以下命令解压：

```bash
tar -xvf node-v10.6.0-linux-x64.tar.xz
```
- 通过建立软连接，将解压后的文件夹放入环境变量中，如下：

```bash
ln -s /usr/local/node-v10.6.0-linux-x64/nodejs/bin/npm /usr/local/bin/
ln -s /usr/local/node-v10.6.0-linux-x64/nodejs/bin/node /usr/local/bin/
```
- 检查是否安装成功，如下：

```bash
node -v
```
## 安装Hexo
- 直接通过终端命令进行安装（安装完成后需将hexo.cmd所在目录加入环境变量中，否则执行hexo命令会报错，hexo.cmd默认安装在Node目录下）：

```bash
npm install -g hexo-cli
```
- 检查是否安装成功，如下：

```bash
hexo -v
```
- 新建一个文件夹，来进行初始化项目：

```bash
hexo init
```
- 安装依赖包：

```bash 
npm install
```
- 生成静态文件：

```bash
hexo generate
```
- 启动服务：

```bash 
hexo server
```
- 以上操作完成后即可通过浏览器输入网址http://localhost:4000访问项目，效果如下：

![](/images/hexo.png)

### 将项目部署至github
- 首先右键打开git bash，然后输入下面命令配置git的相关信息：

```bash
git config --global user.name "你的用户名"
git config --global user.email "你的邮箱"
```
输入下面命令生成ssh key：
```bash
ssh-keygen -t rsa -C "你的邮箱"
```
创建完成后会在本地生成一个文件夹，在文件中找到id_rsa.pub，复制出来，默认目录为：
```bash
C:\Users\17621\.ssh
```
{% note success no-icon %}
然后在github点击自己的头像，点击setting，再点击SSH and GPG keys，新建一个SSH，名字随便。将刚刚复制出来的id_rsa.pub添加进去，点击save，完成。
{% endnote %}
{% note success no-icon %}
在github新建一个项目，如下图所示：
{% endnote %}
![](/images/new_repository.jpg)
{% note success no-icon %}
在Repository name中输入你的用户名.github.io，点击Create repository，即可完成项目的创建。
然后可通过page页面查看项目的地址，如下：
{% endnote %}
![](/images/repository_url.jpg)
### 将项目部署至GitHub Pages
{% note info simple %}
打开项目根目录下的_config.yml文件，拉到最后一行，添加如下内容：
{% endnote %}
```yaml
deploy:
    type: git
    repository: github.com/你的用户名/你的用户名.github.io.git
    branch: master
```
{% note info simple %}
安装hexo-deployer-git，并在hexo中安装：
{% endnote %}
```bash
npm install hexo-deployer-git --save
```
{% note info simple %}
然后在项目根目录下执行以下命令：
{% endnote %}
```bash
hexo clean
hexo generate
hexo deploy
```
{% note info simple %}
项目生成后，可通过浏览器输入网址http://你的用户名.github.io访问项目，效果如下：
{% endnote %}

![](/images/blog_index.jpg)

