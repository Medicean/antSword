获取蚁剑
---

> 仅适用 AntSword >=v2.0.0

##### 1.下载蚁剑加载器

从 v2.0.0-beta 版本开始，我们引入了加载器这一概念。用户/开发者只需要下载对应平台的加载器，无需安装额外的环境，即可对源代码进行编辑/执行/调试等操作。可直接运行当前最新的开发版和发行版源代码。

[点此获取加载器](https://github.com/AntSwordProject/AntSword-Loader)

**注意**：官方加载器仅在 `https://github.com/AntSwordProject/AntSword-Loader` 发布，不会在网盘等其它网站发布，下载后请第一时间校验 md5 值

##### 2. 下载蚁剑源代码并加载

首次打开加载器时，界面如下图所示：

![首次打开加载器][img_get_antsword_1]

点击「`初始化`」按钮，选择一个空目录作为蚁剑的工作目录，加载器会自动下载源代码。待提示初始化完毕时，重新打开蚁剑加载器，即可看到蚁剑的主界面。

![主界面][img_get_antsword_2]

当然了，如果你之前已经有了蚁剑源代码，你可以在这一步选择工作目录的时候，直接选择该目录作为工作目录。


> 你是否还沉浸在愉悦的安装过程中？很遗憾，一切皆已完成。：）


### 可能遇到的问题

##### Q: 下载或者解压出错

##### A: 遇到这种问题，按照下面步骤手动进行：

1. 手动 clone antsword 源代码, 或者直接点[这里下载源代码](https://github.com/AntSwordProject/AntSword/archive/master.zip)并解压

 ```
$ git clone https://github.com/AntSwordProject/AntSword.git
 ```

2. 打开加载器，选择源代码所在目录(简单理解为 app.js 所在目录)。

 例如app.js路径为：`D:\\test\antsword\app.js`，那么选择的目录主是 `D:\\test\antsword\`

 **特别提醒，不要中文路径**


[img_get_antsword_1]: http://7xtigg.com1.z0.glb.clouddn.com/doc/getting_started/get_antsword_1.jpg
[img_get_antsword_2]: http://7xtigg.com1.z0.glb.clouddn.com/doc/getting_started/get_antsword_2.jpg