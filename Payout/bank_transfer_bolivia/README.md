# 📄 Payload for `payout-invoice` (Bank Transfer – Bolivia – BOB)

This document outlines the structure and required fields for the `payout-invoice` payload using the `bank_transfer_bob` service, which supports **bank transfers in Bolivia (BOB)**.

---

## ✅ Required Fields

All the following fields are mandatory and must be correctly nested inside the respective objects of the payload.  
If any of them is missing or invalid, the request will be rejected.

---

### 🧾 Root Attributes (nested under `attributes`)

| JSON Key       | Description                                                                   |
| -------------- | ----------------------------------------------------------------------------- |
| `reference_id` | Unique identifier for the payout request (used for tracking and idempotency). |
| `service`      | Must be `"bank_transfer_bob"` for BOB bank transfer payouts.                  |
| `currency`     | Must be `"BOB"` (Boliviano).                                                  |
| `amount`       | Amount to be paid out.                                                        |
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

| JSON Key                    | Description                                                       |
| --------------------------- | ----------------------------------------------------------------- |
| `bank_code`                 | Bank identifier code. Must match one of the supported bank codes. |
| `bank_account`              | Bank account number of the beneficiary.                           |
| `account_type`              | Type of bank account.                                             |
| `beneficiary_document_type` | Type of beneficiary document. Accepted value: `CI`.               |
| `beneficiary_document_id`   | Beneficiary document number (CI).                                 |

📝 **Important:**  
All keys listed above must be **nested under `fields`**.

---

## 🏦 Supported Bank Codes

The `bank_code` field must be sent as a **string** and must match one of the supported banks listed below.

