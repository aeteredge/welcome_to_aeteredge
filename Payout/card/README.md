# 📄 Payload for `payout-invoice` (CARD)

This document outlines the structure and required fields for the `payout-invoice` payload using the `payment_card_usd` service, which supports **payouts to payment cards in USD**.

---

## ✅ Required Fields

All the following fields are mandatory and must be nested correctly inside their respective parent objects.  
If any of them is missing or misplaced, the request will be rejected.

### 🔐 Fields (nested under `fields`)

| JSON Key       | Description                            |
|----------------|----------------------------------------|
| `card_number`  | The recipient's payment card number.   |

### 💳 Context (nested under `context.card`)

| JSON Key       | Description                            |
|----------------|----------------------------------------|
| `exp_month`    | Card's expiration month (e.g., `"09"`).|
| `exp_year`     | Card's expiration year (e.g., `"2030"`).|

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                            |
|----------------|----------------------------------------|
| `reference_id` | Unique customer identifier.            |
| `name`         | Full name of the recipient.            |

### 🏠 Address (nested under `customer.address`)

| JSON Key       | Description                            |
|----------------|----------------------------------------|
| `country`      | Country code (e.g., `US`, `ES`).       |
| `city`         | City name.                             |
| `region`       | Region, province, or state.            |
| `post_code`    | Postal or ZIP code.                    |
| `full_address` | Complete address string.               |

📝 **Important:** Fields must be nested properly under their respective parent keys (`fields`, `context`, `customer`, `customer.address`).

---

## 🔍 Notes

- `amount` must be provided in **US Dollars (USD)** as an integer (no decimal places).
- `reference_id` is a unique identifier for the transaction (used for tracking).
- `description` is optional and provides context or labeling for the payout.
- `test_mode: true` indicates this is a simulated transaction.
- Set `auto_process` to `true` or `false` to control whether the transaction is processed automatically.
- Additional metadata (e.g., `url`) must be included inside the `customer.metadata` object.

---
