语言模版开发
---

蚁剑默认支持的语言为「中文简体」和「English」，本小节将以实例形式，带你开发「台湾-繁体中文」语言模版

> 当然, 你也可以根据个人喜好，开发出「方言版」


1.首先需要进入语言文件所在目录

```
$ cd source/language/
```

在这里,你会看到下面3个文件:

```
.
├── en.js     // English 语言模版文件
├── index.js  // 语言模块入口文件
└── zh.js     // 中文简体 语言模版文件
```

2.我们复制 `en.js` 或者 `zh.js`, 将其命名为 `zh_tw.js`

```
$ cp zh.js zh_tw.js
```

3.接着，编辑 `zh_tw.js`, 保持结构不变, 只修改字符串, 如下所示:

```
//
// language::zh_tw
//
module.exports = {
  title: '中國蟻劍',
  toastr: {
    info: '提示',
    error: '錯誤',
    warning: '警告',
    success: '成功'
  },
  menubar: {
    main: {
      title: 'AntSword',
      about: '關於程序',
      pluginStore: '插件市場',
      settings: '系統設置',
      language: '語言設置',
      encoders: '編碼設置',
      aproxy: '代理設置',
      display: '顯示設置',
      update: '檢查更新',
      quit: '退出程序'
    },

    ... 以下部分省略
```

4.打开语言模块入口文件 `index.js`

在 languages 里加入我们刚刚创建的语言模版文件, 然后保存:

```
const languages = {
  'en': 'English',
  'zh': '简体中文',
  'zh_tw': '繁體中文(台灣)'
}
```

> 注: `zh_tw` 是文件名, `繁體中文(台灣)` 是我们在设置界面中想显示的文字

5.重启蚁剑,在「语言设置」中就可以看到刚刚创建的语言文件啦

![][img_coredev_language_1]

[img_coredev_language_1]: http://as.xuanbo.cc/doc/core_dev/language/language_1.png
