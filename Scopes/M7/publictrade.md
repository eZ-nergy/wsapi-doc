# Public trade

This object represents any trade that happened on Epex M7.

| Field            | Type                            | Comment                            |
|------------------|---------------------------------|------------------------------------|
| identifier       | string                          | Identifier of the trade at Epex M7 |
| revisionNumber   | long                            |                                    |
| price            | decimal                         |                                    |
| quantity         | decimal                         |                                    |
| state            | Enum                            | See below for values               |
| buyContractArea  | [ContractArea](contractarea.md) | Buy side of the trade              |
| sellContractArea | [ContractArea](contractarea.md) | Sell side of the trade             |
| execDate         | DateTime                        |                                    |

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
  "identifier": "65111271",
  "revisionNumber": 1,
  "price": 175,
  "quantity": 1.2,
  "state": "Active",
  "sellContractArea": {
    "identifier": "DE-AMPRION-1022769",
    "deliveryArea": "DE-AMPRION",
    "contractName": "15Q3",
    "deliveryStart": "2022-05-02T13:30:00Z",
    "deliveryEnd": "2022-05-02T13:45:00Z",
    "product": {
      "name": "Intraday_Quarter_Hour_Power",
      "granularity": "QuarterHour",
      "type": "Local"
    }
  },
  "buyContractArea": {
    "identifier": "DE-TENNET-1022769",
    "deliveryArea": "DE-TENNET",
    "contractName": "15Q3    ",
    "deliveryStart": "2022-05-02T13:30:00Z",
    "deliveryEnd": "2022-05-02T13:45:00Z",
    "product": {
      "name": "Intraday_Quarter_Hour_Power",
      "granularity": "QuarterHour",
      "type": "Local"
    }
  },
  "execDate": "2022-05-02T12:56:02.739Z"
}
```
