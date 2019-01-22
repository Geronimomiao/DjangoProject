# START
#### pip3 install django

### 目录结构
templates --- html
static --- js css img
log --- log日志
apps --- 存放各种 app
media --- 存放用户上传文件

tips: 可将 apps mark 成 source root 引包方便 
在 setting.py 改 base_dir 否则命令行运行回报错  
tips: 在 setting.py TEMPLATE DIRS 修改 模版目录

### 项目可以外网访问
看到生成的地址是127.0.0.1:8000这样的话，我们在外网就无法访问了

解决:
修改启动命令
setting.py 设置 允许外部 ip 访问

    `python3 manage.py runserver 0.0.0.0:8000`
    `ALLOWED_HOSTS = ['*']`





### 启动 app
    `python3 manage.py startapp name`







### 数据库配置

setting.py 下 DATABASES 处设置
注意对应的数据库 要下对应的驱动 
如: mysql ---- pip3 install mysql-python 
[安装失败解决方法](https://blog.csdn.net/qq_19175749/article/details/79838218)

#### models.py (设计数据模型)
tips: 在 settings.py INSTALLED_APPS 注册app
生成表名 appname_ModelClassName(转为小写)
models 为我们提供了多种类型 (CharField ForeignKey DateTimeField ImageField FileField IntegerField EmailField IPAddressField ...)
若不指定主键 models 会自动生成 id 字段 作为主键

#### 数据 crud
在 views 将 models.py 定义的 models 引进来

###### 增
* user_message = UserMessage()
* user_message.name = 'test' (将类实例化即可)
* user_message.save()
###### 删
* all_messages = UserMessage.objects.all()
* all_messages.delete()
###### 改
###### 查
* UserMessage.objects.all() (查询该表所有数据，返回对象 可用 for 进行迭代)
* UserMessage.objects.filter(name='wsm', address='TianJin') （条件查询）

### 路由配置

url.py  
在对应 app 的 view.py 下写函数 并引进了

对路由设置 name 来绑定
{% url 'goform' %}


### templates
有许多内置函数
`{% if not my_message.name == 'wsm' %} wsm {% else %} WSMWSM {% endif %}`
传值 在 views.py 下传
` return render(request, 'message_form.html',{
        "my_message": message
    })`


#### 静态文件 404
setting.py
```
STATIC_URL = '/static/'
STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static')]
```

#### 补充说明 在此处写命令 更方便
pycharm -- Tools -- run manage.py Task
(Alt + r)
##### 一些基本命令
makemigrations appname (先在 settings.py INSTALLED_APPS 注册app)
migrate appname(链接数据库 生成一些默认表)
