Create A Plugin
---

### Get Ready

Enable `Develop Mode` before creating any plugin.


> Tips: Right-click and then click icon of Plugin Store, which should be able to reload plugin store quickly.

![][img_create_1]

`Developer's repositories` panel, with plugins in the development should show up after enable `developer mode`.


### Create `myphpinfo` plugin

#### Basic Function Analysis

This plugin is ment to show users about `phpinfo()`. The steps are as follows:

1. User chooses the shell(type: `PHP`) which is going to load.
2. User chooses `myphpinfo` from the plugins.
3. Send `phpinfo()` code to the server
4. Return result of `phpinfo()` back to AntSword
5. this plugin should show the result to the user.

#### Create Basic File

1. Go to the directory especially for developers, which is already setted before, create a new directory named `myphpinfo` and step into it.
2. Create a `README.md` for description.
3. Create a `package.json` for initialization. The content is as followed:

 ```
{
  "name": "phpinfo 信息查看",
  "name_en": "myphpinfo",
  "main": "main.js",
  "icon": "rocket",
  "version": "0.1",
  "description": "我的第一个插件，查看 phpinfo 信息",
  "description_en": "this is my first plugin, which can show phpinfo",
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
 
 Details:

  - Entrance File: `main.js`
  - `icon`, find a awesome icon, such as [rocket](http://fontawesome.io/icon/rocket/)
  - `miltiple` : `false` . This means that this cannot handle multiple shells at a same time.
  - `scripts` : `php`
 
 > You can find what other fields mean in [last section](./source_files.md)
 
4. Entrance File: `main.js`: 

	```
	'use strict';
	
	class Plugin {
		constructor(opt) {
		// coding here
		}
	}
	module.exports = Plugin;
	```
	
 > the name of `main.js` isn't fixed, which means you may use names you love in `package.json`.

---

**Here the directory tree looks like: **

```
plugins-dev
	|
	└── myphpinfo
	    ├── README.md
	    ├── main.js
	    └── package.json
```

You should be able to see that plugin named `myphpinfo` we just created under `developer's repository` in the `Plugin Store`.

![][img_create_2]

> However, this plugin can do nothing. Let's start coding (:>

#### Coding

Before coding, you may want to know about [`opt`](./api.md) that core of AntSword sends to the plugin.

We need to create a tabbar to show results. Let's set its title as `phpinfo()`

```
const tabbar = require('ui/tabbar');

let t = new tabbar();
t.setTitle('phpinfo()');
t.showLoading();
```

Ant then, instantiate the plugin: 

```
let core = new antSword['core'][opt['type']](opt);
```
One thing to be noted is that `opt['type']` means the current type of webshell. In this situation, its value is `php`.

> It is extremely convenient to create webshell dynamically in ths way if the type is more than just one.

After instantiation, we need to send `phpinfo()` code to webshell in the server. In order to let remote webshell execute codes you send and get results, let's write these:

```
core.request({
	_: 'phpinfo();'
}).then((_ret) => {
	t.safeHTML(_ret['text']).showLoading(false);
}).catch((e) => {
	t.close();
});
```

Use `core.request` method to send data. Its key value is `_` with content `phpinfo()l`.
the value of `_` is encoded by encoder automatically. This feature is extremely helpful to get intercepted if your code is huuugggggeeee. (:?


If we can get results, we will output results to the tabbar. 
Or, shut it down if failed.

This lovely plugin should do the job right now. But not very user-friendly.
To make it more friendly, we choose to inform users the status at the bottom right. So we use `toastr` object to do this.

** The Final Code: **

```
'use strict';

const tabbar = require('ui/tabbar');

class Plugin {
  constructor(opt) {
    // create Ui
    let t = new tabbar();
    t.setTitle('myphpinfo()');
    t.showLoading();
    // instantiate PHP Shell
    let core = new antSword['core'][opt['type']](opt);

	// Send request to the webshell
    core.request({
      _: 'phpinfo()'
    }).then((_ret) => {
      t.safeHTML(_ret['text']).showLoading(false);
      toastr.success('Totally Successful！', 'Success');
    }).catch((e) => {
      toastr.error(JSON.stringify(e), 'Error');
      t.close();
    });
  }
}

module.exports = Plugin;

```

### Testing

Let's get testing. Remember to restart AntSword.

> Click `Debug` => `Restart APP`

![][img_create_3]

Of course, you can do this with `Developer Tool` under `Debug`.
Go to `console`, and use `antSword["logs"]` to check out the HTTP packet: 

![][img_create_4]

You may find out difference while using different encoders.

> Next sectioin: Debuging tricks.

[img_create_1]: http://as.xuanbo.cc/doc/plugin_dev/create_1.png
[img_create_2]: http://as.xuanbo.cc/doc/plugin_dev/create_2.png
[img_create_3]: http://7tigg.com1.z0.glb.clouddn.com/doc/plugin_dev/create_3.png
[img_create_4]: http://as.xuanbo.cc/doc/plugin_dev/create_4.png
