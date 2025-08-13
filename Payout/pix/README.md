# 📄 Payload for `payout-invoice` (Brazil - BR)

This document outlines the structure and required fields for the `payout-invoice` payload using the `pix_brl` service, which supports **PIX transfers in Brazil (BR)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                    |
| -------------- | -------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).  |
| `service`      | Must be `"pix_brl"` for PIX payouts in Brazil.                 |
| `currency`     | Must be `"BRL"` for Brazilian Real.                            |
| `amount`       | Amount to be paid out (**integer**, no decimal places).        |
| `test_mode`    | Set to `true` for sandbox mode, `false` for live transactions. |

---

### 📂 Fields (nested under `fields`)

| JSON Key      | Description                                |
| ------------- | ------------------------------------------ |
| `cpf_number`  | CPF number of the beneficiary.             |
| `document_id` | Internal or government-issued document ID. |

📝 **Important:** These keys must be **nested under `fields`**

---

### ⚙️ Options (nested under `options`)

| JSON Key          | Description                                                                        |
| ----------------- | ---------------------------------------------------------------------------------- |
| `auto_process`    | Set to `true` to automatically process the payout, or `false` for manual approval. |

---

## 🔍 Notes

- All amounts must be provided in **Brazilian Reais (BRL)** as integers.
- `reference_id` must be unique for each payout request.
- `test_mode: true` will simulate the transaction in sandbox mode.
- Use the `options` object to fine-tune processing rules and retry behavior.

---

## 🎯 Approving Transactions in Sandbox

When using `test_mode: true`, you can simulate different payout outcomes by setting specific values in the `amount` field:

| Test Amount | Behavior                                   |
| ----------- | ------------------------------------------ |
| `99997`     | Triggers a **successful** payout callback. |
| `99999`     | Triggers a **declined** payout callback.   |

---
