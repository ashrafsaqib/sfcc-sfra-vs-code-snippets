# Cookie

## Set Cookie in SFRA 

```
/**
 * Sets cookie
 * @param {string} cookieName - cookie name
 * @param {string} cookieValue - cookie value
 * @param {number} maxAge - in seconds
 */
function setCookie(cookieName, cookieValue, maxAge) {
    maxAge = (empty(maxAge) ? 24 : maxAge); 
    var cookie;
    if (!empty(cookieName) && !empty(cookieValue) && !empty(maxAge)) {
        // make sure we're not going to violate the api.cookie.maxValueLength - warnings start at 1,200
        var stringLimit = 1150;

        cookie = new Cookie(cookieName, cookieValue);
        cookie.setPath('/');
        if (cookieValue.length < stringLimit) {
            cookie.setMaxAge(maxAge);
        } else {
            cookie.setMaxAge(0);
        }
        response.addHttpCookie(cookie);
    } else if (!empty(cookieName) && empty(cookieValue) && !empty(maxAge)) {
        cookie = new Cookie(cookieName, cookieValue);
        cookie.setPath('/');
        cookie.setMaxAge(0);
        response.addHttpCookie(cookie);
    }
}
```

## Get Cookie In SFRA

```
/**
 * Get cookie's value
 * @param {string} cookieName - cookie name
 * @param {?string} defaultValue - default value to return
 * @returns {?string} - cookie's value
 */
function getCookieValue(cookieName, defaultValue) {
      // Get the value from the raw cookie header
      var headers = request.httpHeaders;
      var cookieHeader = headers.get("cookie");
      if (cookieHeader) {
          var cookies = cookieHeader.split("; ");
          for (var i = 0; i < cookies.length; i++) {
              var cookie = cookies[i];
              var cookieStr = cookie.toString();
              var firstEqual = cookieStr.indexOf("=");
              var name = cookieStr.substring(0, firstEqual);
              var val = cookieStr.substr(firstEqual + 1);
              return val;
          }
      }
    

    return defaultValue;
}
```
