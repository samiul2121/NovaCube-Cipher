                                  ![image](https://github.com/user-attachments/assets/b5ad8856-0cca-4e32-8adf-55776989aa29)

                                          Hajee Mohammad Danesh Science and Technology University  Dinajpur-5200



 
                                        Course Title:Mathematical Analysis for Computer Science  
                                                      Course Code: CSE 361



                                                      Algorithm Name  
                                                     NovaCube Cipher
                                         Cube-Based Symmetric Modular Cipher


                                                      Submitted By  
                                              Name: samiul Islam sami
                                                  Student ID:2102020
                                                   Level: 3  Semester: II  
                                      Department: Computer Science and Engineering

                                                       Submitted To  
                                                  Name: Pankaj Bhowmik  
                                                  Designation: Lecturer  
                                        Department: Computer Science and Engineering



 Algorithm Description
**NovaCube** is a symmetric encryption algorithm that transforms characters using modular arithmetic, position-based logic, and a cubed-key value. It ensures strong obfuscation without pattern repetition.



 Encryption Algorithm
Let:  
- `P[i]` = ASCII value of the i-th character in plaintext  
- `K` = user-provided odd integer key  
- `i` = character position (starting from 0)  
- `E[i]` = encrypted ASCII value

 Formula:

key_value = (K^3 + i^2) % 127  
E[i] = (P[i] + key_value + i) % 127




 Decryption Algorithm
Let:  
- `C[i]` = ASCII of i-th ciphertext character  
- `K` = symmetric key  
- `i` = position  
- `D[i]` = decrypted ASCII value

Formula:

key_value = (K^3 + i^2) % 127  
D[i] = (C[i] - key_value - i + 254) % 127
```

---

## 🧪 Example Test Case
**Plaintext:** HSTU  
**Key:** 5

### Encryption Table:
| Pos | Char | ASCII | KeyVal | Encrypted ASCII | Cipher |
|-----|------|--------|--------|------------------|--------|
| 0   | H    | 72     | 125    | 70               | F      |
| 1   | S    | 83     | 126    | 83               | S      |
| 2   | T    | 84     | 2      | 88               | X      |
| 3   | U    | 85     | 7      | 95               | _      |

**Ciphertext:** FSX_

### Decryption Table:
| Pos | Cipher | ASCII | KeyVal | Decrypted |
|-----|--------|--------|--------|-----------|
| 0   | F      | 70     | 125    | H         |
| 1   | S      | 83     | 126    | S         |
| 2   | X      | 88     | 2      | T         |
| 3   | _      | 95     | 7      | U         |

**Decrypted Text:** HSTU ✅

---

## 🧰 Source Code (Python)
```python
# NovaCube Cipher

def encrypt(text, key):
    encrypted = ''
    for i, ch in enumerate(text):
        key_val = (key**3 + i**2) % 127
        new_char = (ord(ch) + key_val + i) % 127
        encrypted += chr(new_char)
    return encrypted

def decrypt(cipher, key):
    decrypted = ''
    for i, ch in enumerate(cipher):
        key_val = (key**3 + i**2) % 127
        orig_char = (ord(ch) - key_val - i + 254) % 127
        decrypted += chr(orig_char)
    return decrypted

# Example
plaintext = "HSTU"
key = 5

cipher = encrypt(plaintext, key)
original = decrypt(cipher, key)

print("Encrypted:", cipher)
print("Decrypted:", original)
```

---

## 🥇 Features
- Symmetric key based  
- Non-linear key expansion with cube and square  
- Position sensitive  
- High randomness with simple logic  
- Printable ASCII-safe via mod 127

---

## 📊 Complexity
- Time: O(n)  
- Space: O(1) extra  
- Fully reversible ✅

---

## 🔹 Flowchart
Flowchart diagram attached below:  
![Flowchart](flowchart.png)

---

## 🚀 Future Improvements
- Key rotation on position basis  
- Extended UTF-8 support  
- Hybrid chaining block mode  
- Key generation from passphrase
