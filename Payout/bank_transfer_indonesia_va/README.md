# 📄 Payload for `payout-invoice` (Indonesia - ID)

This document describes the structure and required fields for creating **payout invoices** via bank transfer in Indonesia (`ID`). The format of the payload depends on the recipient's bank.

---

## 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                    |
| -------------- | -------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).  |
| `service`      | Bank service identifier.                                       |
| `currency`     | Must be `"IDR"` for Indonesian Rupiah.                         |
| `amount`       | Amount to be paid out (integer, no decimal places).            |
| `test_mode`    | Set to `true` for sandbox mode, `false` for live transactions. |

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

| JSON Key              | Description                             |
| --------------------- | --------------------------------------- |
| `bank_account_name`   | Name of the bank account holder.        |
| `bank_account_number` | Bank account number of the beneficiary. |

---

### 🔸 **Payload 2**

**Used for the following banks**:

- OCBC Bank Indonesia (`ocbc_bank_indonesia_idr`)
- Panin Bank (`panin_bank_idr`)
- CIMB Niaga (`cimb_niaga_idr`)

#### Fields under `fields`:

| JSON Key                 | Description                             |
| ------------------------ | --------------------------------------- |
| `beneficiary_first_name` | First name of the beneficiary.          |
| `beneficiary_last_name`  | Last name of the beneficiary.           |
| `account_number`         | Bank account number of the beneficiary. |

---

## 👤 Customer (nested under `customer`)

| JSON Key       | Description                 |
| -------------- | --------------------------- |
| `reference_id` | Unique customer identifier. |
| `name`         | Full name of the customer.  |
| `email`        | Customer’s email address.   |
| `phone`        | Customer’s phone number.    |

---

## 🧩 Metadata

| JSON Path      | Description                          |
| -------------- | ------------------------------------ |
| `metadata.url` | URL of the company or merchant site. |

---

## ⚙️ Options (nested under `options`)

| JSON Key       | Description                                                                                           |
| -------------- | ----------------------------------------------------------------------------------------------------- |
| `auto_process` | Set to `true` to automatically process the payout, or `false` for manual approval from the dashboard. |

---

## 🏦 Supported Banks and Their `service` Names

| Bank Name           | `service` Name            | Payload Type |
| ------------------- | ------------------------- | ------------ |
| BCA Bank            | `bca_bank_idr`            | Payload 1    |
| BNI Bank            | `bni_bank_idr`            | Payload 1    |
| BRI Bank            | `bri_bank_idr`            | Payload 1    |
| Danamon Bank        | `danamon_bank_idr`        | Payload 1    |
| Mandiri Bank        | `mandiri_bank_idr`        | Payload 1    |
| Permata Bank        | `permata_bank_idr`        | Payload 1    |
| OCBC Bank Indonesia | `ocbc_bank_indonesia_idr` | Payload 2    |
| Panin Bank          | `panin_bank_idr`          | Payload 2    |
| CIMB Niaga          | `cimb_niaga_idr`          | Payload 2    |

---

## 🔍 Notes

- Amounts must be in **Indonesian Rupiah (IDR)** as integers.
- The `reference_id` must be unique per transaction.
- `test_mode: true` indicates the payout will be processed in sandbox mode.
- Customer details are required for both formats.
- Additional metadata must be included inside the `metadata` object.
- The correct `service` name must be selected according to the beneficiary's bank.

---
