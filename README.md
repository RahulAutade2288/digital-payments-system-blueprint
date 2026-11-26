# Digital Payments System Blueprint: U.S. Rails

A practical guide to the main U.S. payment rails (ACH, Fedwire, FedNow, RTP, SWIFT and Zelle), paired with Java sample code that shows the processing flows a bank runs on each one.

## The rails at a glance

| Rail | Operator | Speed | Typical use |
|------|----------|-------|-------------|
| **ACH** | Nacha rules; Fed and EPN operators | Batch, same day or next day | Payroll, bill pay, direct debits |
| **Fedwire Funds** | Federal Reserve | Real-time gross settlement | High-value and time-critical transfers |
| **FedNow** | Federal Reserve | Instant, 24x7x365 | Instant credit transfers between banks |
| **RTP** | The Clearing House | Instant, 24x7x365 | Instant payments and request for payment |
| **SWIFT** | SWIFT network | Hours to days, via correspondents | Cross-border payments (MT and ISO 20022 MX) |
| **Zelle** | Early Warning Services | Near real-time for consumers | Person-to-person payments |

## How an instant payment flows (RTP example)

1. **Initiation**: a customer or business starts a payment in a bank channel.
2. **Validation and authorization**: the sending bank checks identity, KYC/AML, limits and balance.
3. **Message creation**: the bank builds an ISO 20022 `pacs.008` credit transfer.
4. **Clearing**: the network validates and routes it to the receiving bank.
5. **Settlement**: funds settle immediately against pre-funded positions.
6. **Confirmation**: the receiving bank responds with `pacs.002`, and both sides are notified.

### Common ISO 20022 messages

| Message | Name | Purpose |
|---------|------|---------|
| `pain.001` | Customer Credit Transfer Initiation | Customer instructs its bank to pay |
| `pacs.008` | FI to FI Customer Credit Transfer | The interbank payment itself |
| `pacs.002` | Payment Status Report | Accept or reject |
| `camt.056` | FI to FI Payment Cancellation Request | Ask to recall a payment |
| `camt.052` | Bank to Customer Account Report | Intraday account reporting |

## Sample code

`src/` has one package per rail: `ach`, `fed`, `fednow`, `rtp`, `swift` and `zelle`. Each one models the components a bank runs on that rail, such as message parsers and builders, duplicate checks, limit and liquidity checks, sanctions and fraud screening, routing, posting, returns and recalls, and regulatory reporting.

Within a rail, the classes share a common flow template so they can be compared side by side:

- Validate and route the payment
- Enrich and normalize the instruction
- Run risk and compliance checks
- Post downstream to the ledger
- Send asynchronous notifications
- Simulate exception scenarios
- Collect operational metrics

Rail-specific examples include the NACHA record formatter and parser, same-day ACH eligibility, prenotes and micro-deposits for ACH; Fedline connectivity and wire type resolution for Fedwire; MT103 and MT202 formatters, BIC validation and correspondent selection for SWIFT; and alias, token and device checks for Zelle.

The code uses only the Java standard library. To compile everything:

```bash
git clone https://github.com/RahulAutade2288/digital-payments-system-blueprint.git
cd digital-payments-system-blueprint
find src -name "*.java" > sources.txt
javac -d out @sources.txt
```

## Risk and compliance controls

- Real-time fraud screening, with velocity and amount-based rules
- OFAC sanctions screening
- Customer authentication and tokenization
- Audit trails and end-to-end message traceability

## Repository layout

```text
digital-payments-system-blueprint/
├── src/             Java sample code: ach, fed, fednow, rtp, swift, zelle
├── documentation/   Rail overviews, RTP technical overview, references
└── diagrams/        Diagram notes
```

## Standards and governance

The TCH RTP Operating Rules, Nacha Operating Rules, Federal Reserve operating circulars, ISO 20022 and FFIEC guidance all apply. Links to the official sources are in [documentation/References.md](documentation/References.md).

## Disclaimer

This is an educational blueprint, not production payment software, and it is not affiliated with any payment network.

## Author

**Rahul Autade**, Payments Modernization & Implementation Leader
[rahulautade2288.github.io](https://rahulautade2288.github.io/) · [LinkedIn](https://www.linkedin.com/in/rahul-autade/)
