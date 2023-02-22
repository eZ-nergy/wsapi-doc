# Trade side

This object represents one side of a private trade.

| Field           | Type                            | Comment                                                    |
|-----------------|---------------------------------|------------------------------------------------------------|
| identifier      | string                          |                                                            |
| orderIdentifier | long                            | Epex M7 identifier of the order that resulted in the trade |
| contractArea    | [ContractArea](contractarea.md) |                                                            |
| comment         | string                          | Comment coming from the order                              |
| metadata        | List of key-value pairs         | Metadata coming from the order                             |

Example:
```json
{
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
}
```
