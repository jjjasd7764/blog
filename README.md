# Hexo Blog Setup Guide

## 简介

本指南旨在帮助您在已有的 Node.js 和 Git 环境下，快速安装并配置 Hexo 博客环境。

## 安装步骤

### 1. 安装 Hexo CLI

首先，确保您的系统中已安装 Node.js 和 npm（Node.js 包管理器）。您可以通过以下命令全局安装 Hexo CLI：

```bash
npm install hexo-cli -g
# 或者使用淘宝镜像源
cnpm install hexo-cli -g
2. 初始化 Hexo 博客
安装完成后，使用以下命令初始化一个新的 Hexo 博客项目：

bash
hexo init blog
这将创建一个名为 blog 的文件夹，其中包含了 Hexo 博客的基本结构。

3. 进入博客目录
进入刚刚创建的博客目录：

bash
cd blog
4. 安装依赖
在博客目录下，运行以下命令安装项目依赖：

bash
npm install
5. 启动本地服务器
安装依赖后，使用以下命令启动本地服务器：

bash
hexo server
6. 验证安装
如果一切顺利，您应该能够在浏览器中通过以下地址访问您的博客：

http://localhost:4000/
7. 克隆或解压项目
如果需要将现有的 Hexo 博客项目集成到您的本地环境中，请按照以下步骤操作：

克隆或解压您的 Hexo 项目到 blog 目录下。
再次进入该已解压好的文件夹：
bash
cd path/to/your/hexo-project
重新启动本地服务器：
bash
hexo server
重新访问 http://localhost:4000/，您应该能够看到更新后的博客内容。
注意事项
