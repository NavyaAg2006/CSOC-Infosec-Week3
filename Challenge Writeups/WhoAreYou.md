# Who are you

This challenge is best solved using Burp Suite. Open the [target URL](http://mercury.picoctf.net:1270/) and begin intercepting requests to modify the HTTP headers as needed.  
  
A message is displayed stating: _only for people on official picobrowser_  
To bypass this, change the `User-Agent` header to `picobrowser`.  
```
User-Agent: picobrowser
```
  
The next response says: _dont trust users from other site_  
So, add the `Referer` header:
```
Referer: mercury.picoctf.net:1270
```
  
Then the site responds: _site only worked in 2018_  
Add a `Date` header with a date from 2018:
```
Date: Tue, 29 Oct 2018 16:56:32 GMT
```
  
Next message: _dont trust users who can be tracked_  
Add the `DNT` header set to 1:
```
DNT: 1
```
  
Then: _for people only from sweden_  
Add the `X-Forwarded-For` header with an IP from Sweden:
```
X-Forwarded-For: 192.44.242.19
```
  
Finally: _You are from sweden but dont speak swedish?_  
Set the `Accept-Language` header to Swedish:
```
Accept-Language: sv
```
  
With all headers correctly configured, the final request should look like:
```
GET / HTTP/1.1
Host: mercury.picoctf.net:1270
Cache-Control: max-age=0
Accept-Language: sv
Upgrade-Insecure-Requests: 1
User-Agent: picobrowser
Referer: mercury.picoctf.net:1270
Date: Tue, 29 Oct 2018 16:56:32 GMT
DNT: 1
X-Forwarded-For: 192.44.242.19
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
```

---

**Flag:** `picoCTF{http_h34d3rs_v3ry_c0Ol_much_w0w_f56f58a5}`
