---
# This page was generated from the add-on.
title: Passive Scan Rules - Beta
type: userguide
weight: 1
cascade:
  addon:
    id: pscanrulesBeta
    version: 22.0.0
---

# Passive Scan Rules - Beta

The following beta quality passive scan rules are included in this add-on:

## Big Redirect Detected (Potential Sensitive Information Leak)

This check predicts the size of various redirect type responses and generates an alert if the response is greater than the predicted size. A large redirect response may indicate that although a redirect has taken place the page actually contained content (which may reveal sensitive information, PII, etc.).

Latest code: [BigRedirectsScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/BigRedirectsScanner.java)

## Cookie Poisoning

This check looks at user-supplied input in query string parameters and POST data to identify where cookie parameters might be controlled. This is called a cookie poisoning attack, and becomes exploitable when an attacker can manipulate the cookie in various ways. In some cases this will not be exploitable, however, allowing URL parameters to set cookie values is generally considered a bug.

Latest code: [UserControlledCookieScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/UserControlledCookieScanner.java)

## Content Security Policy (CSP) Header Not Set

This checks HTML response headers for the presence of a Content Security Policy header.  
By default this rule checks for the presence of the "Content-Security-Policy" header, and at the Low threshold also checks for the "X-Content-Security-Policy" and "X-WebKit-CSP" headers.  
Redirects and non HTML responses are ignored except at the Low threshold.

If a "Content-Security-Policy-Report-Only" header is found on a response an INFO alert is raised. This may represent an enforcement effort
that is actively being refined or developed, or one which is only partially implemented.

Latest code: [ContentSecurityPolicyMissingScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/ContentSecurityPolicyMissingScanner.java)

## Directory Browsing

Passively scan responses for signatures that are indicative that Directory Browsing is possible.

Latest code: [DirectoryBrowsingScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/DirectoryBrowsingScanner.java)

## Hash Disclosure

Passively scan for password hashes disclosed by the web server.   
Various formats are including, including some formats such as MD4, MD5, and SHA\*, which are sometimes used for purposes other than to contain password hashes.

Latest code: [HashDisclosureScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/HashDisclosureScanner.java)

## Heartbleed OpenSSL Vulnerability (Indicative)

Passively scans for HTTP header responses that may indicate that the server is vulnerable to the critical HeartBleed OpenSSL vulnerability.

Latest code: [HeartBleedScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/HeartBleedScanner.java)

## HTTP Server Response Header Scanner

This checks response headers for the presence of a server header that contains version details. At LOW Threshold will raise an alert based on presence of the header field whether or not a version string is detected.

Latest code: [ServerHeaderInfoLeakScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/ServerHeaderInfoLeakScanner.java)

## HTTP to HTTPS Insecure Transition in Form Post

This check looks for insecure HTTP pages that host HTTPS forms. The issue is that an insecure HTTP page can easily be hijacked through MITM and the secure HTTPS form can be replaced or spoofed.

Latest code: [InsecureFormLoadScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/InsecureFormLoadScanner.java)

## HTTPS to HTTP Insecure Transition in Form Post

This check identifies secure HTTPS pages that host insecure HTTP forms. The issue is that a secure page is transitioning to an insecure page when data is uploaded through a form. The user may think they're submitting data to a secure page when in fact they are not.

Latest code: [InsecureFormPostScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/InsecureFormPostScanner.java)

## Open Redirect

