# 🚗 VANET Secure Routing Protocol Implementation (NS-3 + Python)

This project implements and simulates a **secure routing protocol for Vehicular Ad Hoc Networks (VANETs)** using **digital signatures** and **cryptographic hash functions**. It integrates **NS-3 network simulation** with a **Python-based framework** for simulating vehicle mobility, message security, attack detection, and performance metrics analysis.

---

## 🗂️ Project Structure

```
VANET-Secure-Routing/
├── ns3_sim/
│   └── Main.py                 # NS-3 + PyCrypto-based simulation
├── python_sim/
│   └── NS3_Integration.py      # Mobility, hash comparison, attack simulation
├── README.md                   # This documentation
```

---

## 🛠️ Configuration Files & Simulation Setup

### 📄 `config/simulation_config.yaml`

Example:

```yaml
vehicles:
  count: 4
  speeds: [65, 50, 35, 20]
  positions: [[0, 0], [10, 20], [30, 50], [10, 50]]
network:
  nodes: 3
  base_ip: "10.0.0.0"
  mask: "255.255.255.0"
security:
  enable_signature: true
  enable_hashing: true
attacks:
  tamper_detection: true
  replay_attack: false
  blackhole_simulation: false
```

> Customize the simulation by editing vehicle speeds, attack flags, and network configurations.

---

## 📖 Documentation & Implementation Overview

### 🔧 NS-3 Simulation (`ns3_sim/secure_vanet_sim.py`)

* **Language**: Python bindings for NS-3
* **Functionality**:

  * Creates ad-hoc WiFi network with `NodeContainer`
  * Installs mobility model, IP stack, and echo applications
  * Signs and verifies messages using **RSA + SHA-256**
* **Security Layer**:

  * Digital signatures with `pkcs1_15` (PyCrypto)
  * Verifies message authenticity before network forwarding

### 🧠 Python Simulation (`python_sim/secure_vanet_analysis.py`)

* **Simulates**:

  * Vehicle mobility and collision detection
  * Cryptographic hashing using multiple algorithms: `SHA-256`, `MD5`, `SHA-1`, `SHA-3`, `BLAKE2`
  * Message tampering, detection, and metrics logging
* **Classes**:

  * `Vehicle`: handles mobility, message signing, and verification
  * `Metrics`: tracks total messages, tampered detections, and detection rate
* **Visualization**:

  * Uses `matplotlib` and `pandas` to compare hash function performance
  * Boxplots for execution time per hash algorithm

---

## ▶️ How to Run

### 📌 Prerequisites

* **NS-3** installed with Python bindings
* Required packages:

  ```bash
  pip install pycryptodome pandas matplotlib
  ```

### 💡 Run NS-3 Simulation

```bash
cd ns3_sim
python NS3_Integration.py
```

### 💡 Run Python-based Security Simulation

```bash
cd python_sim
python Main.py
```

---

## 📊 Protocol Performance & Security Report

### ✅ Features Evaluated:

* **Digital signature verification accuracy**
* **Message tampering detection**
* **Hash algorithm speed and efficiency**

### 📌 Attack Scenarios Simulated:

| Attack Type      | Description                            | Outcome                             |
| ---------------- | -------------------------------------- | ----------------------------------- |
| Tampering        | Modifying message fields (e.g., speed) | Detected via hash + signature check |
| Replay Attack ✖️ | (not yet implemented)                  | Planned for future expansion        |
| Blackhole ✖️     | (not yet implemented)                  | Planned for future expansion        |

### 📈 Performance Metrics:

* **Detection Rate** = `Tampered Messages Detected / Total Messages`
* **Hash Speed Benchmark**:

  * `SHA-256` is most reliable
  * `BLAKE2b` and `SHA-3` offer good security with speed trade-offs
* **Visualization**:

  * Boxplot of hash computation times for statistical comparison

---

## 📌 Example Output

```
Vehicle V2 received message from V1
Message is authentic and unaltered.

Vehicle V2 received message from V1
Message FAILED integrity or signature verification!

Total Messages: 200
Tampered Detected: 40
Detection Rate: 20.00%
```

---

## 🤝 Contribution

Contributions are welcome. Please fork the repository and submit a pull request. Suggested improvements:

* Add blackhole and replay attack simulations
* Extend GUI visualization
* Integrate results into a dashboard

---

## ⚠️ Disclaimer

This project is intended **solely for educational and research purposes**. The implementation demonstrates secure communication concepts within Vehicular Ad Hoc Networks (VANETs) using cryptographic techniques and simulated attack scenarios. It **does not guarantee real-world security** and **should not be used in production or safety-critical environments** without extensive testing, validation, and formal verification.

Use of cryptographic methods such as RSA and hash functions is **simplified** for simulation. Real-world VANET deployments require rigorous compliance with established standards (e.g., IEEE 1609.2, ETSI ITS) and may involve hardware-based trust modules, VPKI infrastructure, and authenticated broadcast protocols.

> By using this project, you acknowledge that the authors are **not responsible for any misuse, data loss, or system issues** resulting from running or modifying the code.

---
