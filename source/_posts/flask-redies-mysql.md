---
title: flask+redies+mysql
date: 2019-03-21 23:30:26
tags:
---
# flask+ redis 问题


#### 链接redis 时候出现SQLALCHEMY_TRACK_MODIFICATIONS报错
> 回退版本 Flask_sqlalchey  2.2 >> 2.1
```
`track_modifications = app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] 报错，需要进行flask的sqlalchemy版本进行回退操作语句 pip install Flask-SQLAlchemy==2.1  `
```


#### flask 连接数据库

  setting.py  配置
```
DIALECT = 'mysql'
    DRIVER = 'pymysql'
    USERNAME = 'root'
    PASSWORD = '123456'
    HOST = '127.0.0.1'
    PORT = '3306'
    DATABASE = 'cms'
 
    SQLALCHEMY_DATABASE_URI = '{}+{}://{}:{}@{}:{}/{}?charset=utf8'.format(
        DIALECT,DRIVER,USERNAME,PASSWORD,HOST,PORT,DATABASE
    )
    SQLALCHEMY_COMMIT_ON_TEARDOWN = True
    SQLALCHEMY_TRACK_MODIFICATIONS = True

```

manage.py  连接数据库

```
from flask_sqlalchemy import SQLAlchemy
db = SQLAlchemy(app)

```


models.py  创建表
```
from manage import db
 
class User(db.Model):
    pass
 
class CodeCountRecord(db.Model):
   pass
 
```

#### 数据迁移  Django 也有这个migrate 还不用下载 美滋滋
>  pip安装flask-script , flask-migrate





modle.py 对于表的操作流程（在一个文件中是这样）.

```
from flask import Flask
from flask_script import Manager
from flask_sqlalchemy import SQLAlchemy
from flask_migrate import Migrate,MigrateCommand

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:////opt/db.sqlite' #使用sqlite3数据库
db = SQLAlchemy(app)  #ORM

migrate = Migrate(app,db)
manager = Manager(app)
manager.add_comman('db',MigrateCommand) #添加db 命令（runserver的用法）

#一个用户表
class User(db.Model):
...
...
省略

if __name__ == '__main__':
    manager.run()

```
 
在命令行界面 运行如下代码

```
python main.py db init  #创建数据表。并且会在你项目下生成migrations/目录，保存你数据库每次变更的内容。


python main.py db migrate #提交修改

python main.py db upgrade #执行修改 

再看User表，已经改变。 
python main.py db downgrade #回退修改
```


## 使用flask迁移数据库,二次创建表问题

> 那么只需在模型类里面添加语句
`table_args = {"extend_existing": True}`


-----
### 参考博客
[二次建表](https://www.jianshu.com/p/0028df446b54)
[数据库连接+迁移](https://www.cnblogs.com/wxiaoyu/p/9526673.html)
[数据连库接+迁移2](https://blog.csdn.net/baidu_35085676/article/details/78079120)
[使用falsk_SQLAlchemy连接MySQL](https://www.cnblogs.com/6324TV/p/9203838.html)
[flask报错 KeyError 'SQLALCHEMY_TRACK_MODIFICATIONS'.md (还是回退版本好用~)](https://www.cnblogs.com/String-Lee/p/10061675.html)