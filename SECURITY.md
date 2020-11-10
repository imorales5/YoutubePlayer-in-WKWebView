# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 0.3.4   | :x:                |

## Reporting a Vulnerability

Datatheorem tool detects the following vulnerability for iOS 14:

"The following code locations within the App leverage the WKWebView APIs to inject JavaScript into a web page:

-[WKYTPlayerView stringFromEvaluatingJavaScript:completionHandler:] calls -[(id) evaluateJavaScript:completionHandler:] "


Starting with iOS 14, WKWebView offers the following APIs that enable injecting JavaScript 
into a web page while also mitigating collision attacks from untrusted JavaScript:

-[WKYTPlayerView stringFromEvaluatingJavaScript:completionHandler:] calls -[(id) evaluateJavaScript:completionHandler:]

By providing a WKContentWorld instance to the inContentWorld: parameter to these methods, 
iOS will ensure that the JavaScript injected into the web page will run in a sandboxed 
environment from the JavaScript originating from the web, which may be untrusted.

Without the use of WKContentWorld, injected App JavaScript and native web JavaScript run in 
a shared environment. This may lead to multiple attacks and bug scenarios.

