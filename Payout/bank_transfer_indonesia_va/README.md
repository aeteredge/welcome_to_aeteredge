
# 📄 Payload for `payout-invoice` (Indonesia - ID)

This document describes the structure and required fields for creating **payout invoices** via bank transfer in Indonesia (`ID`). The format of the payload depends on the recipient's bank.

---

## ✅ Required Fields by Payload Type

There are **two supported payload formats** depending on the selected bank. Required fields must always be nested under the `fields` object.

### 🔹 **Payload 1**  
**Used for the following banks**:

- BCA Bank (`bca_bank_idr`)
- BNI Bank (`bni_bank_idr`)
- BRI Bank (`bri_bank_idr`)
- Danamon Bank (`danamon_bank_idr`)
- Mandiri Bank (`mandiri_bank_idr`)
- Permata Bank (`permata_bank_idr`)

#### Fields under `fields`:

| JSON Key              | Description                                      |
|-----------------------|--------------------------------------------------|
| `bank_account_name`   | Name of the bank account holder.                |
| `bank_account_number` | Bank account number of the beneficiary.         |

---

### 🔸 **Payload 2**  
**Used for the following banks**:

- OCBC Bank Indonesia (`ocbc_bank_indonesia_idr`)
- Panin Bank (`panin_bank_idr`)
- CIMB Niaga (`cimb_niaga_idr`)

#### Fields under `fields`:

| JSON Key                 | Description                                     |
|--------------------------|-------------------------------------------------|
| `beneficiary_first_name` | First name of the beneficiary.                  |
| `beneficiary_last_name`  | Last name of the beneficiary.                   |
| `account_number`         | Bank account number of the beneficiary.         |

---

## 🏦 Supported Banks and Their `service` Names

| Bank Name                        | `service` Name               | Payload Type      |
|----------------------------------|-------------------------------|------------------|
| BCA Bank                         | `bca_bank_idr`                | Payload 1        |
| BNI Bank                         | `bni_bank_idr`                | Payload 1        |
| BRI Bank                         | `bri_bank_idr`                | Payload 1        |
| Danamon Bank                     | `danamon_bank_idr`            | Payload 1        |
| Mandiri Bank                     | `mandiri_bank_idr`            | Payload 1        |
| Permata Bank                     | `permata_bank_idr`            | Payload 1        |
| OCBC Bank Indonesia              | `ocbc_bank_indonesia_idr`     | Payload 2        |
| Panin Bank                       | `panin_bank_idr`              | Payload 2        |
| CIMB Niaga                       | `cimb_niaga_idr`              | Payload 2        |

---

## 🔍 General Notes

- `amount` must be provided as an integer in **Indonesian Rupiah (IDR)** — **no decimal places**.
- `reference_id` is a unique identifier for the transaction.
- `test_mode: true` means this is a test (simulated) transaction.
- Set auto_process to true or false to control whether the transaction is processed automatically. If set to false, you will need to approve it manually from the dashboard.
- Additional metadata (e.g., `url`) must be included in the `metadata` object.
- Customer information (`reference_id`, `phone`, `email`, and `name`) must be included under the `customer` object.
