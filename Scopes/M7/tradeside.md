# Trade side

This object represents one side of a private trade.

| Field | Type | Comment |
| --- | --- | --- |
| identifier | string | |
| orderIdentifier | long | Epex M7 identifier of the order that resulted in the trade |
| contractArea | [ContractArea](contractarea.md) | |
| comment | string | Comment coming from the order |
| userCode | string | Epex M7 trader identifier at the origin of the order |

Example:
```json
{
  "identifier": "58869375_S",
  "orderIdentifier": 303134066,
  "contractArea": {
    "deliveryArea": "DE-AMPRION",
    "contractName": "18-19_XB",
    "deliveryStart": "2022-02-04T17:00:00Z",
    "deliveryEnd": "2022-02-04T18:00:00Z",
    "product": {
      "name": "XBID_Hour_Power",
      "granularity": "Hour",
      "type": "Xbid"
    }
  },
  "comment": "EZ2_2051_4_2.1_M__",
  "userCode": "TRD004",
  "metadata": {
    "SESSION_NAME": "Subs IM RW 1",
    "RUN_ID": "4",
    "SESSION": "2051"
  }
}
```
