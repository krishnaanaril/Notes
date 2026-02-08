# Rsync algorithm

- [Original paper by AndrewTridgell and Paul Mackerras (1996)](https://www.andrew.cmu.edu/course/15-749/READINGS/required/cas/tridgell96.pdf)

Below is a **clean, concise, step‑by‑step summary of how rsync works**, with citations from verified sources.

***

## ✅ **Step‑by‑Step Summary of How rsync Works**

Rsync synchronizes files efficiently by transferring only the **differences (deltas)** between source and destination. Here's how the process works internally:

***

### **1. Receiver splits its file into blocks**

The destination (receiver) divides its existing file into **non‑overlapping blocks**.  
Block size is chosen dynamically:

*   Small files → minimum block size (around 700 bytes)
*   Large files → block size ≈ square root of file length    [\[deepwiki.com\]](https://deepwiki.com/RsyncProject/rsync/2.2-delta-transfer)

***

### **2. Receiver computes two checksums per block**

For each block, the receiver computes:

1.  **Fast checksum (sum1)** — a 32‑bit **rolling checksum**
2.  **Strong checksum (sum2)** — a cryptographic hash such as **MD4, MD5, SHA‑1**    [\[deepwiki.com\]](https://deepwiki.com/RsyncProject/rsync/2.2-delta-transfer)

The receiver then sends these checksums (not block data) to the sender.

***

### **3. Sender scans its file with a sliding window**

The sender now scans its version of the file using a **sliding window** equal to the block size.

At each byte offset:

1.  Compute rolling checksum of the window
2.  Check if it matches any of the receiver’s weak checksums
3.  If weak checksum matches → verify using strong checksum    [\[rsync.samba.org\]](https://rsync.samba.org/tech_report/node2.html)

The rolling checksum allows extremely fast updates as the window moves by one byte at a time.

***

### **4. Sender identifies which parts match and which are new**

For each position:

*   If both checksums match → **block already exists at receiver**
*   If not → the sender marks the bytes as **literal data** (data that must be transferred)

This produces a sequence of “use block X” and “send literal bytes."    [\[rsync.samba.org\]](https://rsync.samba.org/tech_report/node2.html)

***

### **5. Sender sends a compact delta**

Instead of sending the whole file, the sender transmits:

*   References to blocks the receiver already has
*   Only the literal bytes that differ

This is the **delta**, which contains far less data than the full file.    [\[rsync.samba.org\]](https://rsync.samba.org/tech_report/node2.html)

***

### **6. Receiver reconstructs the updated file**

The receiver rebuilds the new file using:

*   Its existing blocks
*   The literal data received
*   The order and instructions sent by the sender

The final output matches the sender’s file exactly.    [\[rsync.samba.org\]](https://rsync.samba.org/tech_report/node2.html)

***

## 🎯 **In Simple Terms**

Rsync works like this:

1.  *Receiver:* “Here are fingerprints of all my blocks.”
2.  *Sender:* “I’ll scan my file and find which blocks match yours.”
3.  *Sender:* “I’ll send you only the pieces you don’t already have.”
4.  *Receiver:* “I’ll assemble the final file from your instructions.”

***