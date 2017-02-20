##Google Cache IP Leakage

####Background:
There seems to be a prevalent myth that using Google's cache is an anonymous means (to the end-server) of accessing the content of page on a particular website.

The Cache has three options:
- "Full version"
- "Text-only version", and
- "View source".

By default however, Google has the Cache set to "Full version", and lacks any way for users to set their default preference otherwise ahead of time.

####Problems:
- By default, when you access Google Cache via Google's web interface by searching, selecting the downward pointing triangle next to a URL, and selecting to view the cached copy of the page, your IP will still be leaked to it.
- Users will also be exposed via DNS query, as hitting the site requires a translation via DNS to IP address.

This is due to the the Cache's default setting--which can't be configured elsewhere--of auto-loading the "Full version" of the website, and the fact that Google does not cache entire copies of websites content. When you access the Cache on this forced "Full version" default setting, doing so instructs your browser to make requests to the server and load the remaining objects that Google does not cache to render the page, such as images.

####Short-term Work-arounds (the Quick Fixes):
- If you access the "Text-only version" of the site this will be anonymous to the end-server. To access this, append: "&strip=1" to the Cache URL prior to accessing it.
- If you want the "View source" version (similarly anonymous), append: "&vwsrc=1".
- Use a more "anonymous-by-default" alternative caching website.

####Mid-term Work-arounds:
- A browser extension that allows users to select the version of the cache that they wish to access, intercepts requests to the cache, and appends the appropriate suffix to the URL before sending it outbound.
- For anonymity (the purpose of the extensinon), it would only really make sense to default to either of the anonymous versions. It stands to reason that most people accessing cached pages are looking for the content, not the page source, so that seems like a reasonable default.

####Long-term Work-arounds:
- Google adding this feature to allow users to pre-select the version of the cache that they desired would be ideal, and is really something they should have implemented in the first place.
- If you know any Google employees, talk to them about the problem, and see if you can get any internal advocates to champion and drive the project forward.
