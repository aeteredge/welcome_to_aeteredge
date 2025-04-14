# 📄 Payload for `payout-invoice` (Indonesia - ID)

This document outlines the structure and required fields for the `payout-invoice` payload using the `dana_idr` service, which supports **DANA wallet transfers in Indonesia (ID)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

| JSON Key                | Description                                                        |
|-------------------------|--------------------------------------------------------------------|
| `bank_account_name`     | Name of the DANA account holder.                                   |
| `bank_account_number`   | DANA account number or identifier.                                 |

📝 **Important:** These keys must be **nested under `fields`**

---

## 🔍 Notes

- `amount` must be provided in **Indonesian Rupiah (IDR)** as an integer (no decimal places).
- `reference_id` is a unique identifier for the transaction (used for tracking).
- `test_mode: true` indicates this is a simulated transaction.
- Set `auto_process` to `true` or `false` to control whether the transaction is processed automatically. If set to `false`, you will need to approve it manually from the dashboard.
- Additional metadata (e.g., `url`) must be included in the `metadata` object.
- Customer details (`reference_id`, `phone`, `email`, and `name`) must be provided inside the `customer` object.

---
