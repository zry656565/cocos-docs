#Web平台上如何集成Facebook SDK Beta for Cocos2d-JS

Web端除了直接使用Facebook提供的Javascript SDK外，Cocos2d-JS也提供了Facebook SDK Beta for Cocos2d-JS插件。
使用Cocos2d-JS的Facebook SDK Beta可以使你的游戏无缝的衔接Android以及iOS平台，你的所有Facebook功能模块可以不修改一行代码就直接运行，使得一份代码能够完整的运行在不同的平台之上。

那么Web端怎么使用Facebook SDK Beta for Cocos2d-JS呢？

## 1. 首先页面要先引入Facebook SDK Beta

可以有两种方式引入Facebook SDK Beta的依赖：

- 开发者可以在`frameworks/cocos2d-html5/extenrnal`文件夹下找到所有的Facebook SDK Beta的依赖文件，使用下面的代码完成手动加载Facebook SDK Beta（注意JS文件顺序）：

```
cc.loader.loadJs("", [
    "external/pluginx/platform/facebook_sdk.js",
    "external/pluginx/platform/facebook.js"
], function(){
    //do something
});
```

- 或者也直接在project.json文件内modules字段里增加`plugin-facebook`，引擎将会自动加载文件，但是这样可能会造成游戏初始化速度变慢，大家根据自己实际情况做取舍吧。

## 2. 加载完成之后，还必须要配置Facebook传入的参数

还是在`project.json`文件内增加plugin字段：

```
{
    "module" : ["cocos2d", "extensions", "external", "plugin-facebook"],
    "plugin" : {
        “facebook”: {
            "appId" : "", // Facebook提供的应用id
            "xfbml" : true,
            "version" : "v2.0"
        }
    }
}
```

## 3. 如何使用Facebook SDK Beta

关于如何使用Facebook API 请参考 [Facebook SDK Beta for Cocos2d-JS](../api-reference/zh.md)