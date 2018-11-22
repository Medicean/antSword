主界面
---

进入蚁剑主程序后，默认程序主界面为「Shell 管理」。左侧为「数据管理」，也就是「Shell 列表」；右侧为「分类管理」。在数据管理区任意位置单击鼠标右键即可弹出菜单。

![][img_main_page_1]

#### 数据管理

以列表形式展现 Shell。单击鼠标左键可选中该 Shell，选中该 Shell 后，可单击鼠标右键呼出弹出菜单，或可直接双击该 Shell 进入「文件管理」模块。

#### 分类管理

详见[Shell管理 - 分类管理](./category.md)

#### 弹出菜单

* **虚拟终端**

 进入[虚拟终端](../terminal/README.md)模块，选中 Shell

* **文件管理**

 进入[文件管理](../file_manager/README.md)模块，管理选中 Shell 文件

* **数据管理**

 进入[数据管理](../file_manager/README.md)模块，管理选中 Shell 数据库

* **浏览网站**

 直接访问该 Shell，并将服务端设置的 Cookie 保存到该 Shell 配置中

 > 对于需要登录才能访问的 Shell(例如放在admin目录下)，可在管理之前，使用「浏览网站」功能，输入认证口令，将此次认证成功的 Cookie 保存至当前 Shell 配置当中。

* **加载插件**

 对当前选中的 Shell 加载插件。详见[加载插件](../plugins/load_plugin.md)

* **插件市场**

 进入「[插件市场](../plugin_store/README.md)」，管理并获取插件

* **添加数据**

 添加一条新 Shell 数据

* **编辑数据**

 修改当前选中 Shell 的配置文件

* **删除数据**

 删除当前选中 Shell，支持同时删除多条数据

* **移动数据**

 移动当前选中的 Shell 到指定的分类目录下

* **清空缓存**

 清空当前选中 Shell 的本地缓存

 > 修改配置之后，不会自动清空缓存，需要根据实际使用场景，手动清空缓存

* **清空所有缓存**

 清空本地所有缓存


[img_main_page_1]: http://as.xuanbo.cc/doc/shell_manager/main_page_1.jpg