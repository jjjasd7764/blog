title: lobechat本地部署+ollama访问
date: 2025-3-22 9:49:32
tags:
-----

#使用docker部署好lobechat环境

#下载ollama，并且运行对应的大模型

#准备两个内网穿透服务

1.穿透lobechat的本机地址127.0.0.1:3210（网页访问地址）

2.穿透127.0.0.1:11434 ollama的地址（等于是API）

#访问lobechat地址使用

1.点击头像

2.找到ollama

```
首次登录时对话需要输入密码lobechat66,进行验证,否则无法搜索到模型
```

3.配置ollama的服务地址，勾选上模型列表里的对应模型

4，返回对话框，选择ollama的模型即可对话。

5.[手把手教你使用 Ollama 和 LobeChat 快速本地部署 DeepSeek R1 模型，创建个性化 AI 助手 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/21282110989)
