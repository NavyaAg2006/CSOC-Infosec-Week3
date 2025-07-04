# Secrets
Open the [link](http://saturn.picoctf.net:64466/).

Inspect the page and notice a reference to `secret/assets/index.css` in the header. Instead of opening the full path, navigate to just `secret/`. The page displays a message: _“you almost found me.”_  
  
Inspect the page again and this time you find a reference to `hidden/file.css`. Open only the `hidden/` path. This reveals a login page.  
  
Inspect the login page again and you’ll find a new reference: `supperhidden/login.css`. Navigate to just `supperhidden/`. The page says: _“Finally. You found me. But can you see me”_  
Inspect this page one more time and you’ll find the flag.

---

**Flag:** `picoCTF{succ3ss_@h3n1c@10n_51b260fe}`
