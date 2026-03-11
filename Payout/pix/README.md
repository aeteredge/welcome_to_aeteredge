# 📄 Payload for `payout-invoice` (PIX – Brazil – BRL)

This document outlines the structure and required fields for the `payout-invoice` payload using the `pix_brl` service, which supports **PIX payouts in Brazil (BRL)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing or invalid, the request will be rejected.

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking and idempotency). |
| `service`      | Must be `"pix_brl"` for PIX payouts in Brazil.                                |
| `currency`     | Must be `"BRL"` (Brazilian Real).                                             |
| `amount`       | Amount to be paid out.                                                        |
| `test_mode`    | Set to `true` for sandbox mode or `false` for live transactions.              |

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                               |
| -------------- | ----------------------------------------- |
| `reference_id` | Unique identifier of the customer.        |
| `name`         | Full name of the customer or beneficiary. |
| `email`        | Email address of the customer.            |

---

### ⚡ PIX Fields (nested under `fields`)

| JSON Key        | Description                                                                 |
| --------------- | --------------------------------------------------------------------------- |
| `pix_key`       | PIX key of the beneficiary (CPF, CNPJ, email, phone number, or random key). |
| `document_type` | Type of beneficiary document. Accepted value: `CPF`.                        |
| `document_id`   | Beneficiary document number (CPF, numbers only).                            |

📝 **Important:**  
All keys listed above must be **nested under `fields`**.

---

## 🔍 Notes

- All amounts must be provided in **Brazilian Reais (BRL)**.
- `reference_id` must be unique per payout request.
- The `pix_key` must be valid and registered in the Brazilian PIX system.
- Only **CPF** is supported as `document_type` for PIX payouts.
- Invalid PIX keys or document data will cause the request to fail.

---
