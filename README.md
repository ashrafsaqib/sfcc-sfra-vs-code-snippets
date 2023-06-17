# Salesforce Commerce Cloud SFRA Code Examples & Snippets

[SFCC VS Code Snippets Plugin](https://marketplace.visualstudio.com/items?itemName=SaqibAshraf.sfra-vs-snippets) to help you write SFCC SFRA code faster in VS code.

## Features

Quickly write code by just typing prefix [sfra-] and relevant keywords

## Controllers / Helpers File Code
### Logs [sfra-log]
```
var Logger = require('dw/system/Logger');
Logger.getLogger('customCategory', 'customLogger').error('any log message' + JSON.stringify(anyObj));
```

### Site Preferences [sfra-sitepreference]

```
var Site = require('dw/system/Site');
var anyPref = Site.current.getCustomPreferenceValue('anyPref');
```
### Custom Objects Query [sfra-customobjects]

```

//query custom objects based on custom attributes
var CustomObjMgr = require('dw/object/CustomObjectMgr');
var queryMap = require('dw/util/HashMap')(); 
queryMap.put('custom.status', 'COMPLETED');
var customObjIterator = CustomObjMgr.queryCustomObjects('PaymentProcessing', queryMap, null);
while (customObjIterator.hasNext()) {
    var payProcessingObj = customObjIterator.next();
}

//find custom object based on ID 

var CustomObjectMgr = require("dw/object/CustomObjectMgr");
var customObjectType = CustomObjectMgr.getCustomObject("customObjectType", customObjID);
const customAttr = customObjectType ? customObjectType.custom.customAttr: null;

// create custom obj
Transaction.wrap(function () {
    var customObject = CustomObjectMgr.createCustomObject("CustomObjType", "customobj-id");
    customObject.custom.attributeX = "anyValue";
});
```
### URL [sfra-urls]

`URLUtils.url('Page-Show', 'cid', 'privacy-policy')`

### Resource / Language Files text [sfra-resourcetext]

`Resource.msg('description.privacypolicy.registration.loyalityoptin', 'registration', null)`

### Controller Override [sfra-controller-override]
```
'use strict';

var server = require('server');
server.extend(module.superModule);

module.exports = server.exports();
```

### Controller Function [sfra-controller-function]

```
server.post('Any-Endpoint', function (
    req,
    res,
    next
) {

    res.render('template/any', { pageData: pageData });
    res.json({
        success: true,
    });

    next();
});
```
### Transaction [sfra-transaction]
```
var Transaction = require('dw/system/Transaction');
    Transaction.wrap(function () {
});
```
### Session Data Get / Set [sfra-session-data]
```
//using privacy cache
session.privacyCache.get('name')
session.privacyCache.set('name', value);
// custom properties on session object
session.custom.anyProp = anyValue;
// access current customer logged
session.customer.profile
//access currency
session.currency.currencyCode
// you can access or modify privacy object if its initiated 
session.privacy.anyProp
// check if user is logged in 
session.userAuthenticated
```
### Get Current Customer [sfra-customer]
```
// you can use session global variable 
session.customer.profile
//you can use request variable inside controller
req.currentCustomer.profile
// raw is actually instance of Class Customer 
req.currentCustomer.raw.profile
```
### Get Current Site [sfra-site]
```
var Site = require('dw/system/Site');
Site.getCurrent().getID();
```
### Get Current Locale or Country [sfra-locale-country]
```
var Locale = require('dw/util/Locale');
var currentLocale = Locale.getLocale(req.locale.id);
currentLocale.country
```
### Get Current Instance Type [sfra-instance]
```
var System = require('dw/system/System');
System.getInstanceType() !== System.PRODUCTION_SYSTEM
```
### Get Custom Cache [sfra-cache-custom]
```
var CacheMgr = require('dw/system/CacheMgr');
CacheMgr.getCache('anyCache');
var cacheKey = pxCache.get('anykey');
pxCache.put('anykey, 'anyvalue');
```
## ISML code 
### site preference [sfra-sitepreference-isml]
### url [sfra-url-isml]
### Resource Text [sfra-resourcetext-isml]
### Remote Include [sfra-include-remote-isml]


## Release Notes


### 1.0.0

Added Snippets for Transaction, Controller Override , Controller Function
Session Data get / set , Currently logged customer 
Short Codes Added for following
- Get Current Site
- Get Current Locale or Country
- Get Current Instance Type
- Get Custom Cache
- remote Include 
- Custom Objects
- Locale
- Session
- Logs



## [Change Logs](CHANGELOG.md)
I Update this extension twice a month! So good things keep coming!

Add your Suggestions or Issues at github repo at https://github.com/ashrafsaqib/sfcc-sfra-vs-code-snippets/issues
**Enjoy!**