| Code  | Technical Name                                | Description                                                                     |
| ----- | --------------------------------------------- | ------------------------------------------------------------------------------- |
| 1     | Banco_bisa                                    | Banco BISA S.A.                                                                 |
| 2     | Banco_mercantil_santa_cruz                    | Banco Mercantil Santa Cruz S.A.                                                 |
| 3     | Banco_de_credito_bcp                          | Banco de Crédito de Bolivia S.A                                                 |
| 4     | Banco_nacional_de_bolivia_bnb                 | Banco Nacional de Bolivia S.A                                                   |
| 6     | Banco_economico                               | Banco Económico S.A                                                             |
| 7     | Banco_ganadero                                | Banco Ganadero S.A.                                                             |
| 8     | Banco_union                                   | Banco Unión S.A.                                                                |
| 9     | Banco_prodem                                  | Banco Prodem S.A.                                                               |
| 10    | Banco_fortaleza                               | Banco Fortaleza S.A                                                             |
| 11    | Banco_sol                                     | Banco Solidario S.A.                                                            |
| 12    | Banco_fie                                     | Banco para el Fomento a Iniciativas Económicas S.A.                             |
| 13    | Banco_de_la_nacion_argentina                  | Banco de la Nación Argentina S. A                                               |
| 14    | Banco_ecofuturo                               | Banco PYME Ecofuturo S.A                                                        |
| 15    | Cooperativa_la_merced_ltda                    | Cooperativa La Merced Ltda.                                                     |
| 16    | Cooperativa_san_martin_de_porres_ltda         | Cooperativa San Martin de Porres Ltda.                                          |
| 17    | Tigomoney                                     | TigoMoney                                                                       |
| 18    | Cooperativa_jesus_nazareno                    | Cooperativa de Ahorro y Crédito Abierta Jesús Nazareno Ltda                     |
| 19    | La_primera_efv_sa                             | La Primera EFV S.A.                                                             |
| 20    | Idepro_ifd                                    | Institución Financiera de Desarrollo IDEPRO                                     |
| 21    | Banco_central_de_bolivia                      | Banco Central de Bolivia                                                        |
| 22    | Banco_de_desarrollo_productivo                | Banco de Desarrollo Productivo S.A.M.                                           |
| 23    | Banco_pyme_de_la_comunidad                    | Banco PYME de la Comunidad S.A.                                                 |
| 24    | La_promotora_efv                              | La Promotora EFV                                                                |
| 25    | El_progreso_entidad_financiera_de_vivienda    | El Progreso Entidad Financiera de Vivienda                                      |
| 26    | El_progreso_efv                               | El Progreso EFV                                                                 |
| 27    | Fondeco_ifd                                   | Institución Financiera de Desarrollo FONDECO                                    |
| 28    | Impro_ifd                                     | Institución Financiera de Desarrollo IMPRO                                      |
| 29    | Sembrar_sartawi_ifd                           | Sembrar Sartawi IFD                                                             |
| 30    | Fundacion_pro_mujer_ifd                       | Fundacion Pro Mujer IFD                                                         |
| 31    | Cidre_ifd                                     | Institución Financiera de Desarrollo CIDRE                                      |
| 32    | Diaconia_ifd                                  | Institución Financiera de Desarrollo DIACONIA                                   |
| 33    | Cooperativa_catedral_potosi                   | Cooperativa Catedral Potosi                                                     |
| 34    | Cooperativa_la_sagrada_familia                | Cooperativa de Ahorro y Crédito Societaria La Sagrada Familia Ltda.             |
| 35    | Cooperativa_societaria_san_martin_de_potosi   | Cooperativa Societaria San Martin de Potosi                                     |
| 36    | Cooperativa_san_mateo                         | Cooperativa San Mateo                                                           |
| 37    | Cooperativa_san_joaquin                       | Cooperativa San Joaquin                                                         |
| 38    | Cooperativa_fatima                            | Cooperativa Fatima                                                              |
| 39    | Cooperativa_loyola                            | Cooperativa Loyola                                                              |
| 40    | Cooperativa_monsenor_felix_gainza             | Cooperativa Monseñor Felix Gainza                                               |
| 41    | Cooperativa_san_antonio                       | Cooperativa San Antonio                                                         |
| 42    | Cooperativa_catedral_de_tarija                | Cooperativa Catedral de Tarija                                                  |
| 43    | Cooperativa_de_ahorro_y_credito_abierta_san_p | Cooperativa de Ahorro y Crédito Abierta San P                                   |
| 44    | Cooperativa_comarapa                          | Cooperativa Comarapa                                                            |
| 45    | Cooperativa_de_ahorro_y_credito_asuncion      | Cooperativa de Ahorro y Crédito Asuncion                                        |
| 46    | Cooperativa_madre_y_maestra                   | Cooperativa Madre y Maestra                                                     |
| 47    | Cooperativa_el_chorolque                      | Cooperativa El Chorolque                                                        |
| 48    | Cooperativa_quillacollo                       | Cooperativa Quillacollo                                                         |
| 49    | Cooperativa_educadores_gran_chaco             | Cooperativa Educadores Gran Chaco                                               |
| 50    | Cooperativa_magisterio_rural_tarija           | Cooperativa Magisterio Rural Tarija                                             |
| 51    | Cooperativa_san_carlos_borromeo               | Cooperativa San Carlos Borromeo                                                 |
| 52    | Cooperativa_san_jose_de_bermejo               | Cooperativa San Jose de Bermejo                                                 |
| 53    | Cooperativa_magisterio_rural_de_chuquisaca    | Cooperativa de Ahorro y Crédito Societaria Magisterio Rural de Chuquisaca Ltda. |
| 54    | Cooperativa_san_jose_de_punata                | Cooperativa San Jose de Punata                                                  |
| 55    | Cooperativa_inca_huasi                        | Cooperativa Inca Huasi                                                          |
| 56    | Cooperativa_san_pedro                         | Cooperativa San Pedro                                                           |
| 57    | Cooperativa_pio_x                             | Cooperativa Pio X                                                               |
| 58    | Cooperativa_trinidad_cactri                   | Cooperativa Trinidad CACTRI                                                     |
| 59    | Cooperativa_cacef                             | Cooperativa CACEF                                                               |
| 84    | Mutual_la_primera                             | Mutual La Primera                                                               |
| 85    | Mutual_paititi                                | Mutual Paititi                                                                  |
| 86    | Mutual_pando                                  | Mutual Pando                                                                    |
| 87    | Mutual_la_plata                               | Mutual La Plata                                                                 |
| 88    | Mutual_potosi                                 | Mutual Potosi                                                                   |
| 89    | Entel_pago_movil                              | Entel Pago Movil                                                                |
| 90    | Edv_cuenta_liquidadora                        | EDV Cuenta Liquidadora                                                          |
| 91    | Accl                                          | ACCL                                                                            |
| 92    | Linkser                                       | LINKSER                                                                         |
| 93    | Edv_cuenta_de_liquidacion                     | EDV Cuenta de Liquidacion                                                       |
| 94    | Crecer_ifd                                    | Institución Financiera de Desarrollo CRECER                                     |
| 97    | Indefinido                                    | Indefinido                                                                      |
| 98    | Indeterminado                                 | Indeterminado                                                                   |
| 99    | Otros_bancos_del_exterior                     | Otros Bancos del Exterior                                                       |
| 100   | Billetera_yape                                | YAPE                                                                            |
| 101   | Coop_de_ahorro_y_credito_abierta_progreso_rl  | Coop. de Ahorro y Credito Abierta "Progreso" R.L.                               |
| 102   | Yolo_pago                                     | YOLO Pago                                                                       |
| 103   | Cooperativa_de_ahorro_y_credito_san_roque_rl  | Cooperativa de Ahorro y Credito San Roque R.L.                                  |
| 104   | Banco_do_brasil                               | Banco Do Brasil S.A.- Sucursal Bolivia                                          |
| 105   | Banco_fassil                                  | Banco Fassil S.A. (Em liquidação)                                               |
| 106   | Banco_pyme_los_andes_procredit                | Banco PYME Los Andes Procredit S.A                                              |
| 107   | Fubode_ifd                                    | Institución Financiera de Desarrollo FUBODE                                     |
| 108   | Argenper_bolivia                              | Empresa de Giro y Remesas de Dinero Argenper Bolivia S.R.L.                     |
| 109   | Caceres_ltda                                  | Empresa de Giro y Remesas de Dinero Caceres Ltda                                |
| 110   | Compania_interamericana_de_servicios          | Empresa de Giro y Remesas de Dinero Compañia Interamericana de Servicios S.R.L. |
| 111   | More_bolivia                                  | Empresa de Giros y Remesas de Dinero More Bolivia S.A                           |
| 112   | Euroenvios                                    | Empresa de Remesas y Giros EUROENVIOS S.R.L                                     |
| 113   | Almacenes_internacionales                     | Almacenes Internacionales S.A.                                                  |
| 114   | Warrant_mercantil_santa_cruz                  | Warrant Mercantil Santa Cruz S.A.                                               |
| 115   | Peru_services                                 | Perú Services S.R.L                                                             |
| 116   | Coop_2_de_junio_abasto                        | Cooperativa de Ahorro y Crédito Societaria 2 de Junio Abasto Ltda               |
| 117   | Coop_cooprole                                 | Cooperativa de Ahorro y Crédito Societaria Cooprole Ltda.                       |
| 118   | Coop_cristo_rey                               | Cooperativa de Ahorro y Crédito Societaria Cristo Rey Ltda.                     |
| 119   | Coop_el_buen_samaritano                       | Cooperativa de Ahorro y Crédito Societaria El Buen Samaritano Ltda.             |
| 120   | Coop_el_churqui                               | Cooperativa de Ahorro y Crédito Societaria El Churqui Ltda                      |
| 121   | Coop_empetrol                                 | Cooperativa de Ahorro y Crédito Societaria EMPETROL Ltda                        |
| 122   | Coop_gran_grigota                             | Cooperativa de Ahorro y Crédito Societaria Gran Grigotá Ltda.                   |
| 123   | Coop_nuestra_senora_de_los_remedios           | Cooperativa de Ahorro y Crédito Societaria Nuestra Señora de Los Remedios Ltda. |
| 124   | Coop_sacarosa                                 | Cooperativa de Ahorro y Crédito Societaria Sacarosa Ltda.                       |
| 125   | Coop_san_francisco_solano                     | Cooperativa de Ahorro y Crédito Societaria San Francisco Solano Ltda.           |
| 126   | Coop_san_pedro_de_aiquile                     | Cooperativa de Ahorro y Crédito Societaria San Pedro de Aiquile Ltda.           |
| 127   | Coop_sarco                                    | Cooperativa de Ahorro y Crédito Societaria Sarco Ltda                           |
| 128   | Coop_tukuypaj                                 | Cooperativa de Ahorro y Crédito Societaria Tukuypaj Ltda.                       |
| 129   | Coop_1_de_septiembre                          | Cooperativa de Ahorro y Crédito Societaria 1 de Septiembre Ltda.                |
| 130   | Coop_4_de_agosto                              | Cooperativa de Ahorro y Crédito Societaria 4 de Agosto Ltda.                    |
| 131   | Coop_alalay                                   | Cooperativa de Ahorro y Crédito Societaria Alalay Ltda.                         |
| 132   | Coop_andres_ibanez                            | Cooperativa de Ahorro y Crédito Societaria Andrés Ibáñez Ltda.                  |
| 133   | Coop_cantera                                  | Cooperativa de Ahorro y Crédito Societaria Cantera Ltda.                        |
| 134   | Coop_concordia                                | Cooperativa de Ahorro y Crédito Societaria Concordia Ltda                       |
| 135   | Coop_credicoop                                | Cooperativa de Ahorro y Crédito Societaria Credicoop Ltda                       |
| 136   | Coop_el_cristo                                | Cooperativa de Ahorro y Crédito Societaria El Cristo Ltda                       |
| 137   | Coop_hospicio                                 | Cooperativa de Ahorro y Crédito Societaria Hospicio Ltda.                       |
| 138   | Coop_ibercoop                                 | Cooperativa de Ahorro y Crédito Societaria Ibercoop Ltda                        |
| 139   | Coop_jerusalen                                | Cooperativa de Ahorro y Crédito Societaria Jerusalén Ltda.                      |
| 140   | Coop_la_primavera                             | Cooperativa de Ahorro y Crédito Societaria La Primavera Ltda.                   |
| 141   | Coop_paulo_vi                                 | Cooperativa de Ahorro y Crédito Societaria Paulo VI Ltda.                       |
| 142   | Coop_pirai                                    | Cooperativa de Ahorro y Crédito Societaria Piraí Ltda                           |
| 143   | Coop_reyes                                    | Cooperativa de Ahorro y Crédito Societaria Reyes Ltda.                          |
| 144   | Coop_san_bartolome                            | Cooperativa de Ahorro y Crédito Societaria San Bartolomé Ltda                   |
| 145   | Coop_san_francisco_de_asis                    | Cooperativa de Ahorro y Crédito Societaria San Francisco de Asís Ltda.          |
| 146   | Coop_san_gabriel                              | Cooperativa de Ahorro y Crédito Societaria San Gabriel Ltda.                    |
| 147   | Coop_san_martin_abierta                       | Cooperativa de Ahorro y Crédito Abierta San Martín Ltda                         |
| 148   | Coop_santisima_trinidad                       | Cooperativa de Ahorro y Crédito Societaria Santísima Trinidad Ltda              |
| 149   | Coop_senor_de_burgos                          | Cooperativa de Ahorro y Crédito Societaria Señor de Burgos Ltda.                |
| 150   | Coop_solucredit_san_silvestre                 | Cooperativa de Ahorro y Crédito Societaria Solucredit San Silvestre             |
| 151   | Coop_terracoop                                | Cooperativa de Ahorro y Crédito Societaria Terracoop Ltda.                      |
| 152   | Coop_varsa                                    | Cooperativa de Ahorro y Crédito Societaria Varsa Ltda.                          |
| 153   | Coop_via_y_obras                              | Cooperativa de Ahorro y Crédito Societaria Vía y Obras Ltda.                    |
| 154   | Coop_vinto                                    | Cooperativa de Ahorro y Crédito Societaria Vinto Ltda.                          |
| 155   | Coop_virgen_de_los_remedios                   | Cooperativa de Ahorro y Crédito Societaria Virgen de los Remedios Ltda          |
| 156   | Coop_virgen_de_urkupina                       | Cooperativa de Ahorro y Crédito Societaria Virgen de Urkupiña Ltda.             |
| 157   | Coop_santiago_de_munaypata                    | Cooperativa Multiactiva Santiago de Munaypata Ltda                              |
| 1014  | New_banco_union                               | Banco Union                                                                     |
| 1017  | New_banco_solidario                           | Banco Solidario                                                                 |
| 1001  | New_bancon_nacional                           | Banco Nacional de Bolivia                                                       |
| 1005  | New_banco_de_credito                          | Banco de Credito de Bolivia                                                     |
| 1016  | New_banco_economico                           | Banco Economico                                                                 |
| 1003  | New_banco_mercantil                           | Banco Mercantil Santa Cruz                                                      |
| 1018  | New_banco_ganadero                            | Banco Ganadero                                                                  |
| 1034  | New_banco_fortaleza                           | Banco Fortaleza                                                                 |
| 1033  | New_banco_fie                                 | Banco FIE                                                                       |
| 1009  | New_banco_bisa                                | Banco Bisa                                                                      |
| 74002 | New_banco_pyme_ecofuturo                      | Banco Pyme Ecofuturo                                                            |
| 3001  | New_coperativa_jesus_nazareno                 | Cooperativa Jesus Nazareno                                                      |
| 1007  | New_banco_de_la_nacion_argentina              | Banco de la Nacion Argentina                                                    |

---

## 🔍 Notes

- All amounts must be provided in **Bolivianos (BOB)**.
- `reference_id` must be unique per payout request.
- The `bank_code` must be sent as a **string**, even when numeric.
- Only banks listed in this document are supported.
- Invalid or unsupported bank codes will cause the request to fail.
```
