# jaWT Scratchpad

> [!TIP] 
> What is that cookie?  
> Have you heard of JWT?

Visit the [website](https://jupiter.challenges.picoctf.org/problem/61864/) and log in using any username. After logging in, inspect the page and examine the cookie. It contains a JWT (JSON Web Token).  
  
The website mentions `john`, which links to [John the Ripper](https://github.com/openwall/john), indicating that password cracking may be involved.  
  
We use John the Ripper along with the `rockyou.txt` wordlist to crack the JWT token's signature. This reveals the secret key: `ilovepico`.  
  
Now, using a JWT generator or decoder tool, change the `user` field in the payload from the username entered to `admin`, and sign the token again using the discovered secret key `ilovepico`.  
  
Replace the existing cookie with this newly signed token and refresh the page. You are now successfully logged in as admin.  
  
**Token used:**
```
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoiYWRtaW4ifQ.gtqDl4jVDvNbEe_JYEZTN19Vx6X9NNZtRVbKPBkhO-s
```

---

**Flag:** `picoCTF{jawt_was_just_what_you_thought_1ca14548}`