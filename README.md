# Digital Payment Processing Rails – U.S. Market

This repository documents the various digital payment processing rails used in the United States. It includes technical overviews, workflows, architecture diagrams, and regulatory compliance considerations for ACH, Wire, RTP, and card-based transactions.

---

## 🔁 U.S. Payment Rails Overview

The United States utilizes multiple electronic payment networks for transferring funds between financial institutions. These include:

- **ACH (Automated Clearing House)** – Batch-processed, low-cost, non-urgent payments (e.g., payroll, bill pay)
- **Wire Transfers** – Immediate, high-value fund transfers (e.g., real estate, institutional payments)
- **RTP (Real-Time Payments)** – Instant, irrevocable payments via The Clearing House (TCH)
- **FedNow** – Federal Reserve's real-time settlement system (launched 2023)
- **Card Networks** – Credit/debit card clearing and settlement (e.g., Visa, Mastercard)

---

## 📐 RTP Framework & Workflow (The Clearing House)

The Real-Time Payments (RTP) rail is the most modern U.S. rail, operating 24/7/365. Key characteristics include:

### Architecture Components

- Originating Bank (Sender)
- Receiving Bank (Receiver)
- TCH RTP Network
- ISO 20022 Messaging Layer
- Pre-funded Settlement Accounts
- Directory and Authentication Services

### End-to-End Workflow

1. **Payment Initiation** – Initiated by a customer or business
2. **Validation & Authorization** – Identity, KYC/AML, and balance verification
3. **Message Formatting** – ISO 20022 messages (e.g., `pain.001`, `pacs.008`)
4. **Clearing & Routing** – TCH RTP routes messages in real-time
5. **Settlement** – Funds are settled instantly using prefunded positions
6. **Notification** – Both sender and receiver are notified in real-time

---

## 📊 ISO 20022 Message Types Used in RTP

| ISO Code   | Name                        | Purpose                          |
|------------|-----------------------------|----------------------------------|
| `pain.001` | Credit Transfer Initiation  | Payment instruction              |
| `pacs.002` | Payment Status Report       | Acknowledgment and rejection     |
| `pacs.008` | Financial Credit Transfer   | Actual settlement transaction    |
| `camt.056` | Reversal Request            | Request to reverse a transaction |
| `camt.052` | Account Notification        | Statement and balance report     |

---

## 🏛️ Industry Standards and Governance

- **TCH RTP Rulebook**
- **NACHA Operating Rules**
- **ISO 20022 Global Standard**
- **Federal Reserve Payment Guidelines**
- **FFIEC Risk Management for Payment Systems**

---

## 🛡️ Risk & Compliance Controls

- Real-time fraud screening
- Velocity and amount-based risk rules
- OFAC sanctions screening
- Customer authentication and tokenization
- Audit trails and end-to-end message traceability

---

## 📁 Repository Contents

- `documentation/01_Payment_System_Overview.pdf`  
- `documentation/02_ACH_Payment_Flow.pdf`  
- `documentation/03_Wire_Transfer_Process.pdf`  
- `documentation/04_SWIFT_Network_Guide.pdf`  
- `documentation/05_RTP_System_Architecture.pdf`

---

This repository is a complete reference for fintech architects, payment engineers, and compliance analysts building or maintaining U.S.-based digital payment infrastructure.
