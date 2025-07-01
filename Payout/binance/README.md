# 📄 Payload for `payout-invoice` (BinancePay - USD)

This document outlines the structure and required fields for the `payout-invoices` payload using the `binancepay_usd` service, which supports **USD payouts using BinancePay**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested within their respective objects.
If any are missing or misplaced, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                      |
| -------------- | ---------------------------------------------------------------- |
| `service`      | Must be `"binancepay_usd"` to indicate BinancePay payout in USD. |
| `currency`     | Must be `"USD"` for United States Dollar.                        |
| `amount`       | Amount to be paid, as an integer (no decimal places).            |
| `reference_id` | Unique identifier for the payout request.                        |
| `fields`       | Object containing recipient details (see below).                 |

---

### 👤 Recipient Fields (nested under `fields`)

| JSON Key         | Description                                                                      |
| ---------------- | -------------------------------------------------------------------------------- |
| `recipient_type` | Type of recipient identifier: `"EMAIL"` or `"BINANCE_ID"`.                       |
| `recipient_id`   | Email address or Binance ID of the recipient, depending on the `recipient_type`. |

📌 Valid examples:


```json
"fields": {
  "recipient_type": "BINANCE_ID",
  "recipient_id": "12345678"
}
```

```json
"fields": {
  "recipient_type": "EMAIL",
  "recipient_id": "test@mail.com"
}
```

---

## 🔍 Notes

* All amounts must be provided in **USD** as whole numbers (integers).
* The `recipient_type` determines how `recipient_id` should be interpreted.
* `reference_id` must be globally unique to identify each payout.

---
