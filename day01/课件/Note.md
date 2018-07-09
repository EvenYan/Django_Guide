# 自我介绍

### 姓名：严燚坤

### 联系方式：2495894421

### 工作经历：

多年开发经验，先后在NVIDIA，蛮蛮云计算从事Python开发。





# Django是啥

Django特点

- 重量型的框架
  - 代码量很高
  - 提高大部分的插件和接口
  - 笨重
    - 丧失了灵活性
    - 自定义程度不高
- 一款web后端框架
  - 产生数据
  - 控制逻辑



LTS：long term support

# 开发环境

Ubuntu 16.04 + Python3  + Django 1.11.7 + PyCharm



# Ubuntu系统和命令介绍

### 系统设置



### 常用命令

- apt/apt-get   安装软件的命令
  - apt install XXX
  - apt remove
  - apt autoremove
  - apt update
- cat
- vi/vim
- ifconfig
- netstat -anp
- grep 
  - grep -v 反向筛选

# Python虚拟环境配置



### pip是python包管理工具

- pip list
- pip install django==1.11.7  安装django1.11.7
- pip uninstall django      卸载django
- pip freeze
  - pip freeze > requirements.txt  将Python中的第三方库写入到requirements.txt文件中
- pip install -r requirements.txt       安装requirements.txt文件中的所有第三方库
- pip uninstall  XXX    卸载XXX



### 虚拟环境常用命令

- mkvirtualenv XXX
- workon XXX
- deactivate
- rmvirtualenv



# Pycharm的安装使用

- 进入到压缩文件的同级目录
- tar -zxvf pycharm-professional-2018.1.2.tar.gz
- cd pycharm-2018.1.2/bin
- ./pycharm.sh



# Django版本选择

思考：Why not django2



# 第一个Django程序

- workon django

- django-admin startproject XXX  创建了XXX项目

- 进入到项目目录

  - cd XXX

- python manage.py runerver  运行开发服务器

  - 默认情况下项目运行在8000端口
  - python manage.py runserver 8080   项目运行在8080端口
  - python manage.py runserver 0.0.0.0:8000

- 进入项目目录

- python manage.py startapp App   创建属于自己的应用

- 在settings.py文件中注册app

  - INSTALLED_APP = [

    'App',

    ]

- 编写App/views.py

  - ```python
    from django.http import HttpResponse
    
    def index(request):
    	return HttpResponse("Hello")
    ```

- 添加路由

  - ```
        url(r'^index/$', views.index, name='index'),
    ```

- 进入项目根目录

  - python manage.py runserver

注意：

- Alt + Enter 万能键
- 在用pycharm打开项目的之前配置python解释起





# django目录结构

- 项目的同名目录：day01_Hello

  - \__init__.py  将目录初始化为Python包
  - settints.py  项目的配置文件
  - urls.py    路由文件

  

### 设计一个小项目

学生表Student

- 学生的名字:s_name
- 学生的性别:s_sex
- 学生的年龄:s_age
- 学生的班级:s_grade

班级表Grade

- 班级名称:g_name
- 班级的人数:g_num

ORM:把Python代码翻译成SQL语句



### 创建表

在models.py文件中定义表结构

```python
from django.db import models

# Create your models here.


class Grade(models.Model):
    g_name = models.CharField(max_length=40)
    g_num = models.IntegerField(default=40)
```



- python manage.py makemigrations
  - 生成数据库迁移文件
- python manage.py migrate
  - 生成数据库表



### 定义views.py函数

- render()
  - 第一个参数是request, 第二个参数template_name, 第三个参数是context

### 新建template：html

- for循环

```
{% for student in students %}
{% endfor %}
```

- 变量的渲染

```
{{ student.s_name }}
```

### 添加urls.py记录

```
urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^index/$', views.index),
    url(r'^getstudent/$', views.get_student),
    url(r'^getgrade/$', views.get_grade),
]
```



# BS/CS

### C/S

C: client(王者荣耀)

S: Server（王者荣耀的服务器）

### B/S

B: Broswer (浏览器)

S: Server (web服务器--Django后端)

# HTTP请求流程

http://127.0.0.1:8000/index/   --->   Django  ----> urls.py(仅仅匹配index) --->  views.py(index函数) ---> 返回给浏览器



# MVC/MVT设计思想

### Django中MVT设计思想

M: model  数据库模型

V: views    处理逻辑

T: template   前端模板



### MVC 设计思想

M: model  数据模型

V: 试图，展示层，相当于django中的template

C: control  控制器，相当于django中的view



