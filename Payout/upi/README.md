# 📄 Payload for `payout-invoice` (India - IN)

This document outlines the structure and required fields for the `payout-invoice` payload using the `upi_inr` service, which supports **UPI bank transfers in India (IN)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                    |
| -------------- | -------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).  |
| `service`      | Must be `"upi_inr"` for UPI payouts in India.                  |
| `currency`     | Must be `"INR"` for Indian Rupees.                             |
| `amount`       | Amount to be paid out (integer, no decimal places).            |
| `test_mode`    | Set to `true` for sandbox mode, `false` for live transactions. |

---

### 🏦 Fields (nested under `fields`)

| JSON Key                | Description                                                             |
| ----------------------- | ----------------------------------------------------------------------- |
| `vpa`                   | Virtual Payment Address (e.g., `example@upi`).                          |
| `account_number`        | Beneficiary's bank account number.                                      |
| `beneficiary_full_name` | Full name of the beneficiary.                                           |
| `beneficiary_address`   | Full address of the beneficiary.                                        |
| `ifsc_bank_code`        | IFSC code of the beneficiary's bank (e.g., `SBIN0001111`).              |
| `pan_number`            | PAN (Permanent Account Number) of the beneficiary (e.g., `ABCDE1234F`). |

📝 **Important:** These keys must be **nested under `fields`**

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                 |
| -------------- | --------------------------- |
| `reference_id` | Unique customer identifier. |
| `email`        | Customer’s email address.   |
| `phone`        | Customer’s phone number.    |

---

### 🧩 Metadata

| JSON Path      | Description                          |
| -------------- | ------------------------------------ |
| `metadata.url` | URL of the company or merchant site. |

---

### ⚙️ Options (nested under `options`)

| JSON Key       | Description                                                                                           |
| -------------- | ----------------------------------------------------------------------------------------------------- |
| `auto_process` | Set to `true` to automatically process the payout, or `false` for manual approval from the dashboard. |

---

## 🔍 Notes

- All amounts must be provided in **Indian Rupees (INR)** as integers.
- `reference_id` must be unique for each payout.
- `test_mode: true` indicates the payout will be processed in sandbox mode.
- Customer details and metadata must be provided exactly as described above.

---
