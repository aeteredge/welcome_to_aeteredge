# 📄 Payload for `payout-invoice` (CARD)

This document outlines the structure and required fields for the `payout-invoice` payload when using card-based payout services. TIt applies to any supported card payout service regardless of currency.

## 💡 Example Services

This payload structure may be used with services like:

- `payment_card_usd`
- `payment_card_eur`  
  _(depending on the selected currency)_

---

## ✅ Required Fields

All the following fields are mandatory and must be nested correctly inside their respective parent objects.  
If any of them is missing or misplaced, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                      |
| -------------- | ---------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking).    |
| `service`      | The card payout service identifier (e.g., `"payment_card_usd"`). |
| `currency`     | Payout currency (e.g., `"USD"`, `"EUR"`).                        |
| `amount`       | Amount to be paid out (**integer**, no decimal places).          |
| `description`  | Optional text describing the payout purpose.                     |
| `test_mode`    | Set to `true` for sandbox mode, `false` for live transactions.   |

---

### 🔐 Fields (nested under `fields`)

| JSON Key      | Description                          |
| ------------- | ------------------------------------ |
| `card_number` | The recipient's payment card number. |

### 💳 Context (nested under `context.card`)

| JSON Key      | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| `card_holder` | Full name of the card owner, exactly as printed on the card. |
| `exp_month`   | Card's expiration month (e.g., `"09"`).                      |
| `exp_year`    | Card's expiration year (e.g., `"30"`).                       |

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                 |
| -------------- | --------------------------- |
| `reference_id` | Unique customer identifier. |
| `name`         | Full name of the recipient. |

### 🏠 Address (nested under `customer.address`)

| JSON Key       | Description                          |
| -------------- | ------------------------------------ |
| `full_address` | Full formatted address string.       |
| `country`      | Country code (e.g., `"US"`, `"ES"`). |
| `region`       | Province, state, or region.          |
| `city`         | City name.                           |
| `street`       | Street name and number.              |
| `post_code`    | Postal or ZIP code.                  |

📝 **Important:** Fields must be nested properly under their respective parent keys (`fields`, `context`, `customer`, `customer.address`).

---

### 🧩 Metadata

| JSON Path               | Description                          |
| ----------------------- | ------------------------------------ |
| `customer.metadata.url` | URL of the company or merchant site. |

---

### ⚙️ Options (nested under `options`)

| JSON Key       | Description                                                                        |
| -------------- | ---------------------------------------------------------------------------------- |
| `auto_process` | Set to `true` to automatically process the payout, or `false` for manual approval. |

---

## 🔍 Notes

- All amounts must be integers in the specified currency.
- The `card_number`, `exp_month`, and `exp_year` are mandatory for card payouts.
- `test_mode: true` simulates the transaction in a sandbox environment.
- Metadata should be placed under `customer.metadata`.
- Address details must be fully provided for compliance checks.

---
