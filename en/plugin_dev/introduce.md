Plugins Introduction
---

In order to make plugins as clear as possible, this section will introduce you to how it works behind AntSword and how to develop one.

### Development of Concept

「Plugins」** is only able to communicate with shells.**


### How it works

Here is a work flow of how the plugins work.(`PortScan` is taken as an example).

![][img_introduce_1]

Comments：

1. The flow is ordered by time from top to button.
2. Just omit `step 4` and `step 5` if there's no need to interactive with users, such as a plugin named `phpinfo`.
3. UI is created on `Step 4`. However you can choose any UI as you like. `dhtmlx` is RECOMMENDED to keep the same UI style.
4. `Step 7` and `step 8` is about HTTP request and response. If you do it all the time if you have to.
5. The communication between the core and plugins could be template code, such as `phpinfo`, or operation on webshells(such as `CopyShell`)

[img_introduce_1]: http://as.xuanbo.cc/doc/plugin_dev/introduce_1.png
