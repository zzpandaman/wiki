# sphinx

## 1. 安装

- 通过pip安装(默认已安装python)

```cmd
pip install -i https://pypi.douban.com/simple/ sphinx
```

- QuikStart

```cmd
cd workplace 
sphinx-quikstart  
make clean
make html  
```

- 替换默认主题

	+ 安装主题，这里选择sphinx_rtd_theme

	```cmd
	pip install -i https://pypi.douban.com/simple/ sphinx_rtd_theme
	```

	+ 添加配置，修改conf.py

	```python
	import sphinx_rtd_theme
	html_theme = 'sphinx_rtd_theme'
	```

	+ 自适应宽度<br>
	
	```css
	//在source/_static目录下建立style.css

	.wy-nav-content {
		max-width: none;
	}
	```

	```css
	//在source/_templates目录下建立layout.html

	{% extends "!layout.html" %}
	{% block extrahead %}
    <link href="{{ pathto("_static/style.css", True) }}" rel="stylesheet" type="text/css">
	{% endblock %}
	```

- 使用markdown编写文档

	- 安装支持
	```cmd
	pip install -i https://pypi.tuna.tsinghua.edu.cn/simple recommonmark sphinx_markdown_tables
	```

	- 添加配置，修改conf.py
	```python
	extensions = [
	# "myst-nb",
	'recommonmark',
	'sphinx_markdown_tables'
	]
	```

	- 如何使用Markdown: 访问 [Markdown官网](https://markdown.com.cn/)

## 2. 托管

- 上传到git

```cmd
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:luhuadong/diary.git
git push -u origin main
```

- 托管到 read the docs

访问 [readthedocs官网](https://readthedocs.org) ，按提示操作即可


