---
title: "what is a XSS"
date: 2025-07-04
draft: false
---

XSS-Cross Site Scripting

Every website(dynamic ones) functions are built with javascripts.

So a function such as clicking a button in a website will invoke the javascript function in the background.

But what if an attacker can input malicious javascript code into the website?

Yes this is known as cross site scripting. The attacker scripts the code from the other end.

## Vulnerable areas to look in a website

1. Search field  
2. Comment boxes  
3. Name field  
4. Or any other parameter  

![Search field example](https://raw.githubusercontent.com/slvignesh05/website/refs/heads/main/content/posts/images/xss-i.png)

## Example of cross site scripting

Consider you go to a website called example.com and you find a search box in it.

You search for a simple query "python'"

After that the url sent to the server to retrieve the results would be like:  
`example.com/search?q="python"`

But what attackers do here to invoke xss is input 'malicious javascript' code such as:

```html
<script>alert("xss")</script>

<img src=0 onerror=alert("xss")>

```

These malicious payloads gets embedded in the source code of the website and executes on the victim’s browser to exfiltrate sensitive information from them..

Biggest Query ( What most people asked me)
An Attacker performs xss on the victim? But what can he truly achieve?

A popup alert box on the victim’s browser can do no harm.

The above question can be answered as “severe” or “low” impact issue for the victim.

The primary objective of XSS is to get the session cookies.

The session cookies can be used by the attackers to impersonate the victims

Can't understand the above? 

Cookies (often known as internet cookies) are text files with small pieces of data — like a username and password — that are used to identify your computer as you use a network. Specific cookies are used to identify specific users and improve their web browsing experience. Data stored in a cookie is created by the server upon your connection. This data is labeled with an ID unique to you and your computer. When the cookie is exchanged between your computer and the network server, the server reads the ID and knows what information to specifically serve you. [https://www.kaspersky.com/resource-center/definitions/cookies](https://www.kaspersky.com/resource-center/definitions/cookies)

in simple terms "They streamline the login information, so users don't have to remember site passwords." (This is why sometimes when you login to a website you're automatically logged in without authentication)

So attackers getting hands on these "cookies" will allow them to impersonate victims

But how?

every website stores session and other cookie stuff in the browser which you can view by inspecting the page(CTRL+Shift+I) and going to the 'application` tab

![Search field example](https://raw.githubusercontent.com/slvignesh05/website/refs/heads/main/content/posts/images/Screenshot%202025-07-05%20235221.png)

Here the attacker can place the victim's cookie(stole from xss) in place of his to succesfully take over the account or to access sensitive information of the victim.

Note: <script>alert(document.cookie)</script> will popup the victim's cookie , The attacker can modify the payload further to send this cookie to their server.

