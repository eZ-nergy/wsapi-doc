# Public Order

This object represents an order in a public order book.

| Field | Type | Comment |
| --- | --- | --- |
| identifier | long | Identifier of the order at Epex M7 |
| price | decimal | |
| quantity | decimal | |
| entryDate | DateTime | Date of entry in the order book |

Example:
```json
 {
  "identifier": 322440886,
  "price": 39.1,
  "quantity": 0,
  "entryDate": "2022-05-02T13:11:06.075Z"
}
```