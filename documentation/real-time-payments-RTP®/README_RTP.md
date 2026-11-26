# Real-Time Payments (RTP) System – Technical Overview

This documentation provides a comprehensive guide to understanding the Real-Time Payments (RTP) system architecture, message workflows, network participants, and industry standards.

## 🔍 Overview

Real-Time Payments (RTP) is a modern electronic payment rail that allows the instantaneous transfer of funds between bank accounts. In the U.S., The Clearing House (TCH) RTP network supports 24/7/365 settlement, offering finality and transparency for financial institutions and consumers.

## 📐 RTP System Architecture

Key components of RTP architecture include:
- **Sender Bank (Participant)**
- **Receiver Bank (Participant)**
- **The Clearing House (TCH) RTP Network**
- **Directory Service**
- **Core Banking Integration**
- **Fraud and Risk Systems**
- **Message Queueing and Orchestration Layer**

## 🔄 Standard RTP Workflow

1. **Payment Initiation** – Customer or system triggers payment via digital channel.
2. **Authorization** – Bank validates payer details, balance, and authorization.
3. **Message Transmission** – Bank sends ISO 20022-compliant RTP message to TCH.
4. **Clearing** – TCH validates and routes message to receiving bank.
5. **Settlement** – Instant settlement using pre-funded positions.
6. **Notification** – Both parties receive confirmation with unique transaction ID.

## 📊 Common RTP Message Types (ISO 20022)

| Message Type | Description                 | ISO Code       |
|--------------|-----------------------------|----------------|
| Credit Transfer | Payment initiation           | `pain.001`     |
| Payment Confirmation | Acknowledgement to sender | `pacs.002`     |
| Settlement Request | Transfer of funds          | `pacs.008`     |
| Reversal | Payment reversal              | `camt.056`     |
| Notification | Credit notification to payee  | `camt.052`     |

## 🏛️ Industry Standards

- **ISO 20022**: Global standard for financial messaging.
- **TCH RTP Rulebook**: Governs network participation, processing, and compliance.
- **FedNow (complementary)**: Federal Reserve's instant payment service in the U.S.
- **FFIEC & OCC Guidelines**: Risk and operational recommendations for RTP adoption.

## 🛡️ Risk and Compliance Controls

- Real-time fraud monitoring
- Pre-transaction screening (e.g., OFAC lists)
- Threshold and velocity checks
- Instant dispute resolution framework
- End-to-end traceability with transaction audit trails

## 📚 Official sources

The RTP operating rules, message specifications and playbooks are published by The Clearing House. See [../References.md](../References.md) for links.

---

This RTP document is part of the broader **Digital Payments System Blueprint** repository.
