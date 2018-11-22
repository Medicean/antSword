创建插件
---

### 准备工作

创建插件前需要先打开「开发者模式」

进入「插件中心」，选择「设置中心」面板，打开「开发者模式」，设置好插件开发目录后，点击「保存」按钮。下次进入插件中心后会生效。

> Tips: 鼠标「右键」点击「插件中心的图标」可快速重新加载插件中心

![][img_create_1]

开启开发者模式后，插件中心会多出「开发仓库」面板，在这里可看到开发仓库中的插件。

### 创建 myphpinfo 插件

#### 插件功能分析

这个插件是用来向用户展示 Shell 的 phpinfo 信息的，流程如下：

1. 用户选择要加载插件的 Shell（类型为 PHP）
2. 用户从加载插件列表中选择`myphpinfo`插件
3. 向服务器发送查看`phpinfo`信息代码
4. 返回`phpinfo`信息给插件
5. 插件向用户展示`phpinfo`信息

#### 创建基本目录结构

1. 打开插件开发目录（在准备工作中已经设置），新建目录 `myphpinfo`,然后进入该目录
2. 新建 `README.md` 文件，用于详细说明该插件
3. 新建 `package.json` 文件，用于格式化插件信息，内容如下：

 ```
{
  "name": "phpinfo 信息查看",
  "name_en": "myphpinfo",
  "main": "main.js",
  "icon": "rocket",
  "version": "0.1",
  "description": "我的第一个插件，查看 phpinfo 信息",
  "description_en": "show phpinfo",
  "author": {
    "name": "Medici.Yan",
    "email": "Medici.Yan@gmail.com"
  },
  "category": "信息获取",
  "category_en": "Infomation",
  "multiple": false,
  "scripts": ["php"]
} 

 ```
 
 说明：

  * 入口脚本为 `main.js`，下面我们会创建这个文件 
  * `icon`, 选个帅气的火箭 [rocket](http://fontawesome.io/icon/rocket/)
  * `miltiple` 的值为 `false`, 不支持同时处理多个 Shell，我们只查看一个Shell的就够了
  * `scripts` 的值仅支持 `php` 这一个类型
 
 > 具体其它字段含义请参考上一小节「[插件源文件说明](./source_files.md)」
 
4. 创建入口脚本 `main.js`，内容如下：

	```
	'use strict';
	
	class Plugin {
		constructor(opt) {
		// 这里是代码
		}
	}
	module.exports = Plugin;
	```
 > 文件名`main.js`是由`package.json`中的 `script`的值指定的

---

**现在整个目录树是这个样子**：

```
plugins-dev
	|
	└── myphpinfo
	    ├── README.md
	    ├── main.js
	    └── package.json
```

进入「插件中心」，此时可以看到「开发仓库」面板下已经出现了我们刚刚创建的 `myphpinfo`插件，见下图：

![][img_create_2]

> 不过此时这个插件没有任何功能，下面我们来编写代码实现功能。

#### 编写功能代码

在编写功能代码之前，你可以先了解一下核心框架向插件传入的参数`opt`的格式:「[插件参数](./api.md)」

我们需要创建一个 tabbar 来将最终结果显示出来，设置它的 title 为 `phpinfo()`

```
const tabbar = require('ui/tabbar');

let t = new tabbar();
t.setTitle('phpinfo()');
t.showLoading();
```

接着，实例化传入的 Shell:

```
let core = new antSword['core'][opt['type']](opt);
```
值得注意的是 opt['type']表示的是当前Shell的类型，在这个插件里等于 `php`

> 如果该插件支付的类型不只是一种的话，使用这种方法动态创建Shell就极为方便了

实例化完毕之后，我们需要向 Shell 发送 `phpinfo();` 这段代码，让 Shell 执行并返回结果：

```
core.request({
	_: 'phpinfo();'
}).then((_ret) => {
	t.safeHTML(_ret['text']).showLoading(false);
}).catch((e) => {
	t.close();
});
```

使用 core.request 方法发送数据，键值为 `_`，内容为`phpinfo();`。`_`的值会自动经过编码器加密处理，如果代码量大的情况下，可以防止被截

处理结果时，如果返回成功，我们就把结果输出到 tabbar,如果失败，就把创建的 tabbar 关闭掉

此时该插件已经可以正常工作了，但是还不够友好，我们需要在成功时在右下角提示信息处提示返回成功，失败时提示失败并打出错误信息，那么就可以用`toastr`这个全局通知对象来实现。

**最终完成代码如下**：

```
'use strict';

const tabbar = require('ui/tabbar');

class Plugin {
  constructor(opt) {
    // 创建UI
    let t = new tabbar();
    t.setTitle('myphpinfo()');
    t.showLoading();
    // 实例化PHP Shell
    let core = new antSword['core'][opt['type']](opt);

	// 向Shell发起请求
    core.request({
      _: 'phpinfo()'
    }).then((_ret) => {
      t.safeHTML(_ret['text']).showLoading(false);
      toastr.success('获取成功！', 'Success');
    }).catch((e) => {
      toastr.error(JSON.stringify(e), 'Error');
      t.close();
    });
  }
}

module.exports = Plugin;

```

### 测试插件

编写完代码后，重启蚁剑，随便找一个 PHP 类型的 Shell 进行测试：

> 点击菜单栏「调试」菜单下的「重启应用」可快速重启

![][img_create_3]

当然，此时你也可以点击菜单栏「调试」菜单下的「开发者工具」，打开开发者工具，在 `Console`下输入：`antSword["logs"]`来查看刚刚的插件发送的数据包：

![][img_create_4]

可以看到 data 部分发送了 `phpinfo();` 到服务端，可以尝试更换编码器打印 log 观察 data 的不同之处

> 关于调试的技巧将在下一小节中讲

[img_create_1]: http://as.xuanbo.cc/doc/plugin_dev/create_1.png
[img_create_2]: http://as.xuanbo.cc/doc/plugin_dev/create_2.png
[img_create_3]: http://as.xuanbo.cc/doc/plugin_dev/create_3.png
[img_create_4]: http://as.xuanbo.cc/doc/plugin_dev/create_4.png