** 字段，就像数据库中的列。模型中最重要的一部分(字段名不能与Django中的模型接口名一样) **

``` python
from django.db import models
#Create your models here.
class person(models.Model):
	name = models.CharField(max_length=15)
	ip   = models.GenericIPAddressField()
	port = models.charField(max_length = 5)
	sex  = models.BooleanField()
```
** name ip port sex都是 person 中字段(表单字段会有一个默认的HTML部件) **
** Django供了几十种字段类型，我们也可以创建自己的字段类型 **