# Private trade

This object represents a trade done by you or your company as a market participant.

| Field      | Type | Comment |
|------------| --- | --- |
| identifier | string | Identifier of the trade at Epex M7 |
| quantity   | decimal | |
| price      | decimal | |
| execDate   | DateTime | Date and time of the execution of the trade |
| buySide    | [TradeSide](tradeside.md) | May not be present, if not private |
| sellSide   | [TradeSide](tradeside.md) | May not be present, if not private |
| state | Enum | See below for values |
| revisionNumber | long | |

Values for state:
```
RecallRejected,
RecallGranted,
RecallRequested,
Active,
Cancelled,
CancelRequest,
CancelRejected,
RequestSentForApproval
```

Example:
```json
 {
    "identifier": "58869375",
    "quantity": 18.000,
    "price": 61.20,
    "execDate": "2022-02-04T10:08:32Z",
    "sellSide": {
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
      "userCode": "TRD004"
    },
    "state": "Active",
    "revisionNumber": 1
  }
```
