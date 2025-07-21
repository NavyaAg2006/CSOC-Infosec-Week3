# Java Script Kiddie
Open the [challenge link](https://jupiter.challenges.picoctf.org/problem/17205).  
The challenge was to recover a PNG file from a scrambled byte array. Each column in a 16-byte-wide image grid had been shifted using a formula derived from JavaScript:  
`offset = (shifter × 16) % total_length + column_index`.  
  
To get the scrambled bytes append `/bytes` in front of the original challenge link.  

To reverse this, the script tested all digit values (0–9) as possible shifters for each column, comparing the shifted bytes to the known PNG signature (`89 50 4E 47 0D 0A 1A 0A ...`)  
```py
LEN = 16
expected_bytes = [0x89, 0x50, 0x4E, 0x47, 0x0D, 0x0A, 0x1A, 0x0A, 0x00, 0x00, 0x00, 0x0D, 0x49, 0x48, 0x44, 0x52]
image_bytes = "[] ".split(" ")
image_bytes = [int(byte) for byte in image_bytes]

key = []

for key_idx in range(LEN):
    for shifter in range(10):  # all digits
        offset = ((shifter * LEN) % len(image_bytes)) + key_idx
        if expected_bytes[key_idx] == image_bytes[offset]:
            key.append(shifter)
            break
```
forming the key `5108180323263640`.

we tried this key but it didn't generate the flag.

Upon inspecting the resulting PNG, we observed that in three positions of the key, higher shifter values could also be used without affecting the correctness of the file. This suggests multiple valid options for those key bytes that still yield a valid PNG. The values replaced with "." are the values that can be changed

51081803...63640

The possible values in these positions are:

* First : 2, 3, 4
* Second : 3, 4, 5, 6
* Third : 2, 3, 4

Brute-forcing the 36 possible combinations (3×4×3) revealed the correct key, enabling PNG decryption.

upon entering the **KEY:** `5108180345363640`  
  
We get the following qr code:  
<img width="370" height="370" alt="image" src="https://github.com/user-attachments/assets/334e2f81-29b5-4f57-9777-1e6d965443b2" />

Scanning this gives the flag.

---

**Flag:** `picoCTF{066cad9e69c5c7e5d2784185c0feb30b}`
