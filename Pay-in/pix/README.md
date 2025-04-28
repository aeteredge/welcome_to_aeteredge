# 📄 Payload for `payment-invoices` (PIX - Brazil - BRL)

This document outlines the structure and required fields for the `payment-invoices` payload using the `pix_brl_invoice` service, which supports **pay-ins via PIX in Brazilian Reais (BRL)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing, the request will be rejected.

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key             | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| `reference_id`       | Unique identifier for the payment request.                                  |
| `description`        | Description of the payment purpose.                                         |
| `currency`           | Must be `"BRL"` for Brazilian Real.                                         |
| `amount`             | Amount to be paid.                                                          |
| `service`            | Must be `"pix_brl_invoice"` for PIX pay-ins.                                |
| `return_url`         | Legacy return URL for redirect after payment.                               |
| `callback_url`       | URL to receive asynchronous status updates.                                 |
| `return_urls.success`| Redirect URL after a successful payment.                                    |
| `return_urls.fail`   | Redirect URL after a failed payment.                                        |
| `return_urls.pending`| Redirect URL while payment is pending.                                      |
| `test_mode`          | Set to `true` for test/sandbox transactions.                                |

---

### 🔐 Service Fields (nested under `service_fields`)

| JSON Key      | Description                             |
|---------------|-----------------------------------------|
| `cpf_number`  | CPF number of the payer (Brazilian ID). |

---

### 👤 Customer (nested under `customer`)

| JSON Key             | Description                                                             |
|----------------------|-------------------------------------------------------------------------|
| `reference_id`       | Unique identifier of the customer.                                      |
| `individual_tax_id`  | The customer's tax identification number (CPF).                         |
| `name`               | Full name of the customer.                                              |
| `email`              | Email address of the customer.                                          |
| `phone`              | Phone number of the customer.                                           |
| `date_of_birth`      | Date of birth in the format `YYYY-MM-DD`.                               |

---

### 🏠 Address (nested under `customer.address`)

| JSON Key         | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| `country`        | Country code (must be `"BR"` for Brazil).                                   |
| `post_code`      | Postal code.                                                                |
| `region`         | Province or region.                                                         |
| `city`           | City name.                                                                  |
| `street`         | Street name and number.                                                     |
| `full_address`   | Full formatted address string.                                              |

---

### 🧩 Metadata

| JSON Path                     | Description                                                   |
|-------------------------------|---------------------------------------------------------------|
| `metadata.url`                | URL of the company.                                           |
| `customer.metadata.ip`        | IP address of the customer.                                   |

---

## 🔍 Notes

- All amounts must be provided in **Brazilian Reais (BRL)** as whole numbers (integer).
- CPF is mandatory and must be included in `service_fields`.
- Use `test_mode: true` to simulate transactions in a sandbox environment.
- Callback and redirect URLs must be HTTPS for secure communications.

---
