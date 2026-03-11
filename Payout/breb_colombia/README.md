# 📄 Payload for `payout-invoice` (BRE-B – Colombia – COP)

This document outlines the structure and required fields for the `payout-invoice` payload using the `breb_cop` service, which supports **BRE-B transfers in Colombia (COP)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing or invalid, the request will be rejected.

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking and idempotency). |
| `service`      | Must be `"breb_cop"` for BRE-B payouts in Colombia.                           |
| `currency`     | Must be `"COP"` (Colombian Peso).                                             |
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

### 📱 BRE-B Fields (nested under `fields`)

| JSON Key          | Description                                                       |
| ----------------- | ----------------------------------------------------------------- |
| `document_type`   | Type of beneficiary document. Accepted value: `CC`.               |
| `document_id`     | Beneficiary document number (CC).                                 |
| `phone_number`    | Beneficiary phone number associated with the destination account. |
| `destination_key` | Destination BRE-B key associated with the beneficiary account.    |

📝 **Important:**  
All keys listed above must be **nested under `fields`**.

---

## 🔍 Notes

- All amounts must be provided in **Colombian Pesos (COP)**.
- `reference_id` must be unique per payout request.
- The `destination_key` must be a valid BRE-B identifier associated with the beneficiary.
- Invalid document information or destination keys will cause the request to fail.
