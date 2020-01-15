> ***1.创建好模型后还需要安装应用,在setting中找到 INSTALLED_APPS列表，在里面添加你的应用名
2.找到DATABASES将内容改为如下***
``` python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'zxlts',# NAME为数据库名 看自己在Mysql中创建的数据库叫什么
        'USER':'root',
        'PASSWORD':'root',
        'HOST':'',
        'PORT':'',
    }
}
```
在mysql中创建一个数据库
**create database zxlts**  
执行命令  
PS C:\Users\Administrator\Desktop\Django项目\protest> **python manage.py makemigrations**  
Migrations for 'apptest':
  apptest\migrations\0001_initial.py
    \- Create model person
	
PS C:\Users\Administrator\Desktop\Django项目\protest> **python manage.py migrate**  
Operations to perform:
  Apply all migrations: admin, apptest, auth, contenttypes, sessions  
  Running migrations:  
  Applying contenttypes.0001_initial... OK  
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying admin.0003_logentry_add_action_flag_choices... OK
  Applying apptest.0001_initial... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying auth.0010_alter_group_name_max_length... OK
  Applying auth.0011_update_proxy_permissions... OK
  Applying sessions.0001_initial... OK  
  **出现以上提示则没有问题**