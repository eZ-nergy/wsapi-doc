# Public Order Book

| Field        | Type                                   | Comment                                                                                             |
|--------------|----------------------------------------|-----------------------------------------------------------------------------------------------------|
| isDelta      | boolean                                | Indicates if this object is part of a snapshot (`false`) or a delta to apply on a snapshot (`true`) |
| updatedAt    | DateTime                               |                                                                                                     |
| contractArea | [ContractArea](contractarea.md)        |                                                                                                     |
| buyOrders    | List of [PublicOrders](publicorder.md) |                                                                                                     |
| sellOrders   | List of [PublicOrders](publicorder.md) |                                                                                                     |

Example:
```json
{
  "updatedAt": "2023-02-21T10:34:58.671Z",
  "isDelta": true,
  "contractArea": {
    "identifier": "DE-50HERTZ-NX_315731",
    "deliveryArea": "DE-50HERTZ",
    "contractName": "PH-20230221-24",
    "deliveryStart": "2023-02-21T22:00:00Z",
    "deliveryEnd": "2023-02-21T23:00:00Z",
    "type": "Xbid",
    "product": "P60Min"
  },
  "buyOrders": [],
  "sellOrders": [
    {
      "identifier": "X213456278",
      "price": 55.7,
      "quantity": 1,
      "entryDate": "2023-02-21T10:34:58.671Z"
    },
    {
      "identifier": "X213456241",
      "price": 56.3,
      "quantity": 0,
      "entryDate": "2023-02-21T10:34:58.671Z"
    }
  ]
}
```
