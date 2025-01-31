title: git推送至github方法
date: 2025-2-1 17:49:32
tags: git
---------

1.在文件夹目录下，先使用git init初始化git

```
git init
```

2.添加文件到暂存区

```
git add .
```

3.将暂存区的内容添加到本地仓库

```
git commit -m "blog1"
```

4.创建分支

```
git branch -M main
```

5.配置远程仓库

```
git remote add origin "仓库链接"
```

6.将本地仓库代码推送到远程的仓库当中

```
git push -u origin main
```
