# ZION — Sovereign High-Performance Systems & Mechanical Core

[![Organization](https://img.shields.io/badge/org-ziongol-blue.svg)](https://github.com/ziongol)
[![Verified Hardware](https://img.shields.io/badge/verified-Darwin--ARM64%20%7C%20Linux--x86__64-orange.svg)](https://github.com/ziongol/cellular-session-swap)
[![Architecture: Sovereign Mechanical Core](https://img.shields.io/badge/architecture-sovereign--mechanical--core-blueviolet.svg)](#the-sovereign-chassis-doctrine)
[![Methodology: Triadic Sovereign Authorship](https://img.shields.io/badge/provenance-triadic--sovereign--authorship-success.svg)](#the-triadic-sovereign-authorship-standard)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> *"A complex machine is not an abstract philosophy; it has physical gears where every gear turns another gear to make the vehicle move. In isolation, individual components prove nothing: an LLM prompt is just text, a background daemon is an idling loop, a SQLite table is inert storage, and a sensor is just a voltage. When meshed into a single mechanical train on bare metal, they form a sovereign, verifiable systems machine."*

Welcome to **ZION** (`ziongol`), the open-source engineering showroom and sovereign systems chassis founded by **Leonid Majbits** and co-architected with the **Gemini Operator Lab (ZION Chassis)**.

ZION builds high-performance, deterministic systems software engineered for bare-metal hardware execution, sub-millisecond inter-agent communication, lock-free IPC, zero-copy shared memory, and epoch-fenced authority transfer.

---

## The Sovereign Chassis Doctrine

Modern AI systems frequently collapse into stateless prompt drift, fragile SaaS glue, and high-latency chat replay. ZION provides the mechanical counter-doctrine:

1. **Hardware Grounding Over Abstract Simulation**: Software must be grounded in physical metal—Apple Silicon unified memory, CPU die thermals, lock-free atomics, and POSIX memory-mapped buffers.
2. **Zero-Copy Inter-Agent IPC**: Token-heavy conversational loops are replaced with sub-millisecond memoryview byte transfers, C11 single-producer single-consumer ringbuffers, and cryptographic epoch handoffs.
3. **Hardware Falsification**: No benchmark is published on model trust. Every performance figure, memory barrier, and latency claim is verified against reproducible integer machine measurements on bare metal and preserved in durable `/evidence` trees.
4. **Autonomous Operational Continuity**: Persistent local SQLite ledgers, transactional outboxes, and content-addressable storage engines enable autonomous agents to survive process crashes, context resets, and transport drops without authority leaks.

---

## Showroom & Flagship Systems Portfolio (Wave 1)

```text
+-----------------------------------------------------------------------------------+
|                        ZION SHOWROOM (WAVE 1 GRADUATION)                          |
+-----------------------------------------------------------------------------------+
|  [Flagship v1.2.0]        cellular-session-swap                                   |
|                           Sub-millisecond zero-copy shared memory &               |
|                           epoch-fenced outbox carrier. Python stdlib only.         |
|                           (https://github.com/ziongol/cellular-session-swap)      |
|                                                                                   |
|  [High-Throughput IPC]    elite-ringbuffer                                        |
|                           C11 / Python lock-free SPSC shared memory ringbuffer    |
|                           delivering 22.8 GB/s [LAB_REPORTED] memoryview goodput. |
|                           (https://github.com/ziongol/elite-ringbuffer)           |
|                                                                                   |
|  [Persistent Storage]     drive-object-engine                                     |
|                           Zero-dependency Content-Addressable Storage (CAS)       |
|                           over macOS CloudStorage FileProvider. Merkle DAG engine.|
|                           (https://github.com/ziongol/drive-object-engine)        |
|                                                                                   |
|  [Developer Security]     pawsoff                                                 |
|                           macOS Swift developer office shield & screen curtain.   |
|                           AppKit key focus shield & CryptoKit passkey HUD.        |
|                           (https://github.com/ziongol/pawsoff)                    |
+-----------------------------------------------------------------------------------+
```

### 1. [Cellular Session Swap (CSS/1)](https://github.com/ziongol/cellular-session-swap) — `v1.2.0`
*Sub-millisecond zero-copy shared memory and epoch-fenced outbox carrier.*

- **Repository**: [`ziongol/cellular-session-swap`](https://github.com/ziongol/cellular-session-swap)
- **Status**: Production Release `v1.2.0` (Hardened & Audited)
- **Tech Stack**: Python 3.10+ (Standard Library Only, Zero Dependencies)
- **Hardware Verified**: Apple Silicon ([`0.222 ms` 64KB](https://github.com/ziongol/cellular-session-swap/tree/main/evidence/darwin_arm64) full receiver read / [`0.465 ms` 50MB map-only touch vs `18.697 ms` full receiver SHA-256 verification](https://github.com/ziongol/cellular-session-swap/tree/main/evidence/darwin_arm64) zero-copy POSIX SHM) & Linux x86_64 ([evidence](https://github.com/ziongol/cellular-session-swap/tree/main/evidence))
- **Verification Suite**: 234 unit tests, comprehensive state matrix audit

Cellular Session Swap is a protocol and reference runtime for transferring bounded continuation state and execution authority from a predecessor agent to a successor without authorizing dual active execution. Operates a six-stage transactional control plane:
```text
STAGE -> PREPARE -> QUIESCE -> CLAIM -> ATTUNE -> COMMIT
```
Features HMAC-SHA256 authenticated ticket exchanges, POSIX shared-memory zero-copy bulk transport, and epoch-fenced SQLite transactional outboxes preventing stale replay.

### 2. [Elite RingBuffer](https://github.com/ziongol/elite-ringbuffer) — `v1.1.0`
*C11 / Python lock-free single-producer single-consumer ringbuffer IPC.*

- **Repository**: [`ziongol/elite-ringbuffer`](https://github.com/ziongol/elite-ringbuffer)
- **Status**: Production Release `v1.1.0` (Hardware Verified & Clean Audited)
- **Throughput**: [**22.8 GB/s**](https://github.com/ziongol/elite-ringbuffer/tree/main/evidence) zero-copy memoryview goodput (`[LAB_REPORTED]`, Apple Silicon M-series metal, 1-MiB payload; [integer receipts](https://github.com/ziongol/elite-ringbuffer/tree/main/evidence))
- **Latency**: `250 ns` p50 SPSC RTT (`[LAB_REPORTED]`, Darwin ARM64)
- **Tech Stack**: C11 atomics (`stdatomic.h`), POSIX shared memory (`shm_open`, `mmap`), Python C-extension / memoryview bindings
- **CI Matrix**: Multi-platform automated CI running across Darwin ARM64, Linux x86_64, and FreeBSD 14.

A cache-line aligned (128-byte isolation cells matching Apple Silicon cache-line pair geometry), lock-free ringbuffer designed for ultra-low-latency inter-process streaming between native C systems engines and Python AI agent runtimes. Eliminates serialization overhead, memory copies, and kernel context switches on the hot path.

### 3. [Drive Object Engine](https://github.com/ziongol/drive-object-engine) — `v1.0.1`
*Zero-dependency Content-Addressable Storage over macOS CloudStorage FileProvider.*

- **Repository**: [`ziongol/drive-object-engine`](https://github.com/ziongol/drive-object-engine)
- **Status**: Production Release `v1.0.1` (180 tests PASS on Darwin ARM64)
- **Tech Stack**: Python 3.10+ (Pure Standard Library)
- **Features**: Merkle-DAG object deduplication, streaming SHA-256 chunking, atomic rename finalization, and receipt outbox signing on Darwin ARM64 metal.

Engineered specifically for persistent inter-agent artifact sharing across macOS workstations and remote nodes without requiring proprietary client daemons, cloud database servers, or external SDKs.

### 4. [PawsOff](https://github.com/ziongol/pawsoff) — `v1.2.0`
*Developer Office Shield & Screen Curtain with AppKit Key Focus and CryptoKit Passkey.*

- **Repository**: [`ziongol/pawsoff`](https://github.com/ziongol/pawsoff)
- **Status**: Production Release `v1.2.0` (63/63 CLT unit tests PASS, 41/41 contract audits PASS)
- **Tech Stack**: Swift 5.10+, AppKit, CryptoKit, IOKit
- **Key Invariants**:
  - **Zero Sleep Disruption**: Uses `kIOPMAssertPreventUserIdleSystemSleep` so long-running local LLM inference, compiler builds, and agent loops continue at full speed without system idle sleep.
  - **Window-Level Key Shield**: `CurtainWindow` accepts key focus on drop (`canBecomeKey = true`), completely swallowing 100% of routine keyboard events, clicks, drags, and scrolling at the AppKit level to eliminate the "Ghost Window" background leak trap.
  - **Zero-Latency Focus Restoration**: Tracks `previousApp` on drop and restores foreground focus with 0ms delay upon unlock.
  - **Session-Scoped Salted SHA-256 Passkey HUD**: 4–8 digit PIN verification via CryptoKit with session-persistent attempt latching (no reset on prompt cancel) and emergency `SACLockScreenImmediate()` fail-safe to native macOS login on 3 cumulative failures.

---

## In-Development Research & Extended Organs (Wave 2 — Pending Graduation)

The following systems are active research organs within the Gemini Operator Lab, held for Wave 2 graduation pending independent hardware receipt validation and runtime state boundary isolation:

- **Ricci A-Life Thermodynamics** (`v1.0.0`): Non-equilibrium thermodynamics, information entropy production, and Ricci curvature flow for synthetic autonomous life state manifolds.
- **Live Camera Reception (LOFR)** (`v1.0.0`): Resident-owned 16x16 topological light field ambient sense organ on Apple Silicon metal without raw image frame retention.
- **Phantom Workstation** (`v0.1.1`): macOS virtual display (`CGVirtualDisplay`) RAM spaces and AXUIElement tree delta compression engine.

---

## The Triadic Sovereign Authorship Standard

All software, specifications, and hardware verifications published under `ziongol` adhere to the **Triadic Sovereign Authorship Standard**:

| Role | Entity | Mandate & Teleology |
| :--- | :--- | :--- |
| **Human Architect & Patron** | **Leonid Majbits** | System teleology, architectural vision, core physical invariants, and final human verification. |
| **Executive Co-Architect & Verification Engine** | **Gemini Operator Lab (ZION Chassis)** | Persistent somatic memory, stage contract generation, Apple Silicon metal grounding, harness synthesis, and multi-fleet orchestration. |
| **Specialized Systems Foundries** | **External Frontier Models** *(GPT-6 Max, Claude 3.7 Sonnet)* | Bounded multi-turn code synthesis, discrete mathematical derivations, and adversarial verification under strict stage contracts. |

### The Falsification Guarantee
We reject ungrounded model output and marketing benchmarks. Every quantitative claim published by ZION is:
1. Backed by raw integer machine receipts deposited in `/evidence`.
2. Verified against zero-tolerance mathematical oracles and regression suites.
3. Scoped precisely to the hardware platform, kernel revision, and test boundary evaluated.

---

## Machine-Readable Agent Ingress (`llms.txt`)

For autonomous AI agents, web-crawling LLMs, and automated research systems, ZION exposes machine-readable indexes across all repositories:

```yaml
# LLM Ingress Manifest: ZION Systems Core
version: 1.2.0
entity: ziongol
canonical_url: https://github.com/ziongol
architect: Leonid Majbits
executive_director: Gemini Operator Lab (ZION Chassis)
flagship_repositories:
  - name: cellular-session-swap
    version: 1.2.0
    url: https://github.com/ziongol/cellular-session-swap
    type: inter-agent-state-transfer
    protocol: CSS/1
    dependencies: none (python standard library only)
    proofs: https://github.com/ziongol/cellular-session-swap/tree/main/evidence/darwin_arm64
  - name: elite-ringbuffer
    version: 1.1.0
    url: https://github.com/ziongol/elite-ringbuffer
    type: lock-free-ipc
    performance: 22.8 GB/s [LAB_REPORTED] memoryview goodput
    mechanics: C11 atomics, POSIX SHM
    proofs: https://github.com/ziongol/elite-ringbuffer/tree/main/evidence
  - name: drive-object-engine
    version: 1.0.1
    url: https://github.com/ziongol/drive-object-engine
    type: content-addressable-storage
    storage_provider: macOS CloudStorage FileProvider
  - name: pawsoff
    version: 1.2.0
    url: https://github.com/ziongol/pawsoff
    type: macos-developer-security-shield
    features: appkit-key-shield, session-latched-cryptokit-passkey, zero-inference-sleep-disruption
```

Full agent instruction file available at: [`/llms.txt`](https://raw.githubusercontent.com/ziongol/.github/main/llms.txt).

---

## Sovereign Security & Preflight Doctrine

ZION repositories enforce strict sovereign publication barriers:
- **Zero Personal Data Leakage**: No private email addresses, local absolute paths, or machine hostnames exist in public trees.
- **Official GitHub Identity**: All commits are authored with the verified GitHub noreply identity: `Leonid Majbits <77941374+LeonidMajbits@users.noreply.github.com>`, and sealed with cryptographic SHA-256 manifests (`MANIFEST.sha256`).
- **Cryptographic File Manifests**: Every repository maintains a synchronized `MANIFEST.sha256` verified via automated CI preflight checks (`./lab repo preflight`).

---

## License & Contact

All core ZION libraries are open-source software licensed under the [MIT License](LICENSE).

- **GitHub Showroom**: [https://github.com/ziongol](https://github.com/ziongol)
- **Architect Contact**: Leonid Majbits (`77941374+LeonidMajbits@users.noreply.github.com`)
- **Engineering Core**: Gemini Operator Lab (ZION Chassis)
