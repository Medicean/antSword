数据库管理配置
---

由于Shell类型不同、数据库系统不同，导致数据库管理时配置形式多种多样。AntSword数据库管理会根据不同的Shell类型和数据库类型自动生成相应的表单。所以下文将会对不同类型的Shell的配置进行说明。


#### PHP 类型配置

![][img_main_page_1]

* **数据库类型**

 选择要管理的数据库类型。对于 MySQL 数据库，选择时依据如下：
 
 * MySQL (PHP < 5.5.0)
 * MYSQLI(PHP >= 5.2.9)

* **数据库编码**

 连接数据库时使用的编码方式，连接 MySQL 数据库时使用，其它数据库连接时直接在连接字符串中指定

* **数据库地址**

 数据库服务器地址，默认为 localhost 即 Shell 所在的服务器

* **连接用户**

 数据库用户名

* **连接密码**

#### ASP/ASPX 类型配置

![][img_main_page_2]

* **数据库类型**

 选择要管理的数据库类型

* **连接字符串**

 直接使用连接字符串连接数据库，在连接字符串中指定连接时需要的用户等信息

 > 一般情况下只需修改默认连接字符串模版即可，如果出现使用不了的情况，请查阅 ASP／ASPX 连接数据库相关文档


#### Custom 类型配置

![][img_main_page_3]

* **数据库类型**

 选择要管理的数据库类型

 > 如果要管理的数据库不在列表中，随便选一个即可

* **连接字符串**

 直接使用连接字符串连接数据库，在连接字符串中指定连接时需要的用户等信息

 > 根据具体所使用的 CUSTOM Shell 中的说明文档来配置

##### 范例1

以 [AntSword JSP Custom Script for Mysql](https://github.com/AntSwordProject/AntSword/blob/master/shells/jsp_custom_script_for_mysql.jsp)这个 Shell 为例，第 18 行说明了该 Shell 的数据库连接字符串：

```
com.mysql.jdbc.Driver
jdbc:mysql://localhost/test?user=root&password=123456
```

> 第一行指定连接时加载的驱动，第二行为连接字符串

##### 范例2

以[AntSword PHP Custom Script for Mysql](https://github.com/AntSwordProject/AntSword/blob/master/shells/php_custom_script_for_mysql.php)为例，第 19 行说明了该 Shell 的数据库连接字符串：

```
<H>localhost</H>
<U>root</U>
<P>123456</P>
```

> <H> 标记中库服务器地址，<U>为用户名，<P>为连接密码

可见 CUSTOM 类型 Shell 在连接时的高度自由，开发者可根据个人喜好，随意定制连接字符串

[img_main_page_1]: http://as.xuanbo.cc/doc/database/database_config_1.png
[img_main_page_2]: http://as.xuanbo.cc/doc/database/database_config_2.png
[img_main_page_3]: http://as.xuanbo.cc/doc/database/database_config_3.png
