# 📄 Payload for `payout-invoice` (Indonesia - ID)

This document outlines the structure and required fields for the `payout-invoice` payload using the `namebank_bank_idr` service, which supports **Bank transfers in Indonesia (ID)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested inside the `fields` object of the payload.  
If any of them is missing or placed outside of `fields`, the request will be rejected.

| JSON Key                | Description                                                        |
|-------------------------|--------------------------------------------------------------------|
| `bank_account_name`     | Name of the bank account holder.                                   |
| `bank_account_number`   | Bank account number of the recipient.                              |

📝 **Important:** These keys must be **nested under `fields`**

---

## 🏦 Supported Banks and Their Corresponding Services

To use one of the supported banks, set the corresponding `service` value in the payload:

| Bank Name                         | Service Name                |
|-----------------------------------|-----------------------------|
| BCA Bank                          | `bca_bank_idr`              |
| BNI Bank                          | `bni_bank_idr`              |
| BRI Bank                          | `bri_bank_idr`              |
| Bank CIMB Niaga                   | `cimb_niaga_idr`            |
| Danamon Bank                      | `danamon_bank_idr`          |
| Mandiri Bank                      | `mandiri_bank_idr`          |
| OCBC (OCBC Bank Indonesia)        | `ocbc_bank_indonesia_idr`   |
| Panin Bank                        | `panin_bank_idr`            |
| Permata Bank                      | `permata_bank_idr`          |

Make sure the correct `service` is selected based on the beneficiary's bank.

---

## 🔍 Notes

- `amount` must be provided in **Indonesian Rupiah (IDR)** as an integer (no decimal places).
- `reference_id` is a unique identifier for the transaction (used for tracking).
- `test_mode: true` indicates this is a simulated transaction.
- Set `auto_process` to `true` or `false` to control whether the transaction is processed automatically. If set to `false`, you will need to approve it manually from the dashboard.
- Additional metadata (e.g., `url`) must be included in the `metadata` object.
- Customer details (`reference_id`, `phone`, `email`, and `name`) must be provided inside the `customer` object.

---


