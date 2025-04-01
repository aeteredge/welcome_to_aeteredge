# Card H2H Integration

## Mandatory Fields

The following fields are **mandatory** in the messages:

- `"reference_id"`: the unique identifier of the operation on the merchant side;  
  if you do not specify it, the API generates it itself and send in response

- `"amount"`: the invoice amount in the float format, for example: 100.55

- `"currency"`: the invoice currency, such as EUR or USD

- `"service"`: the service identifier, for example `"payment_card_eur_hpp"` or `"payment_card_usd_hpp"`

- `"customer"`:
  - `"reference_id"`: Essential for tracking and differentiating transactions (FTDs and STDs) for known customers
  - `"name"`: Always name and surname, must be at least two words
  - `"email"`:
  - `"phone"`: Numbers only
  - `"date_of_birth"`: YYYY-MM-DD
  - `"address"`:
    - `"full_address"`: Street, number, and complement
    - `"country"`: 2-letter country code
    - `"region"`: Region or State
    - `"city"`:
    - `"post_code"`:
  - `"metadata"`:
    - `"ip"`:

- `"metadata"`:
  - `"url"`:

---

## Support

If you have any questions or need assistance, our team is here to help.  
Welcome again, and we look forward to working with you!

**Best regards,**  
*The AeterEdge Team*