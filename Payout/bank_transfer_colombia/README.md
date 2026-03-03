# 📄 Payload for `payout-invoice` (Bank Transfer – Colombia – COP)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_cop` service, which supports **bank transfers in Colombia (COP)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing or invalid, the request will be rejected.

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking and idempotency). |
| `service`      | Must be `"bank_transfer_cop"` for COP bank transfer payouts.                  |
| `currency`     | Must be `"COP"` (Colombian Peso).                                             |
| `amount`       | Amount to be paid.                                                            |
| `test_mode`    | Set to `true` for sandbox mode or `false` for live transactions.              |

---

### 👤 Customer (nested under `customer`)

| JSON Key       | Description                               |
| -------------- | ----------------------------------------- |
| `reference_id` | Unique identifier of the customer.        |
| `name`         | Full name of the customer or beneficiary. |
| `email`        | Email address of the customer.            |
| `phone`        | Customer phone number in E.164 format.    |

---

### 🏦 Bank Fields (nested under `fields`)

| JSON Key                  | Description                                                       |
| ------------------------- | ----------------------------------------------------------------- |
| `bank_code`               | Bank identifier code. Must match one of the supported bank codes. |
| `account_number`          | Bank account number of the beneficiary.                           |
| `account_type`            | Type of bank account.                                             |
| `document_type`           | Type of beneficiary document. Accepted value: `CC`.               |
| `beneficiary_document_id` | Beneficiary document number (CC).                                 |

📝 **Important:**  
All keys listed above must be **nested under `fields`**.

---

## 🏦 Supported Bank Codes

The `bank_code` field must be sent as a **string** and must match one of the supported banks listed below.

