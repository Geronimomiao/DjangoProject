# START
#### pip3 install django

### 项目可以外网访问
看到生成的地址是127.0.0.1:8000这样的话，我们在外网就无法访问了

解决:
修改启动命令
setting.py 设置 允许外部 ip 访问

    `python manage.py runserver 0.0.0.0:8000`
    `ALLOWED_HOSTS = ['*']`