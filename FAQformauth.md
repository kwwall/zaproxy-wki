# How can ZAP automatically authenticate via forms?

ZAP supports form based authentication, and can automatically (re)authenticate, for example when using the Spider or Active Scanner.

There are a few steps required to set this up which can be performed via either the UI or the API.

Via the UI:
  1. Explore your app while proxying through ZAP
  1. Login using a valid username and password
  1. Define a [Context](https://github.com/zaproxy/zap-core-help/wiki/HelpStartConceptsContexts), eg by right clicking the top node of your app in the Sites tab and selecting ["Include in Context"](https://github.com/zaproxy/zap-core-help/wiki/HelpUiTabsSites#include-in-context)
  1. Find the 'Login request' in the Sites or History tab
  1. Right click it and select ["Flag as Context"](https://github.com/zaproxy/zap-core-help/wiki/HelpUiTabsSites#flag-as-context) / "<Context id> Form-based Auth Login request"
  1. Check that the Username and Password parameters are set correctly - they almost certainly wont be!
  1. Find a string in a response which can be used to determine if the user is logged in or not
  1. Highlight this string, right click and select "Flag as Context" / "<Context id> Logged in/out Indicator" as relevant - you only need to set one of these, not both
  1. Double click on the relevant Context node and navigate to the "Users" page - check the user details are correct, add any other users you want to use and enable them all
  1. Navigate to the Context "Forced User" page and make sure the user you want to test is selected
  1. The ![](https://github.com/zaproxy/zap-core-help/wiki/images/fugue/forcedUserOff.png) "[Forced User Mode disabled - click to enable](https://github.com/zaproxy/zap-core-help/wiki/HelpUiTltoolbar#--force-user-mode-on--off)" button should now be enabled
  1. Pressing this button in will cause ZAP to resend the authentication request whenever it detects that the user is no longer logged in, ie by using the 'logged in' or 'logged out' indicator.

Via the API the process is the same but using the API calls:
  1. [context/includeInContext](https://github.com/zaproxy/zaproxy/wiki/ApiGen_context)
  1. [authentication/setAuthenticationMethod](https://github.com/zaproxy/zaproxy/wiki/ApiGen_authentication)
* `authMethodName : formBasedAuthentication`
* `authMethodConfigParams : loginUrl=http://example.com/login.html&loginRequestData=username={%username%}&password={%password%}`
  1. [authentication/setLoginIndicator](https://github.com/zaproxy/zaproxy/wiki/ApiGen_authentication) or `setLogoutIndicator`
  1. [forcedUser/setForcedUserModeEnabled](https://github.com/zaproxy/zaproxy/wiki/ApiGen_forcedUser)

If the "Forced User Mode disabled - click to enable" button is not enabled then you have not configured enough information for ZAP to authenticate - double check that you have performed all of the above steps.

If you have enable forced user mode and are still not logged in when you access your application then look at the requests in the History tab:
* If there is no login request then you have probably not chosen a suitable "logged in/out" indicator, try changing it and trying again
* If there is a login request then look at the requests and response and see if you can work out why the login failed - you may need to change the request or even make multiple requests

If you need to make multiple requests to login then the best option is to record a [Zest](https://github.com/zaproxy/zap-core-help/wiki/HelpAddonsZestZest) authentication script and to test this in isolation first

---

[Back to the FAQ](FAQtoplevel)