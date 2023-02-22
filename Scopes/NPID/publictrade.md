# Public trade

This object represents any trade that happened on NordPool.

| Field            | Type                            | Comment                             |
|------------------|---------------------------------|-------------------------------------|
| identifier       | string                          | Identifier of the trade at NordPool |
| revisionNumber   | long                            |                                     |
| price            | decimal                         |                                     |
| quantity         | decimal                         |                                     |
| state            | Enum                            | See below for values                |
| buyContractArea  | [ContractArea](contractarea.md) | Buy side of the trade               |
| sellContractArea | [ContractArea](contractarea.md) | Sell side of the trade              |
| execDate         | DateTime                        |                                     |

Values for state:
```
Completed,
Disputed,
NotCancelled,
Cancelled
```

Example:
```json
{
  "identifier": "X42447000",
  "revisionNumber": 0,
  "price": 149,
  "quantity": 0.1,
  "state": "Completed",
  "sellContractArea": {
    "identifier": "DE-50HERTZ-NX_315668",
    "deliveryArea": "DE-50HERTZ",
    "contractName": "PH-20230221-15",
    "deliveryStart": "2023-02-21T13:00:00Z",
    "deliveryEnd": "2023-02-21T14:00:00Z",
    "type": "Xbid",
    "product": "P60Min"
  },
  "buyContractArea": {
    "identifier": "DE-50HERTZ-NX_315668",
    "deliveryArea": "DE-50HERTZ",
    "contractName": "PH-20230221-15",
    "deliveryStart": "2023-02-21T13:00:00Z",
    "deliveryEnd": "2023-02-21T14:00:00Z",
    "type": "Xbid",
    "product": "P60Min"
  },
  "execDate": "2023-02-21T10:39:03.997Z"
}
```
