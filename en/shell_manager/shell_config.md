Shell Config
---

AntSword pursues the `free, flexible, highly extendible` config of shells, which can make shells more powerful and colorful.

#### Basic Config

The basic config of shells includes basic information only. Connectivity of shell can encounter errors if you has wrong config.

![][img_shell_config_1]

* **URL**

 Every network package will be sent to this URL.

* **Password**

 This means password to webshell you want to connect.

* **Encoder Setting**

 You will get messy codes if encoder isn't chosen correctly.

 > Under Windows7
 >
 > Character encoding is `GBK` for `cmd`(only for Chinese users). `ANSI` is used by some files. However some source files could be edited by using `UTF-8`
 >
 > If you have **messy characters**, please solve it according the table below:


  Shell Character encoding | Windows XP/7/8/Server 2003 Chinese Version| Windows 10 Chinese Version| *nix 
  :-:|:-:|:-:|:-:
  ASP | GBK | - | -
  ASPX | UTF8 | UTF8 | -
  PHP | GBK(Terminal)/UTF8(File Management) | UTF8 | UTF8
  CUSTOM: JSP | UTF8 | UTF8 | UTF8

  > Korean（Euc-KR），Japanese（Euc-JP or Shift_JIS）

 **Notice: ** You have to clear cache manually after chaning the encoder.

* **Interpreter Categories**

 You can choose `PHP`, `ASP`, `ASPX`, `CUSTOM`.

 > If you choose use `CUSTOM`, please make sure that the server can interpret your scripts. Reference ==> [HERE](https://github.com/AntSwordProject/AntSword/tree/master/shells)

 Users can write your own shells. More details.[Develop Custom Webshells](../core_dev/shell/custom_shells.md)

* **Encoder**

 Encoders are one of main cores of AntSword, which can be used to encryption of connectivity between AntSword and server webshells.

 > You may get an amazing advantage when you are trying to connect to servers behind firewalls.

 * default

   This will transfer plain data without using any encoders. **HIGHLY NOT RECOMMENDED.** Special characters will get escaped, which may result in errors.

 * random

   AntSword will pick up encoders randomly to connect.

 * base64

   AntSword will use base64 to encode. **HIGHLY NOT RECOMMENDED.** This feature has already been marked by WAF.

 * **chr**

   AntSword will use `chr` function in PHP to communicate. (Only in PHP). **RECOMMENDED**

 * **hex**

   AntSword will transform data into hex to communicate in `ASPX` and `CUSTOME`. **RECOMMENDED**

 * **xxxxdog**

   Examples of cutomizeable encoder: (ONLY IN ASP) you have to use it with [asp_eval_xxxxdog.asp](https://github.com/AntSwordProject/AntSword/tree/master/shells/asp_eval_xxxxdog.asp). **RECOMMENDED**

   You may use classical cryptography, DES, AES or others to transfer data. Please see more details in [Encoder Development](../core_dev/encoder/README.md)

#### HTTP Setting

 Sometimes you may want to customize HTTP headers, such as Cookie, User-Agent and etc. or just adding some specific data into your POST. At this time you need 「HTTP Setting」.

![][img_shell_config_2]

* HTTP HEADERS

 This section is about filling in value for HTTP.

 > Eg:  `User-Agent` ==> `AntSword 2.0 dev`
 > 
 > Name ==>  `User-Agent`
 >
 > Value ==> `AntSword 2.0 dev`

 If more than one value is needed in HTTP header, please add 「[+]Header」.

* HTTP BODY

 This section is config for HTTP body. `Name` for Key in POST. `Value` for value of Key.

 > Eg: `mypass` ==> `antsword`
 > 
 > Name ==> `mypass`
 >
 > Value ==> `antsword`

 If more than one value is needed in HTTP body, please add 「[+]Body」.


#### Other Settings

![][img_shell_config_3]

* **Ignore HTTPS Certificate**

Communication will fail if certificates in server is not trusted or expired. You should open this up to ignore check of HTTPS.

* **Cache For Terminal**

 The result won't be saved to cache by default when using terminal.You can set this up to make sure cache will be cached if your Connectivity is poor.

 Cache will be used directly if commands you are going to execute. (**NOT RECOMMEND TO OPEN**)

* **Timeout**

 Set up the timeout for HTTP. The unit is `ms`. `10000ms` is setted by default. Please customize according to your own network situation.

* **Customize path of executing the terminal**

 The default path for terminal is: `/bin/sh` and `cmd`. Please set up according to your own situation. `Absolute path` is RECOMMENDED.

[img_shell_config_1]: http://as.xuanbo.cc/doc/shell_manager/shell_config_1.jpg
[img_shell_config_2]: http://as.xuanbo.cc/doc/shell_manager/shell_config_2.jpg
[img_shell_config_3]: http://as.xuanbo.cc/doc/shell_manager/shell_config_3.jpg
