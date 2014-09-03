Cocos Code IDE入门指南
=========================

简介
----------
你可以通过[这篇文章](../zh.md)了解 Cocos Code IDE 的功能。

下载 Cocos Code IDE
----------
### 下载哪个版本的IDE(Windows用户)
在控制台中输入下面的命令来检查安装的java版本:

`java -version`

如果已经安装过java, 你可以从控制台的输出中知道java版本是 **32-Bit** 或者 **64-Bit**, 然后选择相应版本的IDE。

### 下载

| 平台        | 充分测试版本 | 下载地址 |
| ----------- |:--------------:| ----------------------:|
| Mac OS X      | 10.9 		| [Mac OS X 64][mac ide link] 
| Windows       | Win7/Win8     | [Windows x86 64Bit(.zip)][windows ide 64 zip link], [Windows x86 64Bit(.exe)][windows ide 64 exe link], [Windows x86 32Bit(.zip)][windows ide 32 zip link],[Windows x86 32Bit(.exe)][windows ide 32 exe link]|

如何安装
------------

### 基本需求

+ 安装 [JDK][JDK link]，windows用户要下载合适的jdk版本，例如，X64的jdk对于64位版本的Cocos IDE。
+ 安装 [Python 2.7][Python link]。
+ 开发 Cocos2d-x Lua binding 游戏请下载 [Cocos2d-x 3.2][engine download link]
+ 开发 Cocos2d-x JavaScript binding 游戏请下载 [Cocos2d-js 3.0 rc2][engine download link]

	**Note:**
	+ **Cocos Code IDE(1.0.0-rc1)是基于Cocos2d-x 3.x/Cocos2d-js 3.x的引擎版本做的开发，其他版本的引擎在该版本的IDE上可能无法正常工作。当前IDE的版本(1.0.0-rc1)适用于最新的引擎版本(Cocos2d-x 3.2 rc1 和 Cocos2d-js 3.0 rc1)，并且向后兼容3.x的老版本引擎，所以为了更好的体验和使用IDE的新特性，请下载相应版本的引擎。**
	
	+ **引擎和所创建的工程所在的路径都不能包含非英文字符，即路径中不能包含中文。**
	
### 额外需求

* 如果要在 iOS Simulator 上调试，需要

    保证你的 Mac 上安装了 iOS Simulator

* 如果你要在 android 设备上调试，需要

    安装 [android sdk][Android SDK link]

* 如果你想要定制自己的 runtime，你需要：

	| 目标平台      | 工具 |
	| ------------- |:----------------------------:|
	| Mac OS X/iOS      | XCode 5.0或以上版本 		|
	| Windows       | VS2012 |
	| Android       | [Android SDK][Android SDK link], [NDK(**r9d版本**)][NDK link], [ANT][ANT link] |
	
已有的 Cocos2d 项目如何使用 Code IDE开发
----------

如果你的项目正在使用 cocos2d-x/cocos2d-js 3.x 引擎进行开发，现在可以很容易的切换到 Cocos Code IDE，你需要做的只是：

* 通过 IDE 创建一个对应的 Cocos Lua/JavaScript 示例工程
* 用项目资源（脚本、图片等）替换掉示例工程中的资源

如何使用
----------

+ [使用Code IDE调试Cocos2d-x Lua游戏](../debug-lua/zh.md)
+ [使用Code IDE调试Cocos2d-x JavaScript游戏](../debug-js/zh.md)

[JDK link]: http://www.oracle.com/technetwork/java/javase/downloads/index.html
[Android SDK link]: https://developer.android.com/sdk/index.html?hl=sk
[NDK link]: https://developer.android.com/tools/sdk/ndk/
[ANT link]: http://ant.apache.org/
[Python link]: http://www.python.org/download
[engine download link]: http://cn.cocos2d-x.org/download
[mac ide link]: http://www.cocos2d-x.org/filedown/cocos-code-ide-mac64-1.0.0-rc1.dmg
[windows ide 64 zip link]: http://www.cocos2d-x.org/filedown/cocos-code-ide-win64-1.0.0-rc1.zip
[windows ide 32 zip link]: http://www.cocos2d-x.org/filedown/cocos-code-ide-win32-1.0.0-rc1.zip
[windows ide 64 exe link]: http://www.cocos2d-x.org/filedown/cocos-code-ide-win64-1.0.0-rc1.exe
[windows ide 32 exe link]: http://www.cocos2d-x.org/filedown/cocos-code-ide-win32-1.0.0-rc1.exe
