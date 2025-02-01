title: git推送至github方法
date: 2025-2-1 17:49:32
tags: git
---------

1.在文件夹目录下，先使用git init初始化git

```
git init
```

2.添加文件到暂存区(更新从第二步开始)

```
git add .
```

3.将暂存区的内容添加到本地仓库，“blog1”根据需求修改

```
git commit -m "blog1"
```

4.创建分支

```
git branch -M main
```

5.配置远程仓库(如果仓库已存在，则使用更新URL命令)

```
git remote add origin "https://github.com/jjjasd7764/blog2.git"
```

6.将本地仓库代码推送到远程的仓库当中

```
git push -u origin main
```

**更新现有的远程仓库 URL**：

```
git remote set-url origin "https://github.com/jjjasd7764/blog.git"
```

服务器操作，删除现有的 `blog` 目录再重新克隆

```
rm -rf blog
```

<pre class="code-block-wrapper"><div class="code-block-header"><br class="Apple-interchange-newline"/></div></pre>

克隆仓库的命令

```
git clone 仓库链接
```

更新仓库，新建仓库，复制新仓库链接得以更新

错误修复error: remote origin already exists.

**方法一：使用 HTTPS 连接（推荐）：**

* **修改 `origin` 远程仓库的 URL：**

```
git remote set-url origin "https://github.com/jjjasd7764/blog2.git"
```

再次尝试推送

```
git push -u origin main
```
