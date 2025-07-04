# Client-Side-Again

In this challenge, you're presented with a login portal.  
  
Open the [challenge site](https://jupiter.challenges.picoctf.org/problem/6353/) and inspect the page source. The HTML looks relatively simple, but there's a key detail buried in the inline JavaScript section.  
  
You'll find a line of code with obfuscated variable names and a list of strings, one of which contains the beginning and ending parts of the flag:  
```
'picoCTF{', 'not_this', '_again_', '0a029}'
```
This part is hidden between other strings and values, making it easy to miss if you're skimming.  
  
By closely examining the JavaScript snippet embedded directly in the HTML, you can piece together the flag even though it's split and buried between other function calls and values.

---

**Flag:** `picoCTF{not_this_again_0a029}`
