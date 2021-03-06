Google Analytics Server Side Changelog
======================================

Version 0.8.4 Beta
------------------

- Extract re-used validation into re-usable validator classes
- Convert readme to github flavoured markdown  
- Added in PHPUnit tests for a large majority of the code, remainder to come
- Search Engine information used for organic campaign info changed format in 5.3.0, update to deal with that
- Altered parameters to getEventString. Includes code to deal with Backwards Compatibility.
- Default GASS\Http adapter is now GASS\Http\Curl, falls back to GASS\Http\Stream if php cURL extension is not available

Version 0.8.3 Beta
------------------

- Fix a few issues existing in the code with un-defined / un-used variables

Version 0.8.2 Beta
------------------

- Add in support for organic campaign parameters with __utmz cookies.
- Only send utmip gif query parameter when using a mobile account, pointless otherwise.

Version 0.8.1 Beta
------------------

- Add a __callStatic magic method to GASS\Http so adapter methods can be called statically
- Ensure $php_errormsg has a value in GASS\Http\Stream so can be used when http request fails
- Correct spelling mistakes (retreive -> retrieve)

Version 0.8.0 Beta
------------------

- Converted to PHP 5.3 with namespaces instead of PHP 5.2 virtual namespaces  
	( using @ralphschindler 's php-namespacer: https://github.com/ralphschindler/PHPTools )
- Removed deprecated methods from main class
- Removed get/setEvent, not in GA code and not needed, set is done directly in trackEvent
- Removed support for old csv cache in UserAgentStringInfo which just stored user agents without IPs
- BrowserCap renamed BrowsCap inline with PHP

Version 0.7.11 Beta
-------------------

- Remove all non-PHPDoc doc blocks and replace with PHPDoc blocks so all works when PHPDoc run on project
- Add in package and subpackage tags to all files for use in PHPDoc
- GASS_BotInfo_UserAgentStringInfo now blocks per IP address as well as user agent string to ensure is blocking all bots in list

Version 0.7.10 Beta
-------------------

- Sets the __utmv custom var cookie which stores scope 1 (visitor-level) variables
- Correct the custom var string passed to GA, scope 3 (page-level) shouldn't be passed.
- PHPDoc completion.
- Only load data files in BotInfo adapters when data actually needed
- setCustomVar uses the first available index when one not provided and returns $this for chaining

Version 0.7.9 Beta
------------------

- Ensure user can use the Mobile GA accounts starting in "MO-" aswell. Lets utmip provide the user's location to GA.
- Remove un-required method call.
- Silence parse_url when an issue occurs, return value is checked.

Version 0.7.8 Beta
------------------

- Silence all is_readable, is_writable, file_exists and filemtime calls as the result is being checked anyway
so we don't really want a lot of E_WARNING php errors for no reason.
- Minor code speed improvements
- Some extra verification on event / custom variable strings
- Remove issue where cookie contains one of the invalid raw cookie characters
- convert createPageView / createEvent / setCustomVariable to trackPageView / trackEvent / setCustomVar as they 
are in the Google Analytics ECMAScript, left alias functions for old method names
- Add getVisitorCustomVar, deleteCustomVar, setSessionCookieTimeout & setVisitorCookieTimeout methods

Version 0.7.7 Beta
------------------

- Ensure the BrowserCap latest version date isn't retrieved more than once a day form the server.
Store the version date in a one day cache file in same dir as php_browscap.ini. 
- Make createPageView compatible with Google's trackPageView.
- Fix issue chappy84/google-analytics-server-side#6 raised by skl with the event value being passed wrongly to Google.

Version 0.7.6 Beta
------------------

- BrowserCap ini file is now parsed and dealt with by the code rather than using php's built in get_browser. 
- BrowserCap ini file now updated whenever update available on server.

Version 0.7.5 Beta
------------------

- Fix wrong name variable used in BrowserCap.
- Ensure UserAgent has been sent to BotInfo.
- Ensure AcceptedLanguage / RemoteAddress / UserAgent has been sent to Http.

Version 0.7.4 Beta
------------------

- Fix autoloading issue in PHP 5.2 where GASS_Adapter_Base::__construct didn't match GASS_Adapter_Interface::__construct.

Version 0.7.3 Beta
------------------

- Add in setting of Custom Variables.
- Add extra nonInteraction parameter to setEvent / createEvent.
- Correct issue with getEventString where value set in wrong place.

Version 0.7.2 Beta
------------------

- Check event value is integer.

Version 0.7.1 Beta
------------------

- PHPDoc and Readme updates.

Version 0.7.0 Beta
------------------

- Convert into a small framework under GASS PHP 5.2 virtual namespace (for backwards compatability).
- Add in autoloader for new GASS virtual namespace.
- GASS_Http singleton so can be used anywhere in framework without passing options around.
- GASS_Http uses adapters, defaults to Stream, can also use cURL, ability for developer to write own adapters.
- GASS_BotInfo which detects if user-agent is a bot or not separated out as not required.
- GASS_BotInfo uses adapters, php's BrowserCap is default, but original UserAgentString.info is also available, developer can write own adapters.

Version 0.6.4 Beta
------------------

- Ensure bots.csv is not empty when received from url and ensure lines in csv aren't empty before dealing with them.

Version 0.6.3 Beta
------------------

- Ensure set cookie headers are only sent out once.

Version 0.6.2 Beta
------------------

- Add in check to ensure cURL extension has been installed when the class is instantiated.

Version 0.6.1 Beta
------------------

- Allow setting / getting of any class level variable with a publicly available get / set method via getOption / setOption methods.

Version 0.6.0 Beta
------------------

- Ability to ignore logging statistics for web trawling bots and spiders and caching of the bots list.
- Auto-setting of latest GA version number from ga.js.
- Auto-setting of accepted language from headers.
- Ability to pass options to cURL.
- Remove auto-setting of charset from headers, default to UTF-8 (response should define this, not request headers).
- Try manually reporting IP address to GA as done in the GA mobile code ( http://www.google.com/analytics/googleanalyticsformobile.zip ).
- str_getcsv is not available in PHP before PHP 5.3 so added in a crude implementation so it works in lower than 5.3.

Version 0.5.5 Beta
------------------

- Set Document-Referer by default and check url format.
- Add extra Exceptions thrown in required circumstances.
- Ensure explode on cookies only returns no of parts required.
- Add Traffic source string with utmz cookie.
- Update PHPDoc in code.
- Update Readme with extra info & to correct markdown format.


Version 0.5.0 Beta
------------------

- Initial Release.
- Provides basic PageView and Event functionality, setting cookies in correct format.