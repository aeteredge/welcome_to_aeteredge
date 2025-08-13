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

## 💱 Supported Services

Below are the supported crypto payment HPP services by currency:

### **AUD**

- `applepay_crypto_aud_hpp`
- `googlepay_crypto_aud_hpp`
- `pay_id_crypto_aud_hpp`
- `payment_card_crypto_aud_hpp`

### **CAD**

- `applepay_crypto_cad_hpp`
- `googlepay_crypto_cad_hpp`
- `interac_crypto_cad_hpp`
- `payment_card_crypto_cad_hpp`

### **EUR**

- `payment_card_crypto_eur_hpp`
- `applepay_crypto_eur_hpp`
- `googlepay_crypto_eur_hpp`
- `sepa_transfer_crypto_eur_hpp`

### **USD**

- `applepay_crypto_usd_hpp`
- `googlepay_crypto_usd_hpp`
- `payment_card_crypto_usd_hpp`

### **Other Currencies**

- `payment_card_crypto_brl_hpp` — **BRL**
- `payment_card_crypto_dkk_hpp` — **DKK**
- `payment_card_crypto_jpy_hpp` — **JPY**
- `payment_card_crypto_mxn_hpp` — **MXN**
- `payment_card_crypto_nok_hpp` — **NOK**
- `payment_card_crypto_pln_hpp` — **PLN**
- `payment_card_crypto_sek_hpp` — **SEK**
- `payment_card_crypto_try_hpp` — **TRY**

---

## 🔍 Notes

- `currency` must match the `service` selected.
- The `blockchain_address` in `service_fields` is mandatory for crypto payouts.
- `flow` must be set to `"charge"` for payments.
- Amount precision depends on the currency; typically whole units for fiat and decimals for crypto conversions.

---
