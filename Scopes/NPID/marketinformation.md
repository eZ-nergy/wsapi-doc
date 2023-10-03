# Market information

| Field                      | Type                                            | Comment                                  |
|----------------------------|-------------------------------------------------|------------------------------------------|
| contractArea               | [ContractArea](contractarea.md)                 |                                          |
| dayAheadPrice              | decimal                                         | May not be present                       |
| lastTradedPrice            | decimal                                         | May not be present                       |
| lastTradedQuantity         | decimal                                         | May not be present                       |
| totalTradedQuantity        | decimal                                         | May not be present                       |
| lastTradedDate             | DateTime                                        | May not be present                       |
| highestTradedPrice         | decimal                                         | May not be present                       |
| lowestTradedPrice          | decimal                                         | May not be present                       |
| priceDirection             | Enum                                            | See below for values. May not be present |
| volumeWeightedAveragePrice | decimal                                         | May not be present                       |

Values for priceDirection:
```
Unchanged,
Up,
Down
```

Example:
```json
{
  "contractArea": {
    "identifier": "DE-50HERTZ-NX_315381",
    "deliveryArea": "DE-50HERTZ",
    "contractName": "PH-20230220-03",
    "deliveryStart": "2023-02-20T01:00:00Z",
    "deliveryEnd": "2023-02-20T02:00:00Z",
    "type": "Xbid",
    "product": "P60Min"
  },
  "dayAheadPrice": 48.86,
  "priceDirection": "Up"
}
```