Open redirects are one of the OWASP 2010 Top Ten vulnerabilities. This check looks at user-supplied input in query string parameters and POST data to identify where open redirects might be possible. Open redirects occur when an application allows user-supplied input (e.g. http://nottrusted.com) to control an offsite redirect. This is generally a pretty accurate way to find where 301 or 302 redirects could be exploited by spammers or phishing attacks.

Latest code: [UserControlledOpenRedirectScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/UserControlledOpenRedirectScanner.java)

## PII Disclosure scanner

PII is information like credit card number, SSN etc. This check currently reports only numbers which match credit card numbers and pass Luhn checksum, which gives high confidence, that this is a credit card number.

Latest code: [PiiScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/PiiScanner.java)

## Retrieved from Cache

This scanner detect content that has been served from a shared cache.

Latest code: [RetrievedFromCacheScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/RetrievedFromCacheScanner.java)

## Reverse Tabnabbing

This checks to see if any links use a target attribute without using both of the "noopener" and "noreferrer" keywords in the "rel" attribute, as this will allow target pages to take over the page that opens them.  
By default this rule will ignore all links that are in the same context as the page. At the LOW threshold it will only ignore links that are on the same host.  
At HIGH threshold it will only report links that use the "_blank" target.  
You can specify a comma separated list of URL regex patterns using the `rules.domains.trusted` parameter via the Options 'Rule configuration' panel. Any link URL that matches one of these patterns will be considered to be in a trusted domain and will therefore not be reported.

Latest code: [LinkTargetScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/LinkTargetScanner.java)

## Servlet Parameter Pollution

Searches response content for HTML forms which fail to specify an action element. Version 3 of the Java Servlet spec calls for aggregation of query string and post data elements which may result in unintended handling of user controlled data. This may impact other frameworks and technologies as well. **Note:** This scan rule will only analyze responses on LOW Threshold.

Latest code: [ServletParameterPollutionScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/ServletParameterPollutionScanner.java)

## Strict Transport Security Header Scanner

This scanner checks HTTPS responses for the presence of a HTTP Strict Transport Security (HSTS) header and tests for various implementation concerns, alerting if they're found. Alerts generated:

* **Strict-Transport-Security Header Not Set:** If the response is HTTPS and the header is completely missing.
* **Strict-Transport-Security Disabled:** If the response is HTTPS and the max-age value is set to zero, thus resetting the browser's HSTS information for the site.
* **Strict-Transport-Security Multiple Header Entries (Non-compliant with Spec):** If the response is HTTPS and there is more than one HSTS header on the response.
* **Strict-Transport-Security Missing Max-Age (Non-compliant with Spec):** If the response is HTTPS, a HSTS header is specified but the max-age value does not contain a number.
* **Strict-Transport-Security Defined via META (Non-compliant with Spec):** If the response body includes a META tag which attempts to define HSTS.
* **Strict-Transport-Security Header on Plain HTTP Response:** If the response is HTTP and the HSTS header is present.
* **Strict-Transport-Security Max-Age Malformed (Non-compliant with Spec):** If the response is HTTPS and the HSTS header is present, but there are quotes preceding the max-age directive (quotes are allowed around the max-age value, but not around the directive itself).
* **Strict-Transport-Security Malformed Content (Non-compliant with Spec):** If the response is HTTPS and a HSTS header is present, but there is some unexpected content (such as curly quotes). The expectation is that the content be printable ASCII.

Redirects to HTTPS URLs on the same domain will only be reported at Low threshold.

Latest code: [StrictTransportSecurityScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/StrictTransportSecurityScanner.java)

## User Controllable Charset

This check looks at user-supplied input in query string parameters and POST data to identify where Content-Type or meta tag charset declarations might be user-controlled. Such charset declarations should always be declared by the application. If an attacker can control the response charset, they could manipulate the HTML to perform XSS or other attacks.

Latest code: [UserControlledCharsetScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/UserControlledCharsetScanner.java)

## User Controllable HTML Element Attribute (Potential XSS)

This check looks at user-supplied input in query string parameters and POST data to identify where certain HTML attribute values might be controlled. This provides hot-spot detection for XSS (cross-site scripting) that will require further review by a security analyst to determine exploitability.

Latest code: [UserControlledHTMLAttributesScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/UserControlledHTMLAttributesScanner.java)

## User Controllable Javascript Event (XSS)

This check looks at user-supplied input in query string parameters and POST data to identify where certain HTML attribute values might be controlled. This provides hot-spot detection for XSS (cross-site scripting) that will require further review by a security analyst to determine exploitability.

Latest code: [UserControlledJavascriptEventScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/UserControlledJavascriptEventScanner.java)

## X-Backend-Server Header Information Leak

This checks response headers for the presence of X-Backend-Server details.

Latest code: [XBackendServerInformationLeak.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/XBackendServerInformationLeak.java)

## X-ChromeLogger-Data Header Information Leak

This checks response headers for the presence of X-ChromeLogger-Data or X-ChromePhp-Data details.

Latest code: [XChromeLoggerDataInfoLeakScanner.java](https://github.com/zaproxy/zap-extensions/blob/master/addOns/pscanrulesBeta/src/main/java/org/zaproxy/zap/extension/pscanrulesBeta/XChromeLoggerDataInfoLeakScanner.java)
