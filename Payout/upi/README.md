# 📄 Payload for `payout-invoice` (India - IN)

This document outlines the structure and required fields for the `payout-invoice` payload using the `upi_inr` service, which supports **UPI bank transfers in India (IN)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

| JSON Key                | Description                                                        |
|-------------------------|--------------------------------------------------------------------|
| `vpa`                   | Virtual Payment Address (e.g., `example@upi`).                     |
| `account_number`        | Beneficiary's bank account number.                                 |
| `beneficiary_full_name` | Full name of the beneficiary.                                      |
| `beneficiary_address`   | Full address of the beneficiary.                                   |
| `ifsc_bank_code`        | IFSC code of the beneficiary's bank (e.g., `SBIN0001111`).         |
| `pan_number`            | PAN (Permanent Account Number) of the beneficiary (e.g., `ABCDE1234F`). |

📝 **Important:** These keys must be **nested under `fields`**

---

## 🔍 Notes

- `amount` must be provided in **Indian Rupees (INR)** as an integer (no decimal places).
- `reference_id` is a unique identifier for the transaction (used for tracking).
- `test_mode: true` indicates this is a simulated transaction.
- Set `auto_process` to `true` or `false` to control whether the transaction is processed automatically. If set to `false`, you will need to approve it manually from the dashboard.
- Additional metadata (e.g., `url`) must be included in the `metadata` object.
- Customer details (`reference_id`, `phone`, and `email`) must be provided inside the `customer` object.

---
