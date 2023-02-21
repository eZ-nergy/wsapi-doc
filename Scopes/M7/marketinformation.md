# Market information

| Field                      | Type                            | Comment                                  |
|----------------------------|---------------------------------|------------------------------------------|
| contractArea               | [ContractArea](contractarea.md) |                                          |
| lastTradedPrice            | decimal                         | May not be present                       |
| lastTradedQuantity         | decimal                         | May not be present                       |
| totalTradedQuantity        | decimal                         | May not be present                       |
| lastTradedDate             | DateTime                        | May not be present                       |
| highestTradedPrice         | decimal                         | May not be present                       |
| lowestTradedPrice          | decimal                         | May not be present                       |
| priceDirection             | Enum                            | See below for values. May not be present |
| volumeWeightedAveragePrice | decimal                         | May not be present                       |

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
    "identifier": "DE-AMPRION-1023078",
    "deliveryArea": "DE-AMPRION",
    "contractName": "22-23",
    "deliveryStart": "2022-05-02T20:00:00Z",
    "deliveryEnd": "2022-05-02T21:00:00Z",
    "product": {
      "name": "Intraday_Hour_Power",
      "granularity": "Hour",
      "type": "Local"
    }
  },
  "totalTradedQuantity": 0,
  "priceDirection": "Unchanged"
}
```
