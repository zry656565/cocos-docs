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
工程配置初始化字段

####"isLandscape"####
横竖屏配置，如果为true为横屏，如果为false为竖屏

####"name"####
工程名

####"width"####
窗口宽

**注:只在桌面系统下生效**

####"height"####
窗口高

**注:只在桌面系统下生效**

####"entry"####
"src/main.lua" //入口文件

---
##simulator_screen_size##
配置多种分辨率大小，可以自己添加或者删减

**注:只在桌面系统下生效**

####"title"####
"iPhone 3Gs (480x320)", 菜单标题

####"width"####
480 宽分辨率

####"height"####
320 高分辨率


---