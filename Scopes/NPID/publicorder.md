# Public Order

This object represents an order in a public order book.

| Field      | Type     | Comment                             |
|------------|----------|-------------------------------------|
| identifier | long     | Identifier of the order at NordPool |
| price      | decimal  |                                     |
| quantity   | decimal  |                                     |
| entryDate  | DateTime | Date of entry in the order book     |

Example:
```json
{
  "identifier": "X213456278",
  "price": 55.7,
  "quantity": 1,
  "entryDate": "2023-02-21T10:34:58.671Z"
}
```