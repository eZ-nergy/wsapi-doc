# Contract area state

This object represents the state of a contract for an area.

| Field        | Type                            | Comment              |
|--------------|---------------------------------|----------------------|
| contractArea | [ContractArea](contractarea.md) |                      |
| state        | State Enum                      | See below for values |
| phaseStart   | DateTime                        |                      |
| phaseEnd     | DateTime                        |                      |

Values for `state`:
```
Hibernated,
Inactive,
Active,
Frozen
```

Example:
```json
{
  "contractArea": {
    "identifier": "DE-50HERTZ-NX_315460",
    "deliveryArea": "DE-50HERTZ",
    "contractName": "QH-20230220-55",
    "deliveryStart": "2023-02-20T12:30:00Z",
    "deliveryEnd": "2023-02-20T12:45:00Z",
    "type": "Xbid",
    "product": "P15Min"
  },
  "state": "Inactive",
  "phaseStart": "2023-02-20T12:00:00Z",
  "phaseEnd": "2023-02-20T12:00:00Z"
}
```
