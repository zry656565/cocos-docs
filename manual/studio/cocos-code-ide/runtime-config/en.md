Instructions of project root directory config.json file
===
---
The file presents essential information about your game project,complete config before it run.
Structure of the config.json file
===
---
The below shows the general structure of the config.json file and every element that it can contain.Each element,along with all of its attributes,is documented in full in a separate file.

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
bool

Screen orientation,if true，orientation is "landscape" else is "portrait"

####"entry"####
string

"src/main.lua" entry script file

####"name"####
string

project name，show at window's tile

**Note:This argument valid only in desktop system**
####"width"####
unsigned int

window's width

**Note:This argument valid only in desktop system**

####"height"####
unsigned int

window's height

**Note:This argument valid only in desktop system**



---
##simulator_screen_size##
Configure multiple resolution size, you can add or delete item by yourself，those items show in runtime view’s menu

**Note:This section valid only in desktop system**

####"title"####
string

menu tile. such as: "iPhone 3Gs (480x320)", 

####"width"####
unsigned int

window's width

####"height"####
unsigned int

window's height


---