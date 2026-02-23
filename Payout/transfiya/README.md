# 📄 Payload for `payout-invoice` (Transfiya – Colombia – COP)

This document outlines the structure and required fields for the `payout-invoice` payload using the `transfiya_cop` service, which supports **Transfiya payouts in Colombia (COP)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing or invalid, the request will be rejected.

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking and idempotency). |
| `service`      | Must be `"transfiya_cop"` for Transfiya payouts in Colombia.                  |
| `currency`     | Must be `"COP"` (Colombian Peso).                                             |
| `amount`       | Amount to be paid out.                                                        |
| `test_mode`    | Set to `true` for sandbox mode or `false` for live transactions.              |

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                               |
| -------------- | ----------------------------------------- |
| `reference_id` | Unique identifier of the customer.        |
| `name`         | Full name of the customer or beneficiary. |

---

### 📱 Transfiya Fields (nested under `fields`)

| JSON Key        | Description                                         |
| --------------- | --------------------------------------------------- |
| `document_type` | Type of beneficiary document. Accepted value: `CC`. |
| `document_id`   | Beneficiary document number (Cédula de Ciudadanía). |
| `phone_number`  | Mobile phone number linked to Transfiya .           |

📝 **Important:**  
All keys listed above must be **nested under `fields`**.

---

## 🔍 Notes

- All amounts must be provided in **Colombian Pesos (COP)**.
- `reference_id` must be unique per payout request.
- The `phone_number` must be registered with **Transfiya** and belong to the beneficiary.
- Only **CC** is supported as `document_type` for Transfiya payouts.
- Invalid document data or phone numbers will cause the request to fail.

---
