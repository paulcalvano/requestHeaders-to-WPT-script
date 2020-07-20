# Request Headers to WebPageTest Script

When running [WebPageTest](https://webpagetest.org) as a return visitor, sometimes the page might be rendered differently based on the cookies that the end user has recieved.  Sometimes the sheer size of the cookies can also [impact TTFB](https://dev.to/httparchive/an-analysis-of-cookies-sizes-on-the-web-1mea).  And sometimes you just want to test a website behind a login. In order to test all of these scenarios, you would need to include cookies on your initial request. Fortunately, this is something that you can easily do with the WebPageTest [script](https://sites.google.com/a/webpagetest.org/docs/using-webpagetest/scripting#TOC-setCookie) `setCookie`.

While adding this script step is fairly simple, sometimes the page you are trying to test has a large number of cookies. This can become cumbersome. This  utility parses HTTP request headers to generate a WebPageTest script that includes all of the requested cookies. It can parse both HTTP/1.1 and HTTP/2 request headers (the main differences are case sensitivity in header names and use of `:authority` and `:path` for HTTP/2 instead of `Host` and the the path from the `GET`line in HTTP/1.1)


http://htmlpreview.github.io/?https://github.com/paulcalvano/requestHeaders-to-WPT-script/blob/master/request-headers-to-wpt-script.html

Instructions:

1. In your browser's DevTools, navigate to the Network tab and find the page request that you want to script
2. Copy all of the HTTP request headears.  If given the option of seeing the raw unformatted headers, then use those.
3. Paste the request headers into the text field and click "Parse Request Headers"
4. Make any adjustments needed to the script, and then copy/paste to the WebPageTest script.
 
_This tool processes the headers with local JavaScript, so the request headears are never sent anywhere. However you may want to excercise caution when adding login and session related cookies in WebPageTest as they will be visible in the WebPageTest results_.


