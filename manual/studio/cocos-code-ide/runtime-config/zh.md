工程的config.json文件说明
===
---
每一个新建的工程根目录下都有一个config.json文件，这个文件用于工程配置初始化，在程序运行之前配置好。

config.json文件结构
===
---
以下是config.json的文件内容，包含每一个节点元素节点及其属性，

	{
	
    "init_cfg":{
       "isLandscape": true,
       "name": "HelloLua",
       "width": 960,
       "height": 640,
       "entry": "src/main.lua"
    },
    "simulator_screen_size": [
        {
            "title": "iPhone 3Gs (480x320)",
            "width": 480,
            "height": 320
        },
        {
            "title": "iPhone 4 (960x640)",
            "width": 960,
            "height": 640
        },
        ....
    ]
	}
---	
##"init_cfg"##

####"isLandscape"####
布尔类型

横竖屏配置，如果为true为横屏，如果为false为竖屏

####"name"####
字符串类型

工程名,显示在窗口标题中

####"width"####
浮点类型

窗口宽

**注:这个参数只在桌面系统下生效**

####"height"####
浮点类型

窗口高

**注:这个参数只在桌面系统下生效**

####"entry"####
字符串类型

"src/main.lua" 

脚本启动入口文件

---
##simulator_screen_size##
配置多种分辨率大小，可以自己添加或者删减，显示在runtime的view菜单中

**注:这个字段只在桌面系统下生效**

####"title"####
字符串类型

"iPhone 3Gs (480x320)", 菜单标题

####"width"####
浮点类型

480 宽分辨率

####"height"####
浮点类型

320 高分辨率


---