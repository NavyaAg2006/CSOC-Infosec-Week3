# Irish Name Repo 1

Open the [website](https://jupiter.challenges.picoctf.org/problem/39720/)  
When we look at the Support page of the site, we see an inquiry saying `Hi. I tried adding my favorite Irish person, Conan O'Brien. But I keep getting something called a SQL Error`.  
This tells us that the site uses a SQL database. So we use basic SQL Injection to bypass the portal.
```
username: ' OR 1=1--
password: anything
```
And we successfully login.  
  
  
- **Flag:** `picoCTF{s0m3_SQL_c218b685}`
  
---

# Irish Name Repo 2

Open the [website](https://jupiter.challenges.picoctf.org/problem/64649/login.html).  
When we use basic SQL injections we see `SQLi detected.` So we try and use `;` to end the SQL statement after username.
```
username: admin';
password: anything
```
And we successfully login.  
  
  
- **Flag:** `picoCTF{m0R3_SQL_plz_aee925db}`
  
---

# Irish Name Repo 3

Open the [website](https://jupiter.challenges.picoctf.org/problem/29132/).  
Start by entering any password. Initially, no SQL query is displayed on the page.  
  
Upon inspecting the page, you will notice a debug value set to `0`. Change this value to `1`, and the SQL query becomes visible.  
  
Next, attempt a basic SQL injection using the following input: `'or 1 or '`  
However, this input gets transformed into: `'be 1 be'`  
This suggests that the application is substituting the keyword `or` with `be`.  
  
So now we try entering the word `be` in the input field and observe whether it gets converted back to `or` internally. Upon testing, the substitution works as expected.
```
password: 'be 1 be'
```
  
  
- **Flag:** `picoCTF{3v3n_m0r3_SQL_06a9db19}`
