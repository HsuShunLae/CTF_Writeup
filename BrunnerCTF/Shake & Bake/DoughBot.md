# 🏴 Challenge Name – *DoughBot* (20 Points)

**Difficulty:** Beginner

**Author:** rvsmvs

---

## 📌 Challenge Description

Our state-of-the-art smart mixer, DoughBot, crashed during a routine kneading cycle. Luckily, a technician was monitoring the device over UART and captured the memory output just before the reboot.

Analyze the captured dump and see what the DoughBot was trying to say before it rebooted.
File can be accessed here.

## 🔎 Approach & Solution

### 1. Initial Analysis

After extracting the archive, obtain a binary file. Reading it directly with ```cat``` reveals UART logs

```
cat DoughBot_dump.bin
```

#### Output
<img width="975" height="643" alt="image" src="https://github.com/user-attachments/assets/af74d6ff-33da-473e-9f97-340c5df56fd2" />

---

### 2. Decoding the Flag

Decode the string by Base64 Decoding.

```bash
echo -n "YnJ1bm5lcnttMXgzZF9zMWduYWxzXzRfc3VyZX0=" | base64 -d
```

#### Result
<img width="939" height="103" alt="image" src="https://github.com/user-attachments/assets/53faf27e-3800-4f7a-9f3f-4734a08ef12f" />

---

## 🏁 Flag

```
brunner{m1x3d_s1gnals_4_sure}
```

---

## 📚 Lessons Learned

* Device memory dumps often contain plaintext logs or encoded secrets.

* Always check for base64 or hex-encoded strings when analyzing binary dumps.

* UART monitoring can leak sensitive information if not properly secured.

---





