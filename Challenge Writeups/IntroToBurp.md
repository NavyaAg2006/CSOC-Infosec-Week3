# Intro To Burp

Open the challenge site and fire up Burp Suite to intercept requests.  
  
Register using any random credentials. After signing up, the site asks for an OTP.  
  
Intercept the OTP request in Burp and send it to the Repeater.  

If you just send it with the `otp` parameter (even with an empty or wrong value), you’ll get a response like:
```
Invalid OTP
```

But if we just **remove** the `otp` parameter completely and resend the request, the server skips the OTP check and hands you the flag.

---

**Flag:** `picoCTF{#0TP_Bypvss_SuCc3$S_b3fa4f1a}`
