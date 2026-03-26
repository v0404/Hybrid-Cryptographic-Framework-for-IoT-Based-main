# 🚀 Secure Smart Surveillance System  
**Context-Aware Cryptographic Framework for IoT CCTV**

---

## 📌 Overview
A secure IoT-based CCTV system that uses **context-aware cryptography** instead of uniform encryption.  
It dynamically selects encryption, signing, and key strategies based on event sensitivity.

Built using a **Camera → Gateway → Cloud** architecture with Docker-based simulation and real webcam input.

---

## 🔐 Key Idea
Instead of one encryption for all data, this system uses:

| Context | Encryption | Signing | Key Class |
|--------|-----------|--------|----------|
| LOW_LATENCY_ALERT | AES-128-GCM | Ed25519 | K1 |
| HIGH_VALUE_IMAGE | AES-256-GCM | Ed25519 | K2 |
| CRITICAL_EVENT | AES-256-GCM | RSA-PSS | K3 |

👉 This ensures **performance + security optimization**.

---

## ✨ Features
- 📷 Real-time webcam capture with motion detection  
- 🔐 AES-GCM encryption (128/256-bit)  
- 🔑 RSA-OAEP secure key exchange  
- ✍️ Dual signatures (Ed25519 + RSA-PSS)  
- 🔄 Multi-class N-Key rotation (K1/K2/K3)  
- 🧠 Context-aware crypto policy selection  
- 🛡️ Replay attack protection (UUID + timestamp)  
- 🚫 Anti-downgrade protection (policy-bound signatures)  
- 📦 Docker-based IoT simulation  

---

## 🏗️ Architecture
```
Camera → Gateway → Cloud

Camera:
  - Capture + classify context
  - Encrypt + sign

Gateway:
  - Verify signatures (no decryption)
  - Forward valid packets

Cloud:
  - Decrypt + store
  - Replay protection
```

---

## 📦 Project Structure
```
secure-cctv/
├── docker-compose.yml
├── generate_keys.py
├── capture_host.py
├── display_host.py
├── camera/
├── gateway/
├── cloud/
├── keys/
└── shared/
```

---

## ⚙️ How It Works
1. 📸 Camera captures frames  
2. 🧠 Classifies context (alert/image/critical)  
3. 🔐 Applies corresponding crypto policy  
4. ✍️ Signs packet (context-bound)  
5. 📡 Gateway verifies (no decryption)  
6. ☁️ Cloud decrypts and stores securely  

---

## 🔑 Cryptographic Design
- AES-GCM → Confidentiality + Integrity  
- RSA-OAEP → Secure key wrapping  
- Ed25519 → Fast lightweight signatures  
- RSA-PSS → High-security signatures  
- Context-bound signatures prevent tampering  

---

## 🔄 Key Rotation
- 3 key classes → K1, K2, K3  
- Each has 5 keys  
- Rotates every **60 seconds**  
- Ensures **key isolation + compromise resistance**

---

## 🛡️ Security
Protects against:
- Eavesdropping  
- Replay attacks  
- Man-in-the-middle  
- Impersonation  
- Downgrade attacks  

---

## 📊 Performance
- ⚡ ~2.15 ms per frame (~76 KB)  
- 📉 Only 16 bytes encryption overhead  
- 🎯 Works in real-time (30 FPS compatible)  

---

## ▶️ Run the Project
```bash
docker-compose up --build
```

---

## 📈 Sample Output
```
[IMAGE] 2.13ms | AES-256-GCM + Ed25519
[ALERT] 0.35ms | AES-128-GCM + Ed25519
[CRITICAL] 2.45ms | AES-256-GCM + RSA-PSS
```

---

## ⚠️ Limitations
- No Perfect Forward Secrecy (yet)  
- Static context policy  
- Metadata not encrypted  
- Single gateway dependency  

---

## 🔮 Future Work
- ECDHE (Perfect Forward Secrecy)  
- ML-based context detection  
- Multi-camera scaling  
- Blockchain audit logs  
- Hardware deployment (Raspberry Pi / ESP32)  

---

## 🎯 Conclusion
This project demonstrates that **context-aware cryptographic specialization with N-key rotation** can provide:

- High security  
- Low latency  
- Real-time feasibility  

👉 A strong foundation for next-generation **secure surveillance systems**.

---

## ⭐ If you like this project
Give it a ⭐ on GitHub!
