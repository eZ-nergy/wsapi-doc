# Private order

This object represents orders sent by you or your company as a market participant.

| Field                  | Type                            | Comment                                                          |
|------------------------|---------------------------------|------------------------------------------------------------------|
| identifier             | long                            | Identifier for NordPool                                          |
| clientIdentifier       | GUID                            | Identifier defined by you when posting the order                 |
| revisionNumber         | long                            | Revision of this order from NordPool point of view               |
| contractArea           | [ContractArea](contractarea.md) |                                                                  |
| quantity               | decimal                         |                                                                  |
| price                  | decimal                         |                                                                  |
| direction              | Enum                            | `Buy` or `Sell`                                                  |
| executionRestriction   | Enum                            | See below for values                                             |
| initialQuantity        | decimal                         |                                                                  |
| type                   | Enum                            | `Limit` or `Iceberg` or `UserDefinedBlock`                       |
| comment                | string                          |                                                                  |
| entryDate              | DateTime                        |                                                                  |
| timeInForce            | TimeInForce Enum                | See below for values                                             |
| validityDate           | DateTime                        | Present when `timeInForce` is `GoodToDate`                       |
| state                  | State Enum                      | See below for values                                             |
| action                 | Action Enum                     | See below for values                                             |
| icebergPriceDelta      | decimal                         | Added to the initial price whenever a new iceberg slice is added |
| icebergDisplayQuantity | decimal                         | Quantity displayed on screen                                     |
| icebergHiddenQuantity  | decimal                         | Remaining hidden quantity                                        |
| metadatas              | List of key-values              | Optional metadata                                                |
| errors                 | List of [Error](ordererror.md)  | Optional list of errors                                          |

Values for `timeInForce`:
```
ImmediateOrCancel,
FillOrKill,
GoodToDate,
GoodForSession
```

Values for `state`:
```
Hibernated,
Inactive,
Active,
Pending,
Rejected
```

Values for `action`:
```
UserAdded,
UserHibernated,
UserModified,
UserDeleted,
SystemHibernated,
SystemModified,
SystemDeleted,
SystemExpired,
PartialExecution,
FullExecution,
IcebergSliceAdded
```

Example:
```json
{
  "identifier": "X213112059",
  "clientIdentifier": "352bfce0-ec44-4aaf-8dc1-003265851b9e",
  "revisionNumber": 1,
  "contractArea": {
    "identifier": "DE-50HERTZ-NX_315543",
    "deliveryArea": "DE-50HERTZ",
    "contractName": "PH-20230220-22",
    "deliveryStart": "2023-02-20T20:00:00Z",
    "deliveryEnd": "2023-02-20T21:00:00Z",
    "type": "Xbid",
    "product": "P60Min"
  },
  "quantity": 20.2,
  "price": 96.3,
  "direction": "Buy",
  "timeInForce": "ImmediateOrCancel",
  "initialQuantity": 20.2,
  "type": "Limit",
  "comment": "FromWSAPI",
  "entryDate": "2023-02-20T12:27:54.484Z",
  "validityDate": "2023-02-20T19:30:00Z",
  "state": "Hibernated",
  "action": "UserAdded",
  "executionRestriction": "Aon",
  "metadata": {}
}
```
