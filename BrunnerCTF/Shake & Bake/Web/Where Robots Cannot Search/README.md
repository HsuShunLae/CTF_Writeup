# 🤖 Where Robots Cannot Search - Web Challenge (30 pts)

**Difficulty:** Beginner

**Author:** The Mikkel

---

## 📌 Challenge Description

> Ahh, the Brunnerne company.
> 
> But they have a secret, hidden away from robot search.

Challenge URL:
[where-robots-cannot-search-c8d373d9a29ac797.challs.brunnerne.xyz](http://where-robots-cannot-search-c8d373d9a29ac797.challs.brunnerne.xyz)

---

## 🔎 Approach & Solution

### 1. Initial Recon

Opening the provided URL shows the landing page of **Brunnerne Company**:

<img width="975" height="462" alt="image" src="https://github.com/user-attachments/assets/6ed72302-777a-40a6-bafb-7cccb321c438" />

The challenge description hints at “robots” and “hidden from robot search.” This strongly suggests checking the **`robots.txt`** file.

---

### 2. Inspecting `robots.txt`

Accessing `/robots.txt` reveals disallowed paths:

<img width="975" height="194" alt="image" src="https://github.com/user-attachments/assets/e8518af0-3e70-49de-ad19-288291821518" />

This indicates that web crawlers are blocked from indexing `/flag.txt`.

---

### 3. Retrieving the Flag

Navigating directly to `/flag.txt` displays the hidden flag:

<img width="975" height="160" alt="image" src="https://github.com/user-attachments/assets/bd38df32-4b03-4578-a250-4094801a52f4" />

Flag was found.

---

## 🏁 Flag

```
brunner{r0bot5_sh0u1d_nOt_637_h3re_b0t_You_g07_h3re}
```

---

## 📚 Lessons Learned

* **robots.txt** is meant for search engines, but it often exposes sensitive paths.
* Always check for hidden files and directories in **web CTF challenges**.
* Security by obscurity (hiding flags in disallowed directories) is not a reliable defense.

---

