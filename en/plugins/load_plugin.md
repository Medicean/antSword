Load Plugins
---

> Plugins can only be used after installation. Please make sure that it do get installed before you use.

The mode of loading plugins: `Single` and `Batching`

#### Single

After entering the shell management interface, choose one of shells you want to load plugins. And 「`Right Click`」, find 「`Load Plugins`」 and choose plugins you want to load.

![][img_load_plugin_1]

Notice: Please make sure that the plugins that supports which type of shells do matches the current Shell. For example, you can't use `ASP scripts` while your shell is `PHP scripts`. The type of webshell can be found in details of local repo.

**Another Example：**

> `phpinfo` plugin only support PHP-shell. ASP server won't be able to resolve that script.


#### Batching

Press `Shift` or `Ctrl`(`command` under OSX) and select the shell you want to load plugins. Then 「`right click`」 and select the plugins you want to load.

Notice: Please make sure that the plugins itself support being called batching, and the current shell has same type of plugins.


#### Results of Be Loaded

The results of plugins varies from plugins after being loaded.

**Anthor Example：**

##### phpinfo plugin

No need to input anything. Just open new tab to get the results of `phpinfo`.

![][img_load_plugin_2]

##### PortScan plugin

After being loaded, you need to customize some arguments manually, just like Metasploit. Then you get what you want.

![][img_load_plugin_3]

![][img_load_plugin_4]


[img_load_plugin_1]: http://as.xuanbo.cc/doc/plugins/load_plugin_1.jpg
[img_load_plugin_2]: http://as.xuanbo.cc/doc/plugins/load_plugin_2.jpg
[img_load_plugin_3]: http://as.xuanbo.cc/doc/plugins/load_plugin_3.jpg
[img_load_plugin_4]: http://as.xuanbo.cc/doc/plugins/load_plugin_4.jpg
