# 这是一个不错的文档发布工具

> read the Docs 

[官方](https://readthedocs.org/)
[官方文档](https://docs.readthedocs.io/en/stable/)

## 目录

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [这是一个不错的文档发布工具](#这是一个不错的文档发布工具)
  - [目录](#目录)
  - [安装MkDocs](#安装mkdocs)
    - [设置访问ip和端口号](#设置访问ip和端口号)
    - [如何使用](#如何使用)
  - [安装sphinx](#安装sphinx)
    - [小建议](#小建议)
      - [使用配置文件](#使用配置文件)
      - [建议将sphinx的版本号固定，以免后期出现问题](#建议将sphinx的版本号固定以免后期出现问题)
    - [如果是使用markdown](#如果是使用markdown)

<!-- /code_chunk_output -->

- [ ]


## 安装MkDocs

```bash
# 安装mkdocs
pip install mkdocs

初始化 当前目录
mkdocs new .

启动服务
mkdocs serve
```

### 设置访问ip和端口号

```bash
mkdocs serve -a 0.0.0.0:80
```

### 如何使用

在我们初始化目录后，会出现

```python
  mkdocs.yml    # 配置文件
  docs/
      index.md  # 首页文件(markdown格式)
  ...           # 其他文件
```

我们只需要将我们的md文件放入docs当中，下一步直接运行mkdocs serve就能把服务跑起来了

## 安装sphinx

```bash
# 安装sphinx(默认认为你已经有了python)
pip install sphinx

# 创建项目文件夹
cd /path/to/project
mkdir docs

# 初始化项目
cd docs
sphinx-quickstart

# 构建项目 
make html
```

### 小建议

#### 使用配置文件

```python
# File: .readthedocs.yaml

version: 2

sphinx:
  configuration: docs/conf.py

python:
  version: 3.7
  install:
    - requirements: docs/requirements.txt
    
```

```python
# File: docs/requirements.txt

# Defining the exact version will make sure things don't break
sphinx==3.4.3
sphinx_rtd_theme==0.5.1
readthedocs-sphinx-search==0.1.0

```

#### 建议将sphinx的版本号固定，以免后期出现问题

[文档](https://docs.readthedocs.io/en/stable/guides/reproducible-builds.html#pinning-dependencies)

```python
# File: docs/requirements.txt

sphinx==3.4.3
sphinx_rtd_theme==0.5.1
readthedocs-sphinx-search==0.1.0rc3

```

```python
# File: docs/environment.yaml

name: docs
channels:
  - conda-forge
  - defaults
dependencies:
  - sphinx==3.4.3
  - nbsphinx==0.8.1
  - pip:
    - sphinx_rtd_theme==0.5.1
```

### 如果是使用markdown

pip install myst-parser

然后在conf.py中添加

```python
extensions = ['myst_parser']
```
