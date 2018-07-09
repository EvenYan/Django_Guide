---
typora-copy-images-to: images
typora-root-url: images
---

# Django是个啥

​	最初是被开发来用于管理劳伦斯出版集团旗下的一些以新闻内容为主的网站的。并于2005年7月在BSD许可证下发布。这套框架是以比利时的吉普赛爵士吉他手Django Reinhardt来命名的。

​	Django的主要目标是使得开发复杂的、数据库驱动的网站变得简单。Django注重组件的重用性和“可插拔性”，敏捷开发和DRY法则（Don't Repeat Yourself）。在Django中Python被普遍使用，甚至包括配置文件和数据模型。

- 由 Python 开发的一个免费的开源网站框架，可以用于快速搭建高性能，优雅的网站

- Django 中提供了开发网站经常用到的模块，常见的代码都为你写好了

- Django 提供了通用Web开发模式的高度抽象，提供了频繁进行的编程作业的快速解决方法，以及为“如何解决问题”提供了清晰明了的约定。

- Django的理念是DRY(Don't Repeat Yourself)来鼓励快速开发！

  

# 开发环境

Ubuntu + Python3  + Django + PyCharm



# Ubuntu系统和命令介绍

### 系统设置



### 常用命令

- cd
- ls
- cp
- mv
- rm
- mkdir
- pwd
- touch
- cat
- history
- ps
  - ps -aux
- kill 
  - kill -9 pid
- su/sudo
- chmod
- grep
- which
- whereis
- ifconfig
- netstat
  - netstat -antp 查看网络连接状态
- wget
- ssh username@host -p
  - ssh-keygen
- tar
  - tar -zxvf 解压缩
  - tar -cxvf 压缩
- du
  - du -sh
- df
  - df -h
- apt install
- apt update
- apt remove
- apt autoremove
- dpkg -i
- vi/vim

# BS/CS

​        C/S 架构即“客户端-服务器” 架构。这里的“客户端”可以是有 GUI （图形用户界面）的定制软件，也可以是浏览器，甚至可以是通过 SSH 访问服务器的命令行脚本。只要是客户端通过访问服务器调取计算或者存储资源的，统统都是 C/S 架构。所谓的 Browser-Server 架构其实是 C/S 架构的一种特殊的实现形式，而不是其对立面。

- C/S:
  - C: Client
  - S: Server
- B/S
  - B: Browser
  - S: Server       

# MVC/MVT

- MVC

  - M: Model（模型）
  - V: View（视图）
  - C: Controller（控制器）

- MVT

  - M: Model（模型），主要封装对数据库层的访问，对数据库中的数据进行增、删、改、查操作。

  - V: View（视图），用于封装结果，生成页面展示的html内容。

  - T: Template（模板），用于接收请求，处理业务逻辑，与Model和View交互，返回结果。

    ​

# HelloDjango项目

### 创建虚拟环境

### 虚拟环境的优点

- 使不同应用开发环境独立
- 环境升级不影响其他应用，也不会影响全局的python环境
- 可以防止系统中出现包管理混乱和版本冲突

开发会用 virtualenv 来管理多个开发环境

#### Linux/MacOS 下

virtualenvwrapper 使得virtualenv变得更好用，所以我们一起安装了

```
(sudo) pip install virtualenv virtualenvwrapper
```

修改~/.bash_profile或其它环境变量相关文件(如 .bashrc 或用 ZSH 之后的 .zshrc)，添加以下语句

```
export WORKON_HOME=$HOME/.virtualenvs
export PROJECT_HOME=$HOME/workspace
source /usr/local/bin/virtualenvwrapper.sh(每台机子的位置不一样，可以通过find命令找到)
```

修改后使之立即生效(也可以重启终端使之生效)：

```
source ~/.bash_profile
```



#### Windows 下：

```
pip install virtualenv virtualenvwrapper-win
```

【可选】Windows下默认虚拟环境是放在用户名下面的Envs中的，与桌面，我的文档，下载等文件夹在一块的。更改方法：计算机，属性，高级系统设置，环境变量，添加WORKON_HOME，如图（windows 10 环境变量设置截图）：

![](/1.png)

#### 虚拟环境使用方法：

- **mkvirtualenv django：创建运行环境django**

- **workon django: 工作在 django环境 或 从其它环境切换到 django环境**

- **deactivate**: 退出终端环境

- **其它的：**

- **rmvirtualenv** ENV：删除运行环境ENV

- **mkproject** mic：创建mic项目和运行环境mic

- **mktmpenv**：创建临时运行环境

- **lsvirtualenv**: 列出可用的运行环境

- **lssitepackages**: 列出当前环境安装了的包

  ​




### 安装Django框架

- pip install django==1.11.7

- 测试django是否已经安装好

  - 进入python shell

    ```python
    import django
    django.get_version()
    ```

- pip list 显示当前python环境中的所有的库

- pip freeze 显示当前python环境中的除系统内置库外的所有第三方库

### 创建HelloDJango项目

- 开启一个django项目 django-admin startproject day01_HelloDjango
- 测试django项目环境 python manage.py runserver
  - python manage.py runserver 0.0.0.0:8000 表示允许本机所有的IP被外网访问
  - python manage.py runserver 9000 使用本机运行，但端口是9000
- 开启自己的App
  - python manage.py startapp App



### Django的项目结构

1. manage.py
   - 管理整个项目
2. XXX/settings.py  
   - 项目配置文件
3. XXX/urls.py
   - 路由器，接收用户请求，分发给视图函数（控制器）
4. XXX/wsgi.py
   - 网关接口，通常用在线上环境部署（开发过程中不会接触）

### settings.py

1. DEBUG 是否打开DEBUG
2. ALLOWED_HOSTS 允许访问的主机
3. INSTALLED_APPS   安装了的应用 
4. DATABASES   数据库配置
5. LANGUAGE_CODE 中文 zh-hans
6. TIME_ZONE  中国 Asia/Shanghai



### Pycharm打开

1. 解压
2. 目录结构中会有  bin
3. 进入bin
4. bin 中pycharm.sh
5. 执行 ./pycharm.sh
6. 如果想在终端中的任何位置运行，那就配置到环境变量中



### 创建数据库

- 创建更改的文件
  - python manage.py makemigrations
- 将生成的py文件应用到数据库
  - python manage.py migrate
- 清空数据库
  - python manage.py flush
- 导入导出数据
  - python manage.py dumpdata appname > appname.json
  - python manage.py loaddata appname.json

### 创建视图

- 需要配置到工程的配置文件中settings中的INSTALLED_APPS
- views中定义函数，接收request，返回response
- 在urls中配置路由规则
  - 在根urls中配置（管理麻烦，配置简单）
  - 在App中创建自己的urls，在urls中书写规则，将urls配置到工程urls中
- 创建模板目录，在views返回时调用模板的渲染
- 变更数据库
  - 在settings中配置数据库信息



# Django请求流程

- 进来的请求转入/index/。
- Django 通过在 ROOT_URLCONF 配置来决定根 URLconf。
- Django 在 URLconf 中的所有 URL 模式中，查找第一个匹配 /index/ 的条目。
- 如果找到匹配，将调用相应的视图函数。
- 视图函数返回一个 HttpResponse。
- Django 转换 HttpResponse 为一个适合的 HTTP response， 以 Web page 显示出来。



# 设计一个小项目

### 需求分析

- 本示例完成“班级-学生”信息的维护，需要存储两种数据：班级、学生
- 班级表结构设计：
  - 表名：Grade
  - 班级名称：g_name
  - 班级人数：g_num
- 学生表结构设计：
  - 表名：Student
  - 学生姓名：s_name
  - 学生性别：s_gender
  - 所属班级：s_grade
- 班级-学生的关系为一对多

### 数据库配置

- 在settings.py文件中，通过DATABASES项进行数据库设置
- django支持的数据库包括：sqlite、mysql等主流数据库
- Django默认使用SQLite数据库

### 创建应用

- 在一个项目中可以创建一到多个应用，每个应用进行一种业务处理
- 创建应用的命令：

```
python manage.py startapp day1_hello_django
```

- 应用的目录结构如下图

![](/django项目目录结构.png)

### 定义模型类

- 有一个数据表，就有一个模型类与之对应
- 打开models.py文件，定义模型类
- 引入包from django.db import models
- 模型类继承自models.Model类
- **说明：不需要定义主键列，在生成时会自动添加，并且值为自动增长**
- 当输出对象时，会调用对象的str方法

```python
from django.db import models

class Grade(models.Model):
    g_name = models.CharField(max_length=20, db_column="班级名称")
    g_num = models.IntegerField(default=30)
    g_crete_date = models.DateTimeField(auto_now=True)

class Student(models.Model):
    s_name = models.CharField(max_length=20, db_column="姓名")
    s_age = models.IntegerField(default=20, db_column="年龄")
    s_sex = models.BooleanField(default=True)
    s_birthday = models.DateTimeField()
    s_grade = models.ForeignKey(Grade)

    class Meta:
        ordering = ["-s_age"]
        # 为数据库设置别名
        verbose_name = "学生表"
    	verbose_name_plural = "学生表"
        
    def _ _str_ _(self):
        return "%d" % self.pk
```

### 生成数据表

- 激活模型：编辑settings.py文件，将booktest应用加入到installed_apps中

  ![1531115052424](/注册app.png)

- 生成迁移文件：根据模型类生成sql语句

```
python manage.py makemigrations
```

- 迁移文件被生成到应用的migrations目录

![1531115146872](/迁移文件.png)

- 执行迁移：执行sql语句生成数据表

```
python manage.py migrate
```

### 测试数据操作

- 进入python shell，进行简单的模型API练习

```
python manage.py shell
```

- 进入shell后提示如下：

![](/进入django shell.png)

- 引入需要的包：

```
from App.models import Grade,Student
```

- 查询所有班级信息：

```
Grade.objects.all()
```

- 新建班级信息：

```
grade = Grade()
grade.g_name = "深圳python1805班"
grade.g_num = 40
grade.save()
```

- 查找班级信息：

```
grade = Grade.objects.get(pk=1)
```

- 输出班级信息：

```
grade
grade.id
grade.g_name
```

- 修改班级信息：

```
grade.g_name="大神班"
grade.save()
```

- 删除班级信息：

```
grade.delete()
```

### 关联对象的操作

- 对于Student可以按照上面的操作方式进行
- 添加，注意添加关联对象

```
s=Student()
s.s_name='张三'
s.s_sex=True
s.scontent='爱好打篮球'
# 注意grade为Grade的实例，上面我们已经删除了，这里需要重新创建
s.sclass=grade
s.save()
```

### 运行项目

```
python manage.py runserver ip:port
```



# 项目主要部分

### 视图

- 在django中，视图的作用是对路由转发过来的url进行处理
- 视图函数接收的第一个参数是request对象，request对象中包含了请求的信息
- 视图函数写每个app下的views.py文件中

```
from django.shortcuts import render
from django.http import HttpResponse

# Create your views here.

def index(request):
    return HttpResponse("Hello Django")
```

注意：视图函数的第一个参数必须是request，返回必须调用django的定义的方法规范。

### 路由

- 在视图函数写完后，要编写相应的url规则，这样当我们在浏览器上输入网址的时候才能转到相应的视图函数处理逻辑
- 只定义路径部分，不定义域名
- 路由函数的url部分遵循正则的书写方式
- 路由规则由两部分必须指定的参数和其他可选参数组成

```
url(r'^index/', App.index, name="index"),
```

注：每次定义完路由规则，在代码的末尾添加逗号

- 在编写路由规则之前必须导入相应的视图
- 在组织项目时，将app和项目的路由分离



### 模板

- 模板是HTML文件，通过占位符来传递视图函数的数据

- 每个app目录下都可以创建templates的文件夹，django会自动从这些app里寻找相应的模板

  

##### 定义模板

定义index.html模板文件

```
<!DOCTYPE html>
<html>
<head>
  <title>首页</title>
</head>
<body>
<h1>学生列表</h1>
<ul>
{%for student in students%}
<li>
  {{student.s_name}}
</li>
{%endfor%}
</ul>
</body>
</html>
```

定义detail.html模板

```
<!DOCTYPE html>
<html>
<head>
  <title>详情页</title>
</head>
<body>
<h1>学生详情</h1>
<ul>
<li>
  {{student.s_name}}
  {{student.s_gender}}
  {{student.s_content}}
</li>
</ul>
</body>
</html>
```

##### 使用模板

- 定义视图

```
def index(request):
    students = StudentInfo.objects.all()
    return render(request, "index.html", {"students":students})

def index_page(request, id):
    student = StudentInfo.objects.get(pk=id)
    return render(request, "detail.html", {"student":student})
```

- 定义路由

```
url(r'index/$', class_view.index, name="index"),
url(r'index/(\d+)/$', class_view.index_page, name="index_page"),
```

- 运行项目
  - python manage.py runserver
