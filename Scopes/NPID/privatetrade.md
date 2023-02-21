# Private trade

This object represents a trade done by you or your company as a market participant.

| Field          | Type                      | Comment                                     |
|----------------|---------------------------|---------------------------------------------|
| identifier     | string                    | Identifier of the trade at NordPool         |
| quantity       | decimal                   |                                             |
| price          | decimal                   |                                             |
| execDate       | DateTime                  | Date and time of the execution of the trade |
| buySide        | [TradeSide](tradeside.md) | May not be present, if not private          |
| sellSide       | [TradeSide](tradeside.md) | May not be present, if not private          |
| state          | State Enum                | See below for values                        |
| revisionNumber | long                      |                                             |

Values for `State`:
```
Completed,
Disputed,
NotCancelled,
Cancelled
```

Example:
```json
{
  "identifier": "X42445956",
  "quantity": 0.1,
  "price": 132,
  "currency": "EUR",
  "execDate": "2023-02-21T10:22:26.184Z",
  "sellSide": {
    "identifier": "X42445956_S",
    "orderIdentifier": "6e041182-0cbc-4fe6-9941-98673868028e",
    "contractArea": {
      "identifier": "DE-50HERTZ-NX_315675",
      "deliveryArea": "DE-50HERTZ",
      "contractName": "PH-20230221-16",
      "deliveryStart": "2023-02-21T14:00:00Z",
      "deliveryEnd": "2023-02-21T15:00:00Z",
      "type": "Xbid",
      "product": "P60Min"
    },
    "comment": "EZ2_1162_8_1.1_M__",
    "metadata": {
      "SESSION_NAME": "Session 1",
      "RUN_ID": "8",
      "SESSION": "1162"
    }
  },
  "state": "Completed",
  "revisionNumber": 1
}
```
