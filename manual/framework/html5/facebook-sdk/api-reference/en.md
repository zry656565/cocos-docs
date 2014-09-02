#Facebook SDK Beta for Cocos2d-JS API Reference

##Getting start

Before using Facebook SDK Beta, you may need to integrate Facebook SDK Beta for Cocos2d-JS in your project. Firstly, please use Cocos Console to create a new project, then follow these documents for the integration:

- [Cocos Console usage document](http://www.cocos2d-x.org/docs/manual/framework/html5/v2/cocos-console/en)
- [Integrate the Facebook SDK Beta for Cocos2d-JS on Android](../facebook-sdk-on-android/en.md)
- [Integrate the Facebook SDK Beta for Cocos2d-JS on iOS](../facebook-sdk-on-ios/en.md)
- [Integrate the Facebook SDK Beta for Cocos2d-JS on Web](../facebook-sdk-on-web/en.md)

##API list

###1. FacebookAgent class

FacebookAgent is a singleton class which encapsulated all APIs of Facebook SDK Beta for Cocos2d-JS, if you want to use it, you need to retrieve its instance firstly:

```
var facebook = plugin.FacebookAgent.getInstance();
```

###2. User APIs

- **.login(callback)**

	Login user to Facebook, some APIs require user to login, like .getAccessToken, .request.

	Parameters and return value:

	- **callback**:	Callback for receiving the result, if errorCode equals plugin.FacebookAgent.CodeSucceed, then the function call is returned successfully, if errorCode equals plugin.FacebookAgent.CodeSucceed, then the function call is returned successfully<br/>
	    type:	function(errorCode, message)
	- return:	none
	
- **.logout(callback)**

	Clear the user Token logout user from Facebook.
	
	Parameters and return value:
	- **callback**:	Callback for receiving the result, if errorCode equals plugin.FacebookAgent.CodeSucceed, then the function call is returned successfully<br/>
	    type:	function(errorCode, message)
	- return:	none

- **.isLoggedIn(callback)**

	Detect whether user have been logged in to Facebook.

	Parameters and return value:

	- **callback**:	Callback for receiving the result, if errorCode equals plugin.FacebookAgent.CodeSucceed, then the function call is returned successfully, developer can retrieve the result message or json Object from the message<br/>
	    type:	function(errorCode, message)
	- return:	none

- **.requestAccessToken(callback)**

	Retrieve the user access token for Open Graph API, user must be logged in first.

	Parameters and return value:
	- **callback**:	Callback for receiving the result, if errorCode equals plugin.FacebookAgent.CodeSucceed, then the function call is returned successfully, developer can retrieve the result message or json Object from the message
	type: function(errorCode, message)
	- return: none
	

- **.requestPermissions(permissions, callback)**

	Ask user for Facebook permissions, you must have the correspondent permissions to invoke the Open Graph APIs.

	Parameters and return value:

	- **permissions**:	Permissions to acquire, use "," to seperate multiply permissions<br/>
	    type:	String
	- **callback**:	Callback for receiving the result, if errorCode equals plugin.FacebookAgent.CodeSucceed, then the function call is returned successfully, developer can retrieve the result message or json Object from the message<br/>
	    type:	function(errorCode, message)
	- return:	none

###3. Share APIs

- **.share(info, callback)**

	Share a message to your Facebook, on iOS or Android, if user have installed Facebook app on his device, this function will open Facebook app to finish the share process, otherwise it will open a web view dialog to share a message. If anything goes wrong, the callback will be invoked with error.

	Parameters and return value:

	- **info**:	The content to share<br/>
	    type:	Object
	- **callback**:	Callback for receiving the result, if errorCode equals plugin.FacebookAgent.CodeSucceed, then the function call is returned successfully, developer can retrieve the result message or json Object from the message<br/>
	    type:	function(errorCode, message)
	- return:	none

	Details of parameter:

	- **info** sample:
	
	```
	{
		"description": "Cocos2d-x is a great game engine",
		"title": "Cocos2d-x",
		"link": "http://www.cocos2d-x.org",
		"imageUrl": "http://files.cocos2d-x.org/images/orgsite/logo.png"
	}
	```
	
	- **info** contents:

		1. description: The description of the link
		2. title:       The title of the link
		3. link:        The url of the link
		4. imageUrl:    The image of the link

- **.dialog(info, callback)**

	Share something or send something as message to your friend, if user have installed Facebook app or Facebook Messenger app on his device, this function will open the application to finish the share process, otherwise it will try to open a web view dialog to share or send the message. If anything goes wrong, the callback will be invoked with error.

	Parameters and return value:

	- **info**:	The content to share or to send<br/>
	    type:	Object
	- **callback**:	Callback for receiving the result, if errorCode equals plugin.FacebookAgent.CodeSucceed, then the function call is returned successfully, developer can retrieve the result message or json Object from the message<br/>
	    type:	function(errorCode, message)
	- return:	none

	Details of the parameter:

	- **info** sample:

	```
	{
		// dialog is the sahre type
		"dialog": "share_link",	
		"description": "Cocos2d-x is a great game engine",
		"title": "Cocos2d-x",
		"link": "http://www.cocos2d-x.org",
		"imageUrl": "http://files.cocos2d-x.org/images/orgsite/logo.png"
	}
	```

	- **dialog** type:
	
		1. share_link:			Share a link to Facebook using Facebook app
		2. share_open_graph:		Share Open Graph story to Facebook using Facebook app
		3. share_photo:			Share an image to Facebook using Facebook app
		4. message_link:		Send a link to a friend using Facebook Messenger app
		5. share_open_graph:		Send a Open Graph story to a friend using Facebook Messenger app
		6. share_photo:			Send an image to a friend using Facebook Messenger app

	- Link type parameters:
	
		1. description: Link description
		2. title:       Link title
		3. link:        Link url
		4. imageUrl:    Image for the link

	- Open Graph type parameters:
	
		1. action_type:         Open Graph Action type
		2. preview_property:    Open Graph Object type
		3. other parameters:    Other parameters for this Open Graph story

	- Photo type parameters:

		1. photo:   The path or url for the photo

###4. Open Graph APIs

- **.request(path, method, params, callback)**

	Send an Open Graph API request, more details about Open Graph API can be found in [Facebook Official Open Graph Document](https://developers.facebook.com/docs/opengraph)

	Parameters and return value:

	- **path**:	Open Graph API interface path<br/>
	    type:	Object
	- **method**:	HTTP method to send the request<br/>
	    type:	Number<br/>
	    possible values:

	    ```
	    plugin.FacebookAgent.HttpMethod.Get
	    plugin.FacebookAgent.HttpMethod.Post
	    plugin.FacebookAgent.HttpMethod.Delete
	    ```

	- **params**:	The parameter for the request, parameters vary greatly for different interface, please refer to [Graph API Reference](https://developers.facebook.com/docs/graph-api/reference/)<br/>
	    type:	Object
	- **callback**:	Callback for receiving the result, if errorCode equals plugin.FacebookAgent.CodeSucceed, then the function call is returned successfully, developer can retrieve the result message or json Object from the message<br/>
	    type:	function(errorCode, message)
	- return:	none
	
###5. Payments APIs [Beta feature, comming soon]
    
- **.pay(params, callback)**

    Send a payment request, more details about Payments API can be found in the [Facebook Official Payments Document](https://developers.facebook.com/docs/payments/local-currency-payments-guide)
    
    Parameters and return value:
    
    - **params**:   The parameter for the request<br />
        type:   Object
    - **callback**:	Callback for receiving the result, if errorCode equals plugin.FacebookAgent.CodeSucceed, then the function call is returned successfully, developer can retrieve the result message or json string from the message<br/>
        type:	function(errorCode, message)<br />
        Note:	After the success of the callback parameter, Please refer to [Pay Dialog Return Data](https://developers.facebook.com/docs/payments/reference/paydialog#return-data)
    - return:	none
        
    Details of parameter:
    
    - **params** contents:
    
    ```
    	1. product       : The URL of your og:product object that the user is looking to purchase. 
    	2. quantity      : [Optional]The amount of this item that user is looking to purchase.
    	3. quantity_min  : [Optional]The minimum quantity of the item that user is able to purchase.
    	4. quantity_max  : [Optional]The maximum quantity of the item that user is able to purchase.
    	5. request_id    : [Optional]The developer defined unique identifier for this transaction.
    	6. pricepoint_id : [Optional]Used to shortcut a mobile payer directly to the mobile purchase flow at a given price point.
    	7. test_currency : [Optional]This parameter can be used during debugging and testing your implementation to force the dialog to use a specific currency rather than the current user's preferred currency.
    ```
    
        Parameters vary greatly for different interface, please refer to [Facebook Pay Dialog Document](https://developers.facebook.com/docs/payments/reference/paydialog#properties)
 
    Please note that payment API is only supported on Web and can only be tested with Facebook Canvas Applications. if you want to use this feature, you must deploy your game to a Facebook Canvas Application.

###6. AppEvent APIs [Beta feature, comming soon]

- **.publishInstall()**

	Send an install message to Facebook

	Parameters and return value:

	- return:	none

- **.logEvent(eventName, valueToSum, parameters)**

	Log an app event with the specified name, supplied value, and set of parameters.
	
	Parameters and return value:

	- **eventName** EventName used to denote the event.<br/>
		type: String <br/>
		possible values:

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
	- **valueToSum** (optional) A value to associate with the event which will be summed up in Insights for across all instances of the event, so that average values can be determined, etc.<br/>
		type: Number
	- **parameters** (optional) A Bundle of parameters to log with the event.<br/>
		type: Object <br/>
		possible parameter name constants:
		
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
	- return:	none

##Facebook SDK Beta Features

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
|payments|Send an pay request|×|×|√|
|publishInstall|Send an install message to Facebook|√|√|×|
|logEvent|Log an app event|√|√|×|

##Sample code of Facebook SDK Beta

```
// Get FacebookAgent
var facebook = plugin.FacebookAgent.getInstance();

// Check whether logged in
// @param errCode : 0 logged in, 1 failed to login, 2 logged out
// @param msg : Message returned
facebook.isLoggedIn(function(errCode, msg){
    if(errCode == plugin.FacebookAgent.CodeSucceed){  // Already logged in
        cc.log(JSON.stringify(msg));
    } else{  //Not logged in
        // Login
        facebook.login(function(errCode, msg){

        });
    }
}); 

// Logout
facebook.logout(function(errCode, msg){
});

// Request permissions
// @param array : Permissions to request
// @param callback : Callback function
var permissions = ["create_event", "create_note"];
facebook.requestPermissions(permissions, function(errCode, msg){
});

// Get AccessToken
facebook.requestAccessToken(function(errCode, token){
    if(errCode == plugin.FacebookAgent.CodeSucceed)
        cc.log("AccessToken : " + JSON.stringify(token));
});

// Share API
// Share a simple message on Facebook
var info = {
    "description": "Cocos2d-x is a great game engine",
    "title": "Cocos2d-x",
    "link": "http://www.cocos2d-x.org",
    "imageUrl": "http://files.cocos2d-x.org/images/orgsite/logo.png"
};
facebook.share(info, function (errCode, result) {
    cc.log(JSON.stringify(result));
});

// Dialog API
// similar to fb.ui in Facebook Javascript SDK
// There are in total seven type of dialog listed before, 
// some of them require Facebook app or Messenger app installed on user’s device. 
// Otherwise it will open web dialog or do nothing
var info = {
    "dialog": "share_photo", // Open a dialog to share photo
    "photo": imgpath // The path of photo to share, can be used with screen caption feature
};
facebook.dialog(info, function (errCode, result) {
    cc.log(JSON.stringify(result));
});

// Request API
// Send a request to Facebook OpenGraph api, equivalent to fb.api in Facebook Javascript SDK, 
// take the same parameters
facebook.request("/me", plugin.FacebookAgent.HttpMethod.Get, {}, function(errCode, result){
    // msg is a string of encoded json object which contains the request result
    // User need to parse it manully, but it’s not fixed yet, 
    // we may parse it in Cocos2d-JS and return directly the object to user.
    if(errCode == plugin.FacebookAgent.CodeSucceed) {
        cc.log("User ID : " + response["id"]);
    }
});

// Destroy FacebookAgent
plugin.FacebookAgent.destroyInstance(); 
```
