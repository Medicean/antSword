加载插件
---

> 插件只有安装到本地后才可以被调用，在使用前请确保插件安装成功。

插件有两种调用方式，分别为「单个调用」和「批量调用」

#### 单个调用

进入Shell管理界面，选择要加载插件的Shell，单击鼠标「右键」，选择「加载插件」菜单，并选择要加载的插件

![][img_load_plugin_1]

注意：在加载插件时需要确保插件所支持的 Shell 类型(具体类型请前往插件市场下的本地仓库查看)是否与当前 Shell 所属类型相同。

**例如：**

> phpinfo 插件仅支持 PHP 类 Shell，如果在 ASP 类 Shell 下加载时，菜单会变为不可点击状态。

#### 多个调用

在 Shell 管理界面，按住`Shift`键或者`Ctrl`键(OSX下为`Command`键)，选中需要加载插件的Shell。然后单击鼠标「右键」，选择「加载插件」菜单，并选择要加载的插件。

注意：批量调用时，需要确保该插件`支持批量调用`，并且所选择所有Shell类型都被该插件支持。只有两个条件同时满足，才可调用。


#### 调用结果

在加载插件后，根据具体的插件显示不同的结果。

**例如：**

##### phpinfo 插件

不需要额外输入，直接打开新的选项卡，显示目标主机的phpinfo信息

![][img_load_plugin_2]

##### PortScan 插件

在调用后，需要手动配置一些参数，然后返回结果

![][img_load_plugin_3]

![][img_load_plugin_4]


[img_load_plugin_1]: http://as.xuanbo.cc/doc/plugins/load_plugin_1.jpg
[img_load_plugin_2]: http://as.xuanbo.cc/doc/plugins/load_plugin_2.jpg
[img_load_plugin_3]: http://as.xuanbo.cc/doc/plugins/load_plugin_3.jpg
[img_load_plugin_4]: http://as.xuanbo.cc/doc/plugins/load_plugin_4.jpg
