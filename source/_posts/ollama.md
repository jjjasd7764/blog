title: ollama
date: 2024-12-1 17:33:33
tags: ollama
------------

安装教程

在官网下载后自动安装

预下载的模型名直接输入命令

如

```
ollama run deepseek-r1:1.5b
```

改其他盘保存大模型需在高级系统设置添加环境

变量名填

```
OLLAMA_MODELS
```

例如，变量值填

```
F:\ollama
```

要删除一个模型，您可以使用以下命令：

```
ollama rm model\_name
```

示例

假设您要删除名为*llama3*的模型，可以输入以下命令：

```
ollama rm llama3
```

我们可以使用 **ollama list**，查看已安装的模型：

```
ollama list
```

模型启动

```
ollama run 模型名
```


**可用命令**

* serve：启动 ollama 服务。
* create：根据一个 Modelfile 创建一个模型。
* show：显示某个模型的详细信息。
* run：运行一个模型。
* stop：停止一个正在运行的模型。
* pull：从一个模型仓库（registry）拉取一个模型。
* push：将一个模型推送到一个模型仓库。
* list：列出所有模型。
* ps：列出所有正在运行的模型。
* cp：复制一个模型。
* rm：删除一个模型。
* help：获取关于任何命令的帮助信息。


### 导出模型

将模型导出为文件：

```
ollama export <model-name> <output-file>
```

例如：

```
ollama export llama2 llama2.tar
```

### 导入模型

从文件导入模型：

```
ollama import <input-file>
```

例如：

```
ollama import llama2.tar
```
