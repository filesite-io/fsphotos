
# PHP递归扫描图片、视频等目录类库DirScanner使用介绍

对指定目录进行**递归遍历**，获取目录下所有子目录及其文件，是一个非常常见的需求。  

在FS相册中也用到了类似的功能，安装FS相册的时候需要指定你的照片所在目录，安装完成之后FS相册就会对设定照片目录进行递归扫描，找出里面所有的图片、视频和音乐文件，并对它们进行年份、月份归类。  

为了让更多的朋友可以更方便地实现对指定目录、指定层级深度进行递归文件扫描，我们把这部分功能做成了一个开源的PHP类库：DirScanner，下面就是它的详细使用介绍。


## 源码Github地址

DirScanner类库源码下载地址：  
[PHP DirScanner](https://github.com/filesite-io/dirscanner)

用PHP开发的朋友，如果刚好你在寻找一个能递归遍历图片、视频文件目录的功能（当然它也适用于包含任意文件格式的目录扫描），请参考上述源码里的Composer安装方法或直接下载源码使用，也欢迎大家在Github源码里反馈和交流。


## 为什么做DirScanner？

我们建立了[filesite.io](https://filesite.io)基于目录和文件管理常用的图片、视频、.md文档、.url快捷方式的标准，为了推行这个标准，于是用PHP做了一个简单的CMS系统（[filesite/machete](https://github.com/filesite-io/machete)），而DirScanner就是这个CMS系统中使用的目录递归扫描类库。


## DirScanner有什么与众不同？

DirScanner不只是实现了对指定目录递归遍历功能，为配合上述CMS系统它还做了以下几件事情：

* 实现了filesite.io，返回数据结构遵循该标准（[API data structure](https://filesite.io/#API+data+structure)）
* 按filesite.io标准把.txt文件作为其它任意的描述文件，并读取.txt文件内容返回到扫描结果中
* 扫描结果支持目录树结构数组和Dict字典结构数组两种
* 支持图片、视频exif、iptc原数据中的拍摄时间
* 所有文件都会返回它的fstat数据（参考：[PHP fstat](https://www.php.net/manual/en/function.fstat.php)）
* 可获取目录扫描结果中目录的层级关系目录树
* 可替换.md文档解析后内容中的链接（含图片、A链接）相对路径为CMS系统网址
* 可获取.md文档中所有标题
* 可返回支持Nginx的SecureLink防盗链url


## DirScanner适用场景

理论上DirScanner可以用来扫描包含任意类型文件的目录，但如果你要做的刚好是以下场景之一，我们会觉得它非常适合你：

* 递归扫描包含.md Markdown文章的目录
* 递归扫描包含常见格式（.jpg, .png, .gif等）图片的目录
* 递归扫描包含.mp4、.mov、.m3u8和.ts格式视频的目录
* 递归扫描包含.mp3格式音乐的目录
* 递归扫描包含.url快捷方式的目录


特别说明：  
**DirScanner不适合扫描.txt格式文件目录**。  
由于filesite.io的标准定义，.txt文件会被看作其它文件的说明文件，并不会在扫描结果中返回。


## 二次开发交流

如果你在使用DirScanner二次开发中遇到任何问题，欢迎交流、讨论。  
联系方式请打开官方网站查看底部QQ群和微信：
<a href="https://filesite.io" target="_blank">FileSite.io</a>