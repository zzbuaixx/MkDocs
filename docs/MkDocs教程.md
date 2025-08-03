# MkDocs教程

使用Markdown创建自己的个人网页文档



## 安装

首先，得确认自己电脑里面有`python`,以及和Python的包管理器`pip`,打开cmd命令行，使用以下命令来检测

```cmd
C:\Users\ZXJ>python --version
Python 3.8.3

C:\Users\ZXJ>pip --version
pip 25.0.1 from D:\Python38\lib\site-packages\pip (python 3.8)

```

python和pip的安装教程自行百度

### 安装MkDocs

使用pip安装`MkDocs`

```
python get-pip.py
```

使用以下命令检测是否安装正常

```
C:\Users\ZXJ>python --version
Python 3.8.3

C:\Users\ZXJ>pip --version
pip 25.0.1 from D:\Python38\lib\site-packages\pip (python 3.8)

```



## 使用教程

如果你成功安装好了Mkdocs，那么使用教程就非常简单了。使用PowerShell运行以下命令

```
mkdocs new my-project
cd my-projecgt
```

这个文件里面有一个mkdocs.yml的配置文件和doc的文件夹，这里面包含了所用的文档。现在只有一个index.md的文档。



MkDocs带有一个内置的服务器，可以让你在处理文档时预览文档。 确保与`mkdocs.yml`配置文件位于同一目录中，然后通过运行`mkdocs serve`命令启动服务器：

```
$ mkdocs serve
INFO    -  Building documentation...
INFO    -  Cleaning site directory
[I 160402 15:50:43 server:271] Serving on http://127.0.0.1:8000
[I 160402 15:50:43 handlers:58] Start watching changes
[I 160402 15:50:43 handlers:60] Start detecting changes
```

在浏览器中打开`http://127.0.0.1:8000/`，将看到显示的默认主页：![image-20250803182827996](C:\Users\ZXJ\AppData\Roaming\Typora\typora-user-images\image-20250803182827996.png)

现在尝试编辑配置文件：`mkdocs.yml`。 将[`site_name`][site_name]设置更改为“MkLorum”并保存文件。

```yaml
site_name: MkLorum
```

浏览器刷新后，将看到新设置的站点名称已经生效。

## 添加页面

创建一个test.md文件,然后再配置文件里面，由于我们的文档站点将包含一些导航，你可以编辑配置文件，并通过添加[`nav`][nav]设置来管理每个页面导航的顺序、标题和嵌套情况：

```
site_name: MkLorum
nav:
    - Home: index.md
    - Test: test.md
```

保存更改，你将看到左侧有“Home”和“About”导航栏，同时右侧还有“Search”，“Previous”和“Next”。



一段时间后，文件可能会从文档中删除，但它们仍将驻留在`site`目录中。 要删除那些陈旧的文件，只需在运行`mkdocs`命令时带上`--clean`参数即可。

```bash
mkdocs build --clean
```



## 修改主题

现在，更改配置文件以通过更改主题来更改文档的显示方式。 编辑`mkdocs.yml`文件并添加[`theme`] [theme]设置：

```site_name: MkLorum
nav:
    - Home: index.md
    - About: about.md
theme: readthedocs
```

## 生成网站

首先生成文档:

```
mkdocs build

```

这将创建一个名为`site`的新目录。 看一下该目录的情况：

```bash
$ ls site
about  fonts  index.html  license  search.html
css    img    js          mkdocs   sitemap.xml
```

请注意，你的源文档已输出为两个名为`index.html`和`about/index.html`的HTML文件。同时各种其他媒体文件也已被复制到`site`目录中作为文档主题的一部分。另外还有一个`sitemap.xml`文件和`mkdocs/search_index.json`。

如果你正在使用版本控制软件，例如`git`，你可能不希望将生成的文件包含到存储库中。只需要在`.gitignore`文件中添加一行`site/`即可。

```bash
echo "site/" >> .gitignore
```

如果你正在使用其他版本控制工具，请你自行查阅相关文档，了解如何忽略特定目录。

一段时间后，文件可能会从文档中删除，但它们仍将驻留在`site`目录中。 要删除那些陈旧的文件，只需在运行`mkdocs`命令时带上`--clean`参数即可。

```bash
mkdocs build --clean
```

##其他命令和选项

还有其他各种命令和选项。有关命令的完整列表，请使用`--help`标志：

```bash
mkdocs --help
```

要查看给定命令上可用的选项列表，请使用带有该命令的`--help`标志。 例如，要获取`build`命令可用的所有选项的列表，请运行以下命令：

```bash
mkdocs build --help
```

## 部署

使用github page部署自己的文档，在github创建新项目

然后在本地文件夹执行以下推荐命令

```

git init  初始化仓库





```

创建一个名为 `.gitignore` 的文件。这个文件用来告诉 Git 哪些文件或文件夹永远不要跟踪。

在 `.gitignore` 文件里写入以下内容：

```
site/
mkdocs.yml.bak
```

然后继续

```

git add . 添加暂存区
git commit -m "first commit"  提交
git branch -M main 创建主分支
git remote add origin  git@github.com:zzbuaixx/test.git 关联
git push -u origin main 推送
```

执行完之后，使用mkdoc是gh-deploy部署

在本地目录运行

```mkdocs gh-deploy
mkdocs gh-deploy
```

在github主页，点击settting，点击Pages，可以看到

```
Your site is live at https://zzbuaixx.github.io/learn-MkDocs/
```

这样网页就部署好了。