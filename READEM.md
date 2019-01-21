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




#### 补充说明 在此处写命令 更方便
pycharm -- Tools -- run manage.py Task
(Alt + r)