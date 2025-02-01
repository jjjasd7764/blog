```

```

title: 宝塔安装教程
date: 2025-2-1 17:49:32
tags: 宝塔
----------

1、先上传文件压缩包
2.解压
3.在Python项目中添加新项目，输入原始flask5000的端口，有依赖则选择对应的依赖txt
4.添加域名
5.外网映射
6.运行配置，加入两行：
`callable = app
buffer-size = 62768  ;`
7.在软件商店中找到nginx管理
点击配置修改
在最下方增加和修改
修改服务器名
server_name  103.150.11.115;
#index index.html index.htm index.php;
#root  /www/server/phpmyadmin;

增加运行环境名
location /
{
include uwsgi_params;
uwsgi_pass 127.0.0.1:5000;
uwsgi_param UWSGI_CHDIR /外卖小程序/test22;
}

location /static/
{
alias /外卖小程序/test22/static/;
}
