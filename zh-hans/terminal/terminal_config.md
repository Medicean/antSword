虚拟终端配置
---

#### 自定义终端执行路径

默认情况下，虚拟终端执行路径如下：

操作系统 | 终端执行路径
:-:|:-:
Linux | `/bin/sh`
Windows | `cmd`

如果需要自定义虚拟终端执行路径，请编辑当前Shell的配置。在「Shell配置」窗口中的「其它设置」选项卡下，在「自定义终端执行路径」处填写执行的路径（例如：`/bin/bash`、`C:\\cmd.exe`）

![][img_main_page_1]

#### 缓存配置

默认情况下，虚拟终端**不使用**缓存，如果网络状况不良，可勾选「虚拟终端使用缓存」

[img_main_page_1]: http://as.xuanbo.cc/doc/terminal/terminal_config_1.png

#### 本地命令

* `ashelp`

 显示本地指命令帮助菜单

* `aslistcmd`

 列出可使用的命令解释器

* `ascmd [file]`

 指定file来作为命令解释器, 仅在当前虚拟终端下生效。例如: `ascmd /bin/bash` , `ascmd d:/mycmd.exe`

 > AntSword >= 2.0.7 版本, 可指定 Powershell 作为命令解释器

 `ascmd c:/windows/system32/windowspowershell/v1.0/powershell.exe`

 如果`ascmd`命令指定的PowerShell解释器文件名中包函`powershell`关键字, 会自动启用 PowerShell 模式。如果不包含 `powershell` 关键字，则需要使用 `aspowershell` 指令手动开启或关闭 PowerShell 模式

* `aspowershell [on|off]`

 启用/关闭 PowerShell 模式。

 > 如果`ascmd`命令指定的PowerShell解释器文件名中包函`powershell`关键字, 会自动启用 PowerShell 模式, 如下图:

![aspowershell_default](https://i.loli.net/2019/04/05/5ca753673efe7.png)

 > 如果指定的 PowerShell 解释器文件名中不包含 `powershell` 关键字, 则需要手动使用该命令，启用 PowerShell 模式。如果关闭了 PowerShell 模式,则会执行出错，如下图:

![aspowershell_switch](https://i.loli.net/2019/04/05/5ca75368d85fa.png)

* `quit`

 关闭终端

* `exit`

 关闭终端

#### 快捷键

快捷键 | 效果
:-:|:-:
`Ctrl =` | 放大字体
`Ctrl -` | 缩小字体
`Ctrl L` |   清屏
`Ctrl U` |清除当前行
