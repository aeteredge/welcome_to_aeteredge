# 📄 Payload for `payout-invoice` (Brazil - BR)

This document outlines the structure and required fields for the `payout-invoice` payload using the `pix_brl` service, which supports **PIX transfers in Brazil (BR)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

| JSON Key       | Description                                     |
|----------------|-------------------------------------------------|
| `cpf_number`   | CPF number of the beneficiary.                  |
| `document_id`  | Internal or government-issued document ID.      |

📝 **Important:** These keys must be **nested under `fields`**

---

## 🔍 Notes

- `amount` must be provided in **Brazilian Reais (BRL)** as an integer (no decimal places).
- `reference_id` is a unique identifier for the transaction (used for tracking).
- `test_mode: true` indicates this is a simulated transaction.
- Set `auto_process` to `true` or `false` to control whether the transaction is processed automatically. If set to `false`, you will need to approve it manually from the dashboard.
- The `options` object supports advanced settings like `attempts_limit`, `split_mode`, and `allow_partially`.

## 🎯 Approving transactions in sandbox

When using `test_mode: true`, you can simulate different payment outcomes by setting specific values in the `amount` field:

| Test Amount    | Behavior                                    |
|----------------|---------------------------------------------|
| `99997`        | Triggers a **successful** payment callback. |
| `99999`        | Triggers a **declined** payment callback.   |

---
