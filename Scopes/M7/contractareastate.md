# Contract area state

This object represents the state of a contract for an area.

| Field | Type | Comment |
| --- | --- | --- |
| contractArea | [ContractArea](contractarea.md) | |
| state | Enum | See below for values |
| expirationDate | DateTime | May not be present |
| tradingPhaseStart | DateTime | |
| tradingPhaseEnd | DateTime | |
| tradingPhase | Enum | |

Values for State:
```
Hibernated,
Active,
Inactive,
Standby
```

Values for tradingPhase:
```
Closed,
Continuous
```

Example:
```json
{
  "contractArea":  {
    "deliveryArea": "DE-AMPRION",
    "contractName": "H13:00-13:30_XB",
    "deliveryStart": "2022-02-03T12:00Z",
    "deliveryEnd": "2022-02-03T12:30Z",
    "product": {
      "name": "XBid-HalfHour",
      "granularity": "HalfHour",
      "marketType": "Xbid"
    }
  },
  "state": "Active",
  "tradingPhaseStart": "2022-02-02T15:00Z",
  "tradingPhaseEnd": "2022-02-03T12:20Z",
  "tradingPhase": "Continuous"
}
```
