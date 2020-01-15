> **在使用模型之前应该先创建一个项目接着创建一个应用**  
> **windows下命令如下:**  
> PS C:\Users\Administrator\Desktop\Django项目> django-admin startproject protest
PS C:\Users\Administrator\Desktop\Django项目> cd .\protest\
PS C:\Users\Administrator\Desktop\Django项目\protest> django-admin startapp apptest
PS C:\Users\Administrator\Desktop\Django项目\protest> dir
目录: C:\Users\Administrator\Desktop\Django项目\protest  
Mode                LastWriteTime         Length Name  
d-----        2020/1/13     19:57                apptest
d-----        2020/1/13     19:56                protest  
-a----        2020/1/13     19:56            648 manage.py
```python
'''
   到apptest下找到models.py 在里面创建一个模型
   实例代码
'''
from django.db import models
#Create your models here.
class person(models.Model):
	name = models.CharField(max_length=15)
	ip   = models.GenericIPAddressField()
	port = models.charField(max_length = 5)
	sex  = models.BooleanField()
```