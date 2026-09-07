# System Design: Why is Kafka fast?

- **Topic:** SYSTEM DESIGN
- **Video:** [System Design: Why is Kafka fast?](https://www.youtube.com/watch?v=UNUz1-msbOM) (ByteByteGo)
- **Date:** 06 Sep 2026

## "Fast" ka matlab kya hai yahan?

- "Fast" word ambiguous hai — latency ki baat ho rahi hai ya **throughput** ki?
- Kafka **high throughput** ke liye optimized hai — kam time me bahut saare records move karna.
- Analogy: ek bada pipe jisme liquid beh raha hai — pipe ka diameter jitna bada, utna zyada volume flow hoga.
- Toh jab log kehte hain "Kafka fast hai", matlab Kafka **bahut saara data efficiently move** kar sakta hai.

## Kafka fast kyun hai? — 2 sabse important design decisions

Kafka me bahut saare optimizations hain, lekin ye 2 sabse zyada weight carry karte hain:

1. **Sequential I/O**
2. **Zero Copy principle** (efficiency focus)

## 1. Sequential I/O

### Misconception pehle clear karo

- Common galat dharna: "disk slow hai, memory fast hai."
- Sach ye hai ki speed **data access pattern** pe depend karti hai.

### Random vs Sequential access

| Access Pattern | Kya hota hai | Speed |
|---|---|---|
| **Random access** | Hard drive ka arm physically alag-alag locations pe jump karta hai | Slow — hundreds of **KB/s** (writes) |
| **Sequential access** | Data blocks ek ke baad ek read/write hote hain, arm jump nahi karta | Fast — hundreds of **MB/s** (writes) |

- Sequential access random se **several orders of magnitude faster** hai.

### Kafka isko kaise use karta hai?

- Kafka ka primary data structure hai **append-only log** — naya data hamesha file ke **end me add** hota hai.
- Ye access pattern purely **sequential** hai, isliye HDD pe bhi bahut fast.

### Cost advantage (bonus)

- HDD vs SSD: hard disk **1/3 price** me milti hai aur **~3x capacity** deti hai.
- Matlab Kafka ko **cheap disk space ka bada pool** milta hai, bina performance penalty ke.
- Isi wajah se Kafka messages ko **long time tak retain** kar sakta hai — ye feature Kafka se pehle ke messaging systems me uncommon tha.

## 2. Zero Copy

- Kafka ka kaam hi hai data ko **network → disk** aur **disk → network** move karna.
- Pages of data move karte waqt **excess copying eliminate** karna critical hai.
- Modern Unix OS already optimized hain disk-to-network transfer ke liye — Kafka isi ka fayda uthata hai.

### Without zero copy (disk se consumer tak data bhejna)

1. Data disk se **OS cache** me load hota hai.
2. OS cache se **Kafka application** me copy hota hai.
3. Kafka se **socket buffer** me copy hota hai.
4. Socket buffer se **NIC (network interface card) buffer** me copy hota hai.
5. Finally data network pe consumer ko send hota hai.

- Total: **4 copies + 2 system calls** — clearly inefficient.

### With zero copy

1. Data disk se **OS cache** me load hota hai (same step).
2. Kafka `sendfile()` system call use karta hai — OS directly **OS cache → NIC buffer** copy kar deta hai.

- Is optimized path me sirf **1 copy** hoti hai (OS cache → network card buffer).
- Modern network cards me ye copy **DMA (Direct Memory Access)** se hoti hai — **CPU involve hi nahi hota**, aur bhi efficient.

```text
Without zero copy:
Disk → OS cache → Kafka app → Socket buffer → NIC buffer → Network  (4 copies, 2 syscalls)

With zero copy:
Disk → OS cache → NIC buffer (via sendfile() + DMA) → Network      (1 copy, CPU idle)
```

## Key Takeaways

- Kafka "fast" = **high throughput**, latency ki guarantee nahi.
- **Sequential I/O** (append-only log) + **Zero copy** (`sendfile()` + DMA) — ye 2 cornerstones hain Kafka ki performance ke.
- Sequential access itna fast hai ki **cheap HDDs** pe bhi Kafka high performance + long message retention de deta hai.
- Kafka aur bhi techniques use karta hai hardware squeeze karne ke liye, lekin ye 2 sabse important hain.

> **Interview tip:** "Why is Kafka fast?" puchha jaye toh seedha 2 cheezein bolo — (1) append-only log se sequential disk I/O, (2) `sendfile()` based zero copy with DMA. Numbers quote karo: sequential writes ~100s of MB/s vs random writes ~100s of KB/s.
