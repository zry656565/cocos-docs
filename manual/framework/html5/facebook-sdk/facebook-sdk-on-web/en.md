#Integrate Facebook SDK Beta for Cocos2d-JS on Web

Facebook have provided its official Javascript SDK, so what's meaning of providing another one in Cocos2d-JS? It's because Cocos2d-JS is cross platform, and our mobile solution should work perfectly on Web, iOS and Android. But if you use Facebook Javascript SDK with Cocos2d-JS on Web, then when you port you game to iOS or Android, you will need to rewrite all code using Facebook API with native code. Sometimes, it's just a mission impossible.

So we provided you Facebook SDK Beta for Cocos2d-JS so that your Facebook Game can cross platform without modifing any code.

For integrating Facebook SDK Beta for Cocos2d-JS, please follow the steps below:

## 1. Integrate Facebook Javascript SDK

There are two ways for doing this:

- Developers can found all dependencies files in `frameworks/cocos2d-html5/extenrnal` folder, You can load all dependencies manually like this：
    
```
cc.loader.loadJs("", [
    "external/pluginx/platform/facebook_sdk.js",
    "external/pluginx/platform/facebook.js"
], function(){
    //do something
});
```
    
- There is another easy option, you can directly include Facebook SDK Beta module in `project.json`, the name for this module is `plugin-facebook`. In this way, the engine will load the dependency files in engine loading process, but this will extend loading time. So, the choice is yours.

## 2. Config Facebook parameters in project.json

You need to add all Facebook App related information in `project.json`:

```
{
    "module" : ["cocos2d", "extensions", "external", "plugin-facebook"],
    "plugin" : {
        “facebook”: {
            "appId" : "", // Your application id provided by Facebook
            "xfbml" : true,
            "version" : "v2.0"
        }
    }
}
```

## How to Use Facebook SDK Beta

About how to use Facebook API please reference to [Facebook SDK Beta for Cocos2d-JS](../api-reference/en.md)