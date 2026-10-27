# TCFrameForge Pro (v1.0.0)
> **Autonomous Digital Product Factory — Catalog Record #446**  
> **CCSDS 232.0-B-4 & ISO 22666 Telecommand Space Data Link Protocol Studio & Compliance Auditor**

---

## 🌟 Overview
**TCFrameForge Pro** is an aerospace-grade telecommand uplink protocol synthesizer, MAP demultiplexer, bitfield dissector, Frame Acceptance and Reporting Mechanism (FARM-1) emulator, and 10-point normative compliance engine strictly implementing **CCSDS 232.0-B-4** (*Telecommand Space Data Link Protocol*) and **ISO 22666:2016**.

Designed for smallsat developers, CubeSat ground controllers, COTS/EGSE ground station software engineers, and aerospace telecommunication researchers, TCFrameForge Pro automates telecommand frame authoring, Type-A vs Type-B bypass handling, MAP segmentation, FARM sliding window tracking, and CRC-16 CCITT frame error control validation.

---

## 🚀 Key Features

* **Normative CCSDS 232.0-B-4 Primary Header Engine**:
  - Full 40-bit (5 octet) primary header generation and dissection.
  - TFVN (`00`), Bypass Flag (Type-A sequence-controlled vs Type-B expedited), Control Command Flag, 10-bit Spacecraft ID (SCID 0..1023), 6-bit Virtual Channel ID (VCID 0..63), 10-bit Frame Length ($L-1$), and 8-bit Frame Sequence Number $N(S)$.
* **Multiplexer Access Point (MAP) Segmenter**:
  - Optional 1-octet Segment Header supporting 2-bit Sequence Flags (`01` First, `00` Continuing, `10` Last, `11` Unsegmented) and 6-bit MAP ID (0..63).
* **FARM-1 Receiver State Machine Emulator**:
  - Full COP-1 Frame Acceptance and Reporting Mechanism emulator tracking $V(R)$, sliding acceptance window $W$ (10..64 frames), Retransmit flags, and Lockout recovery via Unlock commands.
* **Dual-Language High-Performance Implementations**:
  - **JavaScript ES6 Web Engine (`tc-engine.js` & `tc-auditor.js`)**: Powers zero-dependency in-browser telecommand operations consoles and Mission Control dashboards.
  - **Python 3 Standalone CLI (`tc_cli.py`)**: Zero-dependency CLI tool for automated EGSE uplink testing, burst generation, and CI/CD validation.
* **10-Point Normative Aerospace Audit Engine**:
  - Automated rules `TC-001` through `TC-010` verifying bitfield masks, pointer limits, counter continuities, and CRC-16 integrity.
* **Interactive Mission Operations Web Studio**:
  - Live parameter synthesis, FARM-1 execution loop, color-coded hex dissection, and interactive audit scorecards.

---

## 📁 Repository & Directory Layout

```
2026-10-17 — TCFrameForge Pro/
├── README.md                               # Master technical documentation
├── PROGRESS_REPORT.md                      # Factory cycle release & validation report
├── source-code/
│   ├── index.html                          # Mission Control web operations console
│   ├── tc-engine.js                        # JavaScript ES6 TC synthesis & dissection engine
│   ├── tc-auditor.js                       # 10-point normative compliance auditor
│   ├── tc_cli.py                           # Python 3 CLI telecommand tool
│   └── test_runner.py                      # 10-suite automated regression test runner
├── build/
│   └── tc-frame-forge-pro-v1.0.0.zip       # Complete standalone production distribution
├── documentation/
│   ├── CCSDS_TC_SPECIFICATION.md           # Deep-dive protocol architecture specification
│   └── TC_COMPLIANCE_MATRIX.md             # 10-point normative requirements traceability matrix
└── screenshots/
    ├── architecture-diagram.svg            # Protocol pipeline & FARM-1 architecture diagram
    └── tc-studio-preview.svg               # Mission Control UI preview graphic
```

---

## 🛠️ Quick Start & CLI Usage

### 1. Run Automated Test Suite (10/10 PASS)
```bash
python3 source-code/test_runner.py
```

### 2. Synthesize TC Frame via CLI
```bash
python3 source-code/tc_cli.py --mode frame --scid 42 --vcid 0 --ns 0 --payload "CMD=REBOOT_SYS VAL=EPS"
```

### 3. Generate Multi-Frame Telecommand Sequence
```bash
python3 source-code/tc_cli.py --mode burst --count 5 --scid 42
```

### 4. Audit Uplink Frame for CCSDS 232.0 Compliance
```bash
python3 source-code/tc_cli.py --mode audit --hex 002A002A00C0434D44...
```

---

## 🛡️ Normative Audit Scorecard (10/10 PASS)

| Rule ID | Clause | Rule Description | Status |
| :--- | :--- | :--- | :--- |
| **TC-001** | §4.1.2.2.2 | Transfer Frame Version Number equals `00` | **PASS** |
| **TC-002** | §4.1.2.3.2 | Bypass Flag & Control Flag valid combination | **PASS** |
| **TC-003** | §4.1.2.4.2 | Reserved Spare bits (bits 4-5) set to `00` | **PASS** |
| **TC-004** | §4.1.2.5.2 | Spacecraft ID in 10-bit range (0..1023) | **PASS** |
| **TC-005** | §4.1.2.6.2 | Virtual Channel ID in 6-bit range (0..63) | **PASS** |
| **TC-006** | §4.1.2.7.2 | Frame Length matches actual size minus 1 | **PASS** |
| **TC-007** | §4.1.2.8.2 | Frame Sequence Number $N(S)$ modulo-256 for Type-A; 0 for Type-B | **PASS** |
| **TC-008** | §4.1.3.2 | Segment Header Sequence Flags & MAP ID validity | **PASS** |
| **TC-009** | §4.1.4.2 | CRC-16 CCITT Frame Error Control Field checksum | **PASS** |
| **TC-010** | §4.1.2.1 | Maximum frame length $\le 1024$ octets | **PASS** |

---

## 💼 Commercialization & Monetization
* **Target Audience**: Commercial Smallsat & CubeSat operators, aerospace defense contractors, EGSE/COTS ground station tool vendors, university satellite teams.
* **Pricing Tier**:
  - **Community Tier (Free / OSS)**: Core CLI and basic JavaScript synthesizer.
  - **Commercial Flight Team License ($1,490/seat)**: Full studio GUI, automated EGSE integration hooks, custom mission parameter profiles, and formal normative audit verification reports.
  - **Enterprise Ground Station Site License ($6,800/unlimited)**: Multi-satellite constellation telemetry streaming, automated CI/CD pipeline plugins, and dedicated protocol customization support.
