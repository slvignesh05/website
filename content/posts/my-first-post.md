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

![Search field example](images/search-field.png)

## Example of cross site scripting

Consider you go to a website called example.com and you find a search box in it.

You search for a simple query python in it.

After that the url sent to the server to retrieve results would be like:  
`example.com/search?q="python"`

But what attacker do to invoke xss here is input malicious javascript code such as:

```html
<script>alert("xss")</script>
