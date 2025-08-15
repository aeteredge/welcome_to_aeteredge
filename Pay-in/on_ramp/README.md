# 📄 Payload for `payment-invoice` (Crypto HPP Payments)

This document outlines the structure and required fields for the `payment-invoice` payload when using **Hosted Payment Page (HPP)** services to pay with crypto.  
It applies to multiple currencies and service types as listed in the [Supported Services](#-supported-services) section.

---

## 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                               |
| -------------- | ------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payment request (used for tracking).            |
| `service`      | Crypto HPP service name (see [Supported Services](#-supported-services)). |
| `currency`     | Currency code (e.g., `"AUD"`, `"USD"`). Must match the selected service.  |
| `amount`       | Amount to be charged (integer or decimal depending on currency rules).    |
| `test_mode`    | Set to `false` for live/production transactions.                          |
| `flow`         | Payment flow. Use `"charge"` for hosted page flow.                        |

---

## 🔐 Service Fields (nested under `service_fields`)

| JSON Key             | Description                                                                              |
| -------------------- | ---------------------------------------------------------------------------------------- |
| `blockchain_address` | Blockchain address to receive the payment, contact support team for further information. |

---

## 💱 Supported Services (by Service Type)

Below is the list of supported crypto payment HPP services **organized by service type**.  
Each section shows the available currencies and their corresponding service IDs.

### **Apple Pay**

| Currency | Service ID                |
| -------- | ------------------------- |
| AUD      | `applepay_crypto_aud_hpp` |
| CAD      | `applepay_crypto_cad_hpp` |
| EUR      | `applepay_crypto_eur_hpp` |
| USD      | `applepay_crypto_usd_hpp` |

---

### **Google Pay**

| Currency | Service ID                 |
| -------- | -------------------------- |
| AUD      | `googlepay_crypto_aud_hpp` |
| CAD      | `googlepay_crypto_cad_hpp` |
| EUR      | `googlepay_crypto_eur_hpp` |
| USD      | `googlepay_crypto_usd_hpp` |

---

### **Pay ID**

| Currency | Service ID              |
| -------- | ----------------------- |
| AUD      | `pay_id_crypto_aud_hpp` |

---

### **Payment Card**

| Currency | Service ID                    |
| -------- | ----------------------------- |
| AUD      | `payment_card_crypto_aud_hpp` |
| CAD      | `payment_card_crypto_cad_hpp` |
| EUR      | `payment_card_crypto_eur_hpp` |
| USD      | `payment_card_crypto_usd_hpp` |
| BRL      | `payment_card_crypto_brl_hpp` |
| DKK      | `payment_card_crypto_dkk_hpp` |
| JPY      | `payment_card_crypto_jpy_hpp` |
| MXN      | `payment_card_crypto_mxn_hpp` |
| NOK      | `payment_card_crypto_nok_hpp` |
| PLN      | `payment_card_crypto_pln_hpp` |
| SEK      | `payment_card_crypto_sek_hpp` |
| TRY      | `payment_card_crypto_try_hpp` |

---

### **Interac**

| Currency | Service ID               |
| -------- | ------------------------ |
| CAD      | `interac_crypto_cad_hpp` |

---

### **Open Banking**

| Currency | Service ID                     |
| -------- | ------------------------------ |
| EUR      | `sepa_transfer_crypto_eur_hpp` |
| GBP      | `sepa_transfer_crypto_gbp_hpp` |

---

### **Pix**

| Currency | Service ID           |
| -------- | -------------------- |
| BRL      | `pix_crypto_brl_hpp` |

---

### **iDEAL**

| Currency | Service ID             |
| -------- | ---------------------- |
| EUR      | `ideal_crypto_eur_hpp` |

---

## 🔍 Notes

- `currency` must match the `service` selected.
- The `blockchain_address` in `service_fields` is mandatory for crypto payouts.
- `flow` must be set to `"charge"` for payments.
- Amount precision depends on the currency; typically whole units for fiat and decimals for crypto conversions.

---