| Code   | Technical Name                                     | Description                              |
| ------ | -------------------------------------------------- | ---------------------------------------- |
| 1001   | Banco_de_bogota                                    | Banco de Bogotá                          |
| 1002   | Banco_popular                                      | Banco Popular                            |
| 1006   | Itau                                               | Itaú                                     |
| 1007   | Bancolombia                                        | Bancolombia                              |
| 1009   | Citibank                                           | Citibank                                 |
| 1012   | Banco_gnb_sudameris                                | Banco GNB Sudameris                      |
| 1013   | Bbva_colombia                                      | BBVA Colombia                            |
| 1019   | Scotiabank_colpatria                               | Scotiabank Colpatria                     |
| 1023   | Banco_de_occidente                                 | Banco de Occidente                       |
| 1031   | Bancoldex                                          | Bancóldex                                |
| 1032   | Banco_caja_social_bcsc                             | Banco Caja Social (BCSC)                 |
| 1040   | Banco_agrario                                      | Banco Agrario                            |
| 1047   | Banco_mundo_mujer                                  | Banco Mundo Mujer                        |
| 1051   | Banco_davivienda                                   | Banco Davivienda                         |
| 1052   | Banco_av_villas                                    | Banco AV Villas                          |
| 1053   | Banco_w                                            | Banco W                                  |
| 1059   | Banco_de_las_microfinanzas_bancamia                | Banco de las Microfinanzas Bancamía      |
| 1060   | Banco_pichincha                                    | Banco Pichincha                          |
| 1061   | Bancoomeva                                         | Bancoomeva                               |
| 1062   | Banco_falabella                                    | Banco Falabella                          |
| 1063   | Banco_finandina                                    | Banco Finandina                          |
| 1065   | Banco_santander_de_negocios_colombia               | Banco Santander de Negocios              |
| 1066   | Banco_cooperativo_coopcentral                      | Banco Cooperativo Coopcentral            |
| 1067   | Mibanco                                            | Mibanco                                  |
| 1069   | Banco_serfinanza                                   | Banco Serfinanza                         |
| 1070   | Lulo_bank                                          | Lulo Bank                                |
| 1071   | Banco_jp_morgan_colombia                           | Banco JP Morgan Colombia                 |
| 1086   | Asopagos                                           | Asopagos                                 |
| 1097   | Dale                                               | Dale                                     |
| 1121   | Financiera_juriscoop_compaÑia_de_financiamiento    | Financiera Juriscoop                     |
| 1283   | Cooperativa_financiera_de_antioquia                | Cooperativa Financiera de Antioquia      |
| 1286   | Jfk_cooperativa_financiera                         | JFK Cooperativa Financiera               |
| 1289   | Cootrafa_cooperativa_financiera                    | Cootrafa Cooperativa Financiera          |
| 1291   | Coofinep_cooperativa_financiera                    | Coofinep Cooperativa Financiera          |
| 1292   | Confiar_cooperativa_financiera                     | Confiar Cooperativa Financiera           |
| 1303   | Banco_union                                        | Banco Unión                              |
| 1370   | Coltefinanciera                                    | Coltefinanciera                          |
| 1507   | Nequi                                              | Nequi                                    |
| 1551   | Daviplata                                          | Daviplata                                |
| 1558   | Ban100                                             | Ban100                                   |
| 1560   | Pibank                                             | PiBank                                   |
| 1637   | Iris                                               | Iris                                     |
| 1801   | Movii                                              | Movii                                    |
| 1802   | Ding_tecnipagos                                    | Ding Tecnipagos                          |
| 1803   | Powwi                                              | Powwi                                    |
| 1804   | Uala                                               | Ualá                                     |
| 1805   | Banco_btg_pactual                                  | Banco BTG Pactual                        |
| 1808   | Bold_cf                                            | Bold CF                                  |
| 1809   | Nu_colombia                                        | Nu Colombia                              |
| 1811   | Rappipay                                           | RappiPay                                 |
| 1812   | Coink                                              | Coink                                    |
| 1813   | Santander_consumer                                 | Santander Consumer                       |
| 1814   | Global66                                           | Global66                                 |
| 1815   | Alianza_fiduciaria                                 | Alianza Fiduciaria                       |
| 1816   | Crezcamos                                          | Crezcamos                                |
| 1081   | Banco_agrario_desarrollo                           | Banco Agrario de Desarrollo              |
| 1080   | Banco_agrario_qa_defectos                          | Banco Agrario QA Defectos                |
| 1005   | Banco_union_colombiano_fd2                         | Banco Unión Colombiano FD2               |
| 1077   | Banka                                              | Banka                                    |
| 1513   | Bbva_desarrollo                                    | BBVA Desarrollo                          |
| 121212 | Prueba_steve                                       | Prueba Steve                             |
| 001    | Short_code_banco_de_bogota                         | Banco de Bogotá (short code)             |
| 002    | Short_code_banco_popular                           | Banco Popular (short code)               |
| 006    | Short_code_itau_antes_corpbanca                    | Itaú (antes Corpbanca)                   |
| 007    | Short_code_bancolombia                             | Bancolombia (short code)                 |
| 009    | Short_code_citibank                                | Citibank (short code)                    |
| 012    | Short_code_banco_gnb_sudameris                     | Banco GNB Sudameris (short code)         |
| 013    | Short_code_bbva_colombia                           | BBVA Colombia (short code)               |
| 014    | Short_code_itau                                    | Itaú (short code)                        |
| 019    | Short_code_scotiabank_colpatria_sa                 | Scotiabank Colpatria (short code)        |
| 023    | Short_code_banco_de_occidente                      | Banco de Occidente (short code)          |
| 031    | Short_code_bancoldex_sa                            | Bancóldex (short code)                   |
| 032    | Short_code_banco_caja_social_bcsc_sa               | Banco Caja Social (short code)           |
| 040    | Short_code_banco_agrario                           | Banco Agrario (short code)               |
| 047    | Short_code_banco_mundo_mujer                       | Banco Mundo Mujer (short code)           |
| 051    | Short_code_banco_davivienda_sa                     | Banco Davivienda (short code)            |
| 052    | Short_code_banco_av_villas                         | Banco AV Villas (short code)             |
| 053    | Short_code_banco_w                                 | Banco W (short code)                     |
| 059    | Short_code_banco_de_las_microfinanzas_bancamia_sa  | Banco Bancamía (short code)              |
| 060    | Short_code_banco_pichincha                         | Banco Pichincha (short code)             |
| 061    | Short_code_bancoomeva                              | Bancoomeva (short code)                  |
| 062    | Short_code_banco_falabella_sa                      | Banco Falabella (short code)             |
| 063    | Short_code_banco_finandina_sa                      | Banco Finandina (short code)             |
| 065    | Short_code_banco_santander_de_negocios_colombia_sa | Banco Santander de Negocios (short code) |
| 066    | Short_code_banco_cooperativo_coopcentral           | Banco Coopcentral (short code)           |
| 067    | Short_code_mibanco_sa                              | Mibanco (short code)                     |
| 069    | Short_code_banco_serfinanza_sa                     | Banco Serfinanza (short code)            |
| 070    | Short_code_lulo_bank_sa                            | Lulo Bank (short code)                   |
| 071    | Short_code_banco_jp_morgan_colombia_sa             | Banco JP Morgan (short code)             |
| 086    | Short_code_asopagos_sas                            | Asopagos (short code)                    |
| 121    | Short_code_financiera_juriscoop_sa                 | Financiera Juriscoop (short code)        |
| 283    | Short_code_cooperativa_financiera_de_antioquia     | Cooperativa de Antioquia (short code)    |
| 286    | Short_code_jfk_cooperativa_financiera              | JFK Cooperativa (short code)             |
| 289    | Short_code_cootrafa_cooperativa_financiera         | Cootrafa (short code)                    |
| 291    | Short_code_coofinep_cooperativa_financiera         | Coofinep (short code)                    |
| 292    | Short_code_confiar_cooperativa_financiera          | Confiar (short code)                     |
| 303    | Short_code_banco_union_sa                          | Banco Unión (short code)                 |
| 370    | Short_code_coltefinanciera_sa                      | Coltefinanciera (short code)             |
| 507    | Short_code_nequi                                   | Nequi (short code)                       |
| 151    | Short_code_daviplata                               | Daviplata (short code)                   |
| 551    | Short_code_daviplata_alt                           | Daviplata (alt short code)               |
| 558    | Short_code_ban100_sa                               | Ban100 (short code)                      |
| 560    | Short_code_pibank                                  | PiBank (short code)                      |
| 637    | Short_code_iris                                    | Iris (short code)                        |
| 801    | Short_code_movii                                   | Movii (short code)                       |
| 802    | Short_code_ding_tecnipagos_sa                      | Ding Tecnipagos (short code)             |
| 803    | Short_code_powwi                                   | Powwi (short code)                       |
| 804    | Short_code_uala                                    | Ualá (short code)                        |
| 805    | Short_code_banco_btg_pactual                       | Banco BTG Pactual (short code)           |
| 811    | Short_code_rappipay                                | RappiPay (short code)                    |
| 888    | Banco_rojo                                         | Banco Rojo                               |
| 81     | Banca_de_inversion_bancolombia                     | Banca de Inversión Bancolombia           |
| 41     | Banco_agrario_de_colombia                          | Banco Agrario de Colombia                |
| 378    | Banco_comercial_av_villas                          | Banco Comercial AV Villas                |
| 44     | Banco_coomeva                                      | Banco Coomeva                            |
| 50     | Banco_credifinanciera                              | Banco Credifinanciera                    |
| 313    | Compania_financiamiento_tuya                       | Compañía de Financiamiento Tuya          |
| 65     | Corporacion_financiera_colombiana                  | Corporación Financiera Colombiana        |
| 323    | Credifamilia_compania_financiamiento               | Credifamilia                             |
| 328    | Crezcamos_compania_financiamiento                  | Crezcamos Compañía de Financiamiento     |
| 72     | Financiera_desarrollo_nacional                     | Financiera de Desarrollo Nacional        |
| 74     | Financiera_desarrollo_territorial_findeter         | Findeter                                 |
| 684    | Fogafin                                            | Fogafin                                  |
| 991    | Fondo_nacional_garantias                           | Fondo Nacional de Garantías              |
| 936    | Fondo_nacional_del_ahorro                          | Fondo Nacional del Ahorro                |
| 692    | Finagro                                            | Finagro                                  |
| 305    | Gm_financial_colombia                              | GM Financial Colombia                    |
| 884    | Instituto_credito_exterior                         | Instituto Crédito Exterior               |

---

## 🔍 Notes

- All amounts must be provided in **Colombian Pesos (COP)**.
- `reference_id` must be unique per payout request.
- The `bank_code` must be sent as a **string**, even when numeric.
- Some institutions may have both a **full code** (e.g., `1007`) and a **short code** (e.g., `007`). Use the one required by your integration.
- Only banks listed in this document are supported.
- Invalid or unsupported bank codes will cause the request to fail.
