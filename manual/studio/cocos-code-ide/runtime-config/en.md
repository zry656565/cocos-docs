Instructions of project's config.json file
===
---
Every new project have a "config.json" file in its root directory.The file presents essential information about your game project,complete config before it run.
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
Screen orientation,if true orientation is "landscape" else is "portrait"

####"name"####
project name

####"width"####
window's width

**Note:valid only in desktop system**

####"height"####
window's height

**Note:valid only in desktop system**

####"entry"####
"src/main.lua":  entry script file

---
##simulator_screen_size##
Configure multiple resolution size, you can add or delete item by yourself

**Note:valid only in desktop system**

####"title"####
"iPhone 3Gs (480x320)", menu tile

####"width"####
480  resolution of width

####"height"####
320 resolution of height


---