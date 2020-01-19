## 公共选项
* **任何字段都可以设置的选项**  
* **null**  
	* *如果为真,django将存储空值(null)到数据库中。默认为false*  
	* *不要在基于字符串的字段上使用该字段，因为这样会导致它存在两个无意义的数据值:null和空字符串*  
	* * 
* **blank**
	* *如果为真，字段允许为空白*  
	*  *null与数据库有关,blank与表单验证有关*
* **choice**
	* *当字段设置了该选项后,字段默认的小部件会变成一个选择框*  
	* choice是一个数组,内部的元组为每一个选项,元组第一项为实际存储到数据库中的,第二项为我们看到的.(**元组的第一项要与该字段类型相同，否则无法存储**)
	* 默认情况下blank是False,所以choice中会看到-----,新增一个元组,None即可
	* ```python
	  from django.db import models  
	  
	   '''Create your models here.'''  
	   
	  Sex_Schoice=[
	  	(True:'Man'),
	  	(False:'Woman')
	  ]  
	  
	  class person(models.Model):
	  	name = models.CharField(max_length=15)
	  	ip   = models.GenericIPAddressField()
	  	port = models.CharField(max_length = 5)
	  	sex  = models.BooleanField(choices=Sex_Schoice) 
	  
	```
* **枚举类型**
	*  
* **db_column**
  * 设置该字段在数据库中列的名称,如果没有设置则使用字段名称作为数据库中的列名称  
  * **当你的字段名称为SQL保留字或python变量名中不可以使用的符号时可以使用该字段**
* **db_index** 
	如果为真，将为该字段创建索引
* **db_tablespace**
	* 当该字段的索引创建时，该属性设置它的名称  
* **default**
	* 字段的默认值,可以是一个具体的值也可以是一个可调用对象，**如果是可调用对象，那么每次创建新对象时都会调用它** 
	* **默认值不能是可变对象**
* **editable**
	* 如果为真,则该字段将不会显示在管理员或其他任何人中 ModelForm。在模型验证期间也将跳过它们。默认值为True。  
* **error_messages**
	* 覆盖该字段将引发的默认消息 **传递一个包含与您要覆盖的错误消息相匹配的键的字典。** 
	* **这些错误消息通常不会传播到表单**
* **help_text**
	* 额外的“帮助”文本将与表单窗口小部件一起显示  
* **primary_key**
	* 设置表的主键,当某个字段设置主键后也设置了 null=False和 unique=True，一个对象只允许使用一个主键  
	* 主键字段是只读的。如果更改现有对象上的主键的值然后保存，则将在旧对象的旁边创建一个新对象。
*  **unique**  
	* **如果为True，则此字段在整个表中必须是唯一的。**  
	* **当unique为is时True，您无需指定 db_index，因为这unique意味着创建了索引。**
* **unique_for_date** 
	* **前提 字段的类型为日期这一块,该字段的值不能相同** 
* **unique_for_month**  
	* **依unique_for_date类推**
* **unique_for_year**
	* **依unique_for_date类推** 
* **verbose_name**
	* 该字段的可读名称,如果未提供详细名称，则Django将使用字段的属性名称自动创建，将下划线转换为空格
* **validators**
	*  要为此字段运行的验证器列表 
## 私有选项
* **只有一些字段才可以设置的选项 例如CharField中的max_length属性**  
## 字段类型
	* **AutoField** 
		* 自动主键类型字段(**自动添加**) 
	* **BigAutoField**
		* **与AutoField一样，不过表示数的范围变大了**
	* **BigIntegerField**
		* **与IntegerField一样,不过表示数的范围变大了**
	* **BinaryField**
		* 二进制类型字段
		* **max_length(可设置)** **该字段的最大长度** 
	* **BooleanField** 
		* 布尔类型字段 
	* **CharField** 
		* 字符串字段
		* 对于大量文本，请使用TextField
		* **max_length(必设置)** **该字段的最大长度**
	* **DateField** 
		* 日期类型字段
		* auto_now(默认False) 每次保存时,时间为当前时间，可以覆盖默认值
		* auto_now_add() 每次创建时,时间为当前时间,可以覆盖默认值
		* 两个选项也可以不覆盖默认值
		* ```python
		'''DateField'''
		import datetime.date.today
		default=date.today
		'''DateTimeField'''
		import django.utils.timezone.now
		default=timezone.now
		```
	* **DateTimeField**
		* 日期时间类型字段 
	* **DecimalField**
		* 十进制数字段
		* max_digits 整个数字的最大长度 
		* decimal_places 小数位数的长度
	* **DurationField**
		* 时间段类型 存储时间段 
	* **EmailField**
		* 邮件字段 
	* **FileField**
		* 文件字段(主键不支持此字段)
		* 此属性提供了一种设置上传目录和文件名的方法，并且可以通过两种方式进行设置 
		* 如果使用默认值 FileSystemStorage，则将字符串值附加到MEDIA_ROOT路径中，以形成本地文件系统上将存储上传文件的位置
	* **FloatField**  
		* 浮点类型字段(小数类型) 
	* **ImageField**
		* 图片类型字段 
		* **height_field** 图片的高度
		* **width_field**  图片的宽度
	* **IntegerField**
		* 整数类型字段 
	* **GenericIPAddressField** 
		* 字符串格式的IPv4或IPv6地址 
		* **protocol** 指定的协议 IPv4或IPv6
		* **解压缩IPv4映射的地址**
	*  **NullBooleanField**
		* Like BooleanField with null=True. Use that instead of this field as it’s likely to be deprecated in a future version of Django.
	* **PositiveIntegerField**
		* 正整数字段
	* **PositiveSmallIntegerField**
		*  Like a PositiveIntegerField, but only allows values under a certain (database-dependent) point. Values from 0 to 32767 are safe in all databases supported by Django
	* **SlugField**  
		* Slug is a newspaper term. A slug is a short label for something, containing only letters, numbers, underscores or hyphens. They’re generally used in URLs.
	* **SmallAutoField**
		* 自动主键类型字段  范围变小
	* **SmallIntegerField**
		* 整数类型字段  范围变小 
	* **TextField** 
		* 文本类型字段 
	* **TimeField**
	 * 时间类型字段
	* **URLField**
		* url类型字段
	* **UUIDField** 
		* A field for storing universally unique identifiers. Uses Python’s UUID class. When used on PostgreSQL, this stores in a uuid datatype, otherwise in a char(32).  

## 关系字段  