Cocos Code IDE入门指南
=========================

下载 Cocos Code IDE
----------
### 下载哪个版本的IDE(Windows用户)
在控制台中输入下面的命令来检查安装的java版本:

`java -version`

如果已经安装过java, 你可以从控制台的输出中知道java版本是 **32-Bit** 或者 **64-Bit**, 然后选择相应版本的IDE。

### Cocos2d-x 3.1 补丁包
Cocos2d-x 3.1 的 lua-template-runtime/runtime/win32/PrebuiltRuntimeLua.exe 存在无法输出日志的bug，请下载并解压[此文件](http://cdn.cocos2d-x.org/cocos2dx-3.1-templates.zip)到指定目录。

### Cocos2d-js 3.0 rc0 hotfix
当前已经发布的 Cocos2d-js 3.0 rc0 版本支持 Cocos Code IDE 1.0.0-rc0，但这个版本的引擎在Windows上工作路径比较长时无法正常创建工程，为了提高 Cocos Code IDE 的体验，Cocos2d-js 3.0 团队临时提供了一个基于 Cocos2d-js 3.0 rc0 的 hotfix 版本。我们建议所有 Windows 用户[下载此版本][js engine download link]。

### 下载

| 平台        | 充分测试版本 | 下载地址 |
| ----------- |:--------------:| ----------------------:|
| Mac OS X      | 10.9 		| [Mac OS X 64][mac ide link] 
| Windows       | Win7/Win8     | [Windows x86 64Bit][windows ide 64 link], [Windows x86 32Bit][windows ide 32 link]|

如何安装
------------

### 基本需求

+ 安装 [JDK][JDK link]，windows用户要下载合适的jdk版本，例如，X64的jdk对于64位版本的Cocos IDE。
+ 安装 [Python 2.7][Python link]。
+ 开发 Cocos2d-x Lua binding 游戏请下载 [Cocos2d-x 3.2][lua engine download link]
+ 开发 Cocos2d-x JavaScript binding 游戏请下载 [Cocos2d-js 3.0 rc0 hotfix][js engine download link]

	**Note : **
	
	+ **Cocos Code IDE(1.0.0-rc0)是基于Cocos2d-x 3.x/Cocos2d-js 3.x的引擎版本做的开发，其他版本的引擎在该版本的IDE上可能无法正常工作。当前IDE的版本(1.0.0-rc0)适用于最新的引擎版本(Cocos2d-x 3.2 rc0 和 Cocos2d-js 3.0 rc0)，并且向后兼容3.x的老版本引擎，所以为了更好的体验和使用IDE的新特性，请下载相应版本的引擎。**
	
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
[lua engine download link]: http://www.cocos2d-x.org/download
[js engine download link]: http://www.cocos2d-x.org/filedown/cocos2d-js-v3.0-rc0-hotfix.zip
[mac ide link]: http://www.cocos2d-x.org/filedown/cocos-code-ide-mac64-1.0.0-rc0.zip
[windows ide 64 link]: http://www.cocos2d-x.org/filedown/cocos-code-ide-win64-1.0.0-rc0.zip
[windows ide 32 link]: http://www.cocos2d-x.org/filedown/cocos-code-ide-win32-1.0.0-rc0.zip
