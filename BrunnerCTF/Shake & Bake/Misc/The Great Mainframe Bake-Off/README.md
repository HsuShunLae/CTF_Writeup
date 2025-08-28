# 🖥️ The Great Mainframe Bake-Off - Misc Challenge (30 pts)

**Difficulty:** Beginner

**Author:** H4N5

---

## 📌 Challenge Description

> It's 1974. Deep inside the crusty vaults of CrumbTrust Bank, a covert team of COBOL developers and pastry chefs created a failsafe for their most prized possession: The Marzipan Reverse Recipe.
>
> This sacred document was too valuable to be stored on paper. So, they did the unthinkable - they encoded it and buried it in the production mainframe under a fake batch job titled IEBCAKED. Only those with knowledge of both banking ops and baking science could ever retrieve it.
>
> Years later, the IEBCAKED job has mysteriously reappeared in the job output spool of an IBM z/OS LPAR. But what's left is a string of mysterious byte codes. It's clearly not hex, not ASCII... maybe something older... something only the graybeards of computing would recognize.
>
> Can you decipher the original recipe and unlock the secret to the perfect butterbyte tart?
>
> We are given a suspicious byte sequence:

```
d0-85-97-89-83-85-d9-6d-85-a2-99-85-a5-85-d9-6d-95-
81-97-89-a9-99-81-d4-6d-85-88-e3-6d-a2-c9-6d-a2-89-
88-e3-6d-84-95-c1-6d-a2-85-94-81-99-c6-95-89-81-d4-
6d-95-d6-6d-f0-f7-f9-f1-6d-85-88-e3-6d-95-c9-6d-84-
85-a2-e4-6d-a2-81-e6-6d-c3-c9-c4-c3-c2-c5-c0-99-85-
95-95-a4-99-82
```

---

## 🔎 Approach & Solution

### 1. Recognizing the Encoding

The challenge hint (“1970s mainframes”) points to **EBCDIC** (Extended Binary Coded Decimal Interchange Code), an old character encoding used by IBM mainframes before ASCII became dominant.

---

### 2. First Attempt: Online Decoder

Using the [dcode.fr EBCDIC decoder](https://www.dcode.fr/ebcdic-code), the hex string was decoded, producing reversed text:

<img width="975" height="463" alt="image" src="https://github.com/user-attachments/assets/bd5bbe77-aab4-45c5-94b0-8610111d02e6" />

Output looked like this:

```
}epiceR_esreveR_napizraM_ehT_sI_sihT_dnA_semarFniaM_nO_0791_ehT_nI_desU_saW_CIDCBE{rennurb
```

This is clearly the **flag reversed**.

---

### 3. Automating with Python

To cleanly decode and reverse, I wrote a short Python script:

```python
# mainframe_bakeOff.py
hex_bytes = (d0-85-97-89-83-85-d9-6d-85-a2-99-85-a5-85-d9-6d-95-"
            "81-97-89-a9-99-81-d4-6d-85-88-e3-6d-a2-c9-6d-a2-89-"
            "88-e3-6d-84-95-c1-6d-a2-85-94-81-99-c6-95-89-81-d4-"
            "6d-95-d6-6d-f0-f7-f9-f1-6d-85-88-e3-6d-95-c9-6d-84-"
            "85-a2-e4-6d-a2-81-e6-6d-c3-c9-c4-c3-c2-c5-c0-99-85-"
              95-95-a4-99-82)

# Convert to bytes
b = bytes.fromhex(hex_bytes.replace("-", ""))

# Decode using EBCDIC CP037 (US/Canada)
s = b.decode("cp037")

# Reverse string to reveal flag
print(s[::-1])
```

Running it revealed the correct flag:

```
python mainframe_bakeOff.py
```

Output:

<img width="975" height="94" alt="image" src="https://github.com/user-attachments/assets/50e5d1d5-26d7-4320-b86e-202e2dbf8f2b" />

---

## 🏁 Flag

```
brunner{EBCDIC_Was_Used_In_The_1970_On_MainFrames_And_This_Is_The_Marzipan_Reverse_Recipe}
```

---

## 📚 Lessons Learned

* Some CTF challenges reference **historical computing standards** (EBCDIC vs ASCII).
* When analyzing strange byte sequences, consider older or less common encodings.
* Always check if output is reversed, shifted, or obfuscated after decoding.
* Automating the decoding with Python ensures reproducibility.

---
