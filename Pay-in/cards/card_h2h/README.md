# 📄 Payload for `payment-invoices` (Card Payment)

This document outlines the structure and required fields for the `payment-invoices` payload using the `payment_card_eur_hpp` service, which supports **hosted pay-ins via payment cards**.

---

## ✅ Required Fields – Payment Invoice (HPP)

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key              | Description                                                                              |
| --------------------- | ---------------------------------------------------------------------------------------- |
| `reference_id`        | Unique identifier for the payment request.                                               |
| `service`             | The service identifier, for example `"payment_card_eur_hpp"` or `"payment_card_usd_hpp"` |
| `currency`            | Must be `"EUR"` for Euro and `"USD"` for US Dollar.                                      |
| `amount`              | Amount to be paid.                                                                       |
| `description`         | Description of the payment purpose.                                                      |
| `test_mode`           | Set to `true` for test/sandbox transactions.                                             |
| `flow`                | Payment flow. Use `"charge"` for hosted page flow.                                       |
| `return_urls.success` | Redirect URL after a successful payment.                                                 |
| `return_urls.pending` | Redirect URL while payment is pending.                                                   |
| `return_urls.fail`    | Redirect URL after a failed payment.                                                     |
| `callback_url`        | URL to receive asynchronous status updates.                                              |

---

### 👤 Customer (nested under `customer`)

| JSON Key        | Description                               |
| --------------- | ----------------------------------------- |
| `reference_id`  | Unique identifier of the customer.        |
| `name`          | Full name of the customer.                |
| `email`         | Email address of the customer.            |
| `phone`         | Phone number of the customer.             |
| `date_of_birth` | Date of birth in the format `YYYY-MM-DD`. |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key       | Description                            |
| -------------- | -------------------------------------- |
| `full_address` | Full formatted address string.         |
| `country`      | Country code (e.g., `"ES"` for Spain). |
| `region`       | Province or region.                    |
| `city`         | City name.                             |
| `street`       | Street name and number.                |
| `post_code`    | Postal code.                           |

---

### 🧩 Metadata

| JSON Path              | Description                 |
| ---------------------- | --------------------------- |
| `customer.metadata.ip` | IP address of the customer. |
| `metadata.url`         | URL of the company.         |

---

## ✅ Required Fields – Sale Operation (Card Details)

This is the payload sent after the user submits their card details on the hosted payment page.

⚠️ **All fields listed below are mandatory**. Omission of any of them will result in a failed or rejected transaction.

### 🔐 Card Details (nested under `attributes`) - **Mandatory**

| JSON Key      | Description                              |
| ------------- | ---------------------------------------- |
| `card_number` | The customer's card number.              |
| `card_holder` | Name on the card.                        |
| `cvv`         | Card Verification Value (CVV/CVC).       |
| `exp_month`   | Expiration month (e.g., `"10"`).         |
| `exp_year`    | Expiration year (e.g., `"30"` for 2030). |

### 🌐 Browser Info (nested under `browser_info`) - **Mandatory**

| JSON Key                | Description                                  |
| ----------------------- | -------------------------------------------- |
| `browser_accept_header` | Accept header sent by browser.               |
| `browser_java_enabled`  | Whether Java is enabled.                     |
| `browser_language`      | Browser language (e.g., `"en-US"`).          |
| `browser_user_agent`    | Full browser user-agent string.              |
| `browser_color_depth`   | Color depth of the browser window.           |
| `browser_ip`            | IP address of the customer device.           |
| `browser_screen_height` | Screen height in pixels.                     |
| `browser_screen_width`  | Screen width in pixels.                      |
| `browser_tz`            | Timezone offset (e.g., `"-570"`).            |
| `device_channel`        | Indicates channel: `"02"` for browser-based. |
| `window_height`         | Window height in pixels.                     |
| `window_width`          | Window width in pixels.                      |

---

## 🔍 Notes

- All amounts must be provided in **Euros (EUR) or US Dollar(USD)** as whole numbers (integer).
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- Callback and redirect URLs must be HTTPS for secure communications.
- This integration supports HPP (hosted payment page) for card transactions.

---
