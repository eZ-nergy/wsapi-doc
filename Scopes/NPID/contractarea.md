# Contract Area

This object contains information about the contract for a particular area.

| Field         | Type             | Comment                                                                       |
|---------------|------------------|-------------------------------------------------------------------------------|
| identifier    | string           | Uniquely identifies the ContractArea                                          |
| deliveryArea  | string           | See the [DeliveryArea](deliveryarea.md) section for a list of supported areas |
| contractName  | string           | Name of the contract for NordPool                                             |
| deliveryStart | DateTime         | Start of the delivery period                                                  |
| deliveryEnd   | DateTime         | End of the delivery period                                                    |
| type          | MarketType Enum  | See the values for `MarketType` below                                         |
| product       | ProductType Enum | See the values for `ProductType` below                                        |

Values for `MarketType`:
```
Local,
Xbid
```

Values for `ProductType`:
```
P15Min,
P30Min,
P60Min,
Block_2H,
Block_4H,
Don,
Db34,
Dp,
Dep,
Db,
CustomBlock
```

Example:
```json
{
  "identifier": "DE-50HERTZ-NX_315460",
  "deliveryArea": "DE-50HERTZ",
  "contractName": "QH-20230220-55",
  "deliveryStart": "2023-02-20T12:30:00Z",
  "deliveryEnd": "2023-02-20T12:45:00Z",
  "type": "Xbid",
  "product": "P15Min"
}
```
