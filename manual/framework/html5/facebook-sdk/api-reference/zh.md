#Facebook SDK Beta for Cocos2d-JS API Reference

##集成Facebook SDK Beta

开始使用Facebook SDK Beta for Cocos2d-JS之前，你可能需要集成这个SDK到你的个人项目中。首先请使用Cocos Console创建一个新的个人项目，然后参考不同平台的集成指南将Facebook SDK Beta for Cocos2d-JS集成到你的项目中：

- [Cocos Console使用文档](http://www.cocos2d-x.org/docs/manual/framework/html5/v2/cocos-console/zh)
- [Android平台上如何集成Facebook SDK Beta for Cocos2d-JS](../facebook-sdk-on-android/zh.md)
- [iOS平台上如何集成Facebook SDK Beta for Cocos2d-JS](../facebook-sdk-on-ios/zh.md)
- [Web平台上如何集成Facebook SDK Beta for Cocos2d-JS](../facebook-sdk-on-web/zh.md)

##Facebook SDK Beta API列表

###1. FacebookAgent类

FacebookAgent类包装了所有Facebook SDK Beta的API，在Cocos2d-JS中使用Facebook SDK Beta，需要首先获得这个类的实例：

```
var facebook = plugin.FacebookAgent.getInstance();
```

###2. User APIs

- **.login(callback)**

	让用户登录到Facebook，一些操作要求用户必须登录，比如申请权限，获取Access Token，Open Graph API调用等

	参数和返回值:
	
	- **callback**:	接收登录结果的回调函数，如果errorCode等于plugin.FacebookAgent.CodeSucceed，那么表示函数调用成功,开发者可以在message中获取到登录结果的Json对象<br/>
	    type:	function(errorCode, message)    
	- return:	无
	
- **.logout(callback)**
    
	从Facebook登出用户。

	参数和返回值:
	- **callback**:	接收登出结果的回调函数，如果errorCode等于plugin.FacebookAgent.CodeSucceed，那么表示函数调用成功<br/>
	    type:	function(errorCode, message)
	- return:	无

- **.isLoggedIn(callback)**
    
	检测用户是否已经登录Facebook

	参数和返回值:
	
	- **callback**:	接收结果的回调函数，如果errorCode等于plugin.FacebookAgent.CodeSucceed，那么表示函数调用成功，开发者可以从message中取得返回消息或Json对象<br/>
	    type:	function(errorCode, message)
	- return:	无
	
- **.requestAccessToken(callback)**

	获取用来访问Open Graph API的access token，用户必须首先登录

	参数和返回值:
    - **callback**: 接收结果的回调函数，如果errorCode等于plugin.FacebookAgent.CodeSucceed，那么表示函数回调成功，开发者可以从message中得到返回消息或者Json对象<br/>
    type: function(errorCode,message)
	- **return**:	无

- **.requestPermissions(permissions, callback)**

	向Facebook请求用户权限，想要访问Open Graph API你的应用必须拥有相应的用户访问权限

	参数和返回值:

	- **permissions**:	需要的权限列表，用数组存放例如：["manage_pages", "publish_actions"]<br/>
	    type:	Array
	- **callback**:	接收结果的回调函数，如果errorCode等于plugin.FacebookAgent.CodeSucceed，那么表示函数调用成功，开发者可以从message中取得返回消息或Json字符串<br/>
	    type:	function(errorCode, message)
	- return:	无

###3. Share APIs

- **.share(info, callback)**

	分享一条消息到你的Facebook，在iOS或Android平台，如果设备上已经安装有Facebook应用，这个函数会自动打开对应的应用以完成分享过程。如果设备上没有安装需要的应用，Cocos2d-JS会尝试打开内建Web View以完成分享。否则将会返回失败

	参数和返回值:

	- **info**:	分享的内容<br/>
	    type:	Object
	- **callback**:	接收结果的回调函数，如果errorCode等于plugin.FacebookAgent.CodeSucceed，那么表示函数调用成功，开发者可以从message中取得返回消息或Json对象<br/>
	    type:	function(errorCode, message)
	- return:	无

	参数细节:

	- **info**参数示例:

	```
	{
		"description": "Cocos2d-x is a great game engine",
		"title": "Cocos2d-x",
		"link": "http://www.cocos2d-x.org",
		"imageUrl": "http://files.cocos2d-x.org/images/orgsite/logo.png"
	}
	```

	- **info**参数详解:
		1. description: 链接描述
		2. title:       链接名称
		3. link:        链接地址
		4. imageUrl:    链接描述图片

- **.dialog(info, callback)**

	分享一条消息到你的Facebook或与你的朋友分享一条消息，在iOS或Android平台，如果设备上已经安装有Facebook应用或Facebook Messenger应用，这个函数会自动打开对应的应用以完成分享过程。如果设备上没有安装需要的应用，Cocos2d-JS会尝试打开内建Web View以完成分享。否则将会返回失败

	参数和返回值:

	- **info**:	分享的内容<br/>
	    type:	Object
	- **callback**:	接收结果的回调函数，如果errorCode等于plugin.FacebookAgent.CodeSucceed，那么表示函数调用成功，开发者可以从message中取得返回消息或Json对象<br/>
	    type:	function(errorCode, message)
	- return:	无

	参数细节:

	- **info**参数示例:

	```
	{
		// dialog代表分享的类型
		"dialog": "share_link",
		"description": "Cocos2d-x is a great game engine",
		"title": "Cocos2d-x",
		"link": "http://www.cocos2d-x.org",
		"imageUrl": "http://files.cocos2d-x.org/images/orgsite/logo.png"
	}
	```
        
	- **dialog**类型:

		1. share_link:		用Facebook应用分享一个链接到Facebook
		2. share_open_graph:	用Facebook应用分享一个Open Graph对象到Facebook
		3. share_photo:		用Facebook应用分享一张图片
		4. message_link:	用Facebook Messenger应用发送一个链接给朋友
		5. share_open_graph:	用Facebook Messenger应用发送一个Open Graph对象给朋友
		6. share_photo:		用Facebook Messenger应用发送一张图片给朋友
        
	- Link内容的参数:

		1. description: 链接描述
		2. title:       链接名称
		3. link:        链接地址
		4. imageUrl:    链接描述图片

	- Open Graph内容的参数:

		1. action_type:         Open Graph Action类型
		2. preview_property:    Open Graph Object名称
		3. other parameters:    其他该action所指定的参数
        
	- Photo内容的参数:

		1. photo:   要分享的图片地址

###4. Open Graph APIs

- **.request(path, method, params, callback)**

	发送一个Open Graph API请求，关于Open Graph的更详细信息，请参考[Facebook官方Open Graph文档](https://developers.facebook.com/docs/opengraph)

	参数和返回值:

	- **path**:	Open Graph API接口路径<br/>
	    type:	Object
	- **method**:	HTTP请求方法<br/>
	    type:	Number<br/>

	可选值:
	
	```
	plugin.FacebookAgent.HttpMethod.Get
	plugin.FacebookAgent.HttpMethod.Post
	plugin.FacebookAgent.HttpMethod.Delete
	```

	- **params**:	请求的参数，参数可能会根据开发者调用的接口有很大差别，请参考[Graph API Reference文档](https://developers.facebook.com/docs/graph-api/reference/)<br/>
	    type:	Object
	- **callback**:	接收结果的回调函数，如果errorCode等于plugin.FacebookAgent.CodeSucceed，那么表示函数调用成功，开发者可以从message中取得返回消息或Json对象<br/>
	    type:	function(errorCode, message)
	- return:	无
	
###5. Payments APIs [Beta特性，即将发布]
    
- **.pay(params, callback)**

    发起一条支付请求，关于支付更详细的信息，请参考[Facebook官方Payments文档](https://developers.facebook.com/docs/payments/local-currency-payments-guide)
    
    参数和返回值:
    
    - **params**:   请求所包含的参数，该参数根据不同的支付请求会有比较大的差别，请参考[Facebook Pay Dialog文档](https://developers.facebook.com/docs/payments/reference/paydialog#properties)<br />
        type:   Object
    - **callback**:	接收结果的回调函数，如果errorCode等于plugin.FacebookAgent.CodeSucceed，那么表示函数调用成功，开发者可以从message中取得返回消息或Json字符串<br/>
        type:	function(errorCode, message)<br />
        关于成功后的message回传的参数，请参考[Pay Dialog Return Data](https://developers.facebook.com/docs/payments/reference/paydialog#return-data)
    - return:    无
    
    参数细节:
    
    - **params**参数详解:
    
    ```
        1. product       : 用户即将购买的产品对象URL. 
        2. quantity      : [可选]用户即将购买的金额。
        3. quantity_min  : [可选]用户购买的最低数量。
        4. quantity_max  : [可选]用户购买的最高数量。
        5. request_id    : [可选]开发人员定义的交易唯一标识符。
        6. pricepoint_id : [可选]用于设置快捷的移动支付流程。
        7. test_currency : [可选]此参数可调试和测试你的执行力的对话框。
    ```
    
    需要注意的是，支付功能只支持web端。并且只能够在Facebook Canvas应用中测试流程，如果你在开发过程中碰到error 1151，请尝试部署你的游戏到Facebook Canvas应用中测试，因为支付API必须要使用Facebook链接才能生效。

###6. AppEvent APIs [Beta特性，即将发布]

- **.publishInstall()**

	向Facebook发送一个安装消息。

	参数和返回值:

	- return:	none

- **.logEvent(eventName, valueToSum, parameters)**

	记录一个app事件，参数是事件名，累加的值，和一组参数。

	参数和返回值:
	
	- **eventName** 事件名<br/>
		类型: String <br/>
		可选值:

	    ```
	    plugin.FacebookAgent.AppEvent.ACTIVATED_APP
		plugin.FacebookAgent.AppEvent.COMPLETED_REGISTRATION
		plugin.FacebookAgent.AppEvent.VIEWED_CONTENT
		plugin.FacebookAgent.AppEvent.SEARCHED
		plugin.FacebookAgent.AppEvent.RATED
		plugin.FacebookAgent.AppEvent.COMPLETED_TUTORIAL
		plugin.FacebookAgent.AppEvent.ADDED_TO_CART
		plugin.FacebookAgent.AppEvent.ADDED_TO_WISHLIST
		plugin.FacebookAgent.AppEvent.INITIATED_CHECKOUT
		plugin.FacebookAgent.AppEvent.ADDED_PAYMENT_INFO
		plugin.FacebookAgent.AppEvent.PURCHASED
		plugin.FacebookAgent.AppEvent.ACHIEVED_LEVEL
		plugin.FacebookAgent.AppEvent.UNLOCKED_ACHIEVEMENT
		plugin.FacebookAgent.AppEvent.SPENT_CREDITS
	    ```
	- **valueToSum** (optional) 一个和事件相关联的的数值，会在Insights累加来计算平均值。<br/>
		type: Number
	- **parameters** (optional) 事件的参数<br/>
		类型: Object <br/>
		可选的参数名:
		
		```
		plugin.FacebookAgent.AppEventParam.CURRENCY
		plugin.FacebookAgent.AppEventParam.REGISTRATION_METHOD
		plugin.FacebookAgent.AppEventParam.CONTENT_TYPE
		plugin.FacebookAgent.AppEventParam.CONTENT_ID
		plugin.FacebookAgent.AppEventParam.SEARCH_STRING
		plugin.FacebookAgent.AppEventParam.SUCCESS
		plugin.FacebookAgent.AppEventParam.MAX_RATING_VALUE
		plugin.FacebookAgent.AppEventParam.PAYMENT_INFO_AVAILABLE
		plugin.FacebookAgent.AppEventParam.NUM_ITEMS
		plugin.FacebookAgent.AppEventParam.DESCRIPTION
		```
	- return: none

##Facebook SDK Beta跨平台特性

|API|Feature|iOS|Android|Web|
|:-:|:-----:|:-:|:-----:|:-:|
|login|Login to Facebook|√|√|√|
|logout|Logout from Facebook|√|√|√|
|isLoggedIn|Check whether user is logged in|√|√|√|
|getAccessToken|Retrieve access token for the current session|√|√|√|
|requestPermissions|Request user permission for open graph API|√|√|√|
|share|Share a simple message on user's Facebook page|√|√|√|
|dialog - share_link|Share a link with Facebook built in dialog|√|√|√|
|dialog - share_open_graph|Share a open graph story with Facebook built in dialog|√|√|√|
|dialog - share_photo|Share a photo with Facebook built in dialog|√|√|×|
|dialog - message_link|Send a link with Facebook built in messenger dialog|√|√|√|
|dialog - message_open_graph|Send a open graph story with Facebook built in messenger dialog|√|√|×|
|dialog - message_photo|Send a photo with Facebook built in messenger dialog|√|√|×|
|dialog - apprequests|Send a app request with Facebook built in dialog|√|√|√|
|request|Request a open graph API|√|√|√|
|publishInstall|Send an install message to Facebook|√|√|×|
|payments|Send an pay request|×|×|√|
|logEvent|Log an app event|√|√|×|

##Facebook SDK Beta使用示例 (based on Cocos2d-JS v3.0 RC2) 

```
// 获取插件
var facebook = plugin.FacebookAgent.getInstance();

// 检查是否已登录
// errCode: 0 已登录， 1 登陆失败， 2 已登出
// msg: 插件返回的信息
facebook.isLoggedIn(function(errCode, msg){
    if(errCode == plugin.FacebookAgent.CodeSucceed){  //已登录
    	cc.log(JSON.stringify(msg));
    }else{  //未登陆
		//登陆，回调的参数同上
        facebook.login(function(errCode, msg){
        });
    }
}); 

// 登出
facebook.logout(function(errorCode,message){
});

// 请求高级权限，第一个参数是权限的数组，第二个参数是回调
var permissions = ["create_event", "create_note"];
facebook.requestPermissions(permissions, function(errCode, msg){
});

// 获取AccessToken
facebook.requestAccessToken(function(errCode, token){
    if(errCode == plugin.FacebookAgent.CodeSucceed)
    	cc.log("AccessToken : " + JSON.stringify(token));
});

// 分享，会打开Facebook app的ui
var info = {
    "description": "Cocos2d-x is a great game engine",
    "title": "Cocos2d-x",
    "link": "http://www.cocos2d-x.org",
    "imageUrl": "http://files.cocos2d-x.org/images/orgsite/logo.png"
};
facebook.share(info, function (errCode, result) {
    cc.log(JSON.stringify(result));
});


// 打开Facebook的share, message, reqeust对话框，一共7种，
// 有些需要安装Facebook app，如果没安装会自动以webview的形式打开
var info = {
    "dialog": "share_photo", // 分享一张本地图片
    "photo": imgpath // 图片路径，可配合cocos的截屏功能使用
};
facebook.dialog(info, function (errCode, result) {
	cc.log(JSON.stringify(result));
});

// 使用Facebook OpenGraph api，相当于Facebook js sdk中的FB.api(),参数形式也是一样的
facebook.request("/me", plugin.FacebookAgent.HttpMethod.Get, {}, function(errCode, result){
    // msg目前还是字符串形式，request api返回的实际是一个json字符串，里面包含具体信息，需要手动解析
    if(errCode == plugin.FacebookAgent.CodeSucceed) {
        cc.log("User ID : " + response["id"]);
    }
});

// 销毁插件
plugin.FacebookAgent.destroyInstance();
```
