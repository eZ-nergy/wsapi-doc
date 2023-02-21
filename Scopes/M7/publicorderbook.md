# Public Order Book

| Field          | Type                                   | Comment                                                                                             |
|----------------|----------------------------------------|-----------------------------------------------------------------------------------------------------|
| isDelta        | boolean                                | Indicates if this object is part of a snapshot (`false`) or a delta to apply on a snapshot (`true`) |
| revisionNumber | long                                   | Revision number of the order book on Epex M7 side                                                   |
| contractArea   | [ContractArea](contractarea.md)        |                                                                                                     |
| buyOrders      | List of [PublicOrders](publicorder.md) |                                                                                                     |
| sellOrders     | List of [PublicOrders](publicorder.md) |                                                                                                     |

Example:
```json
 {
        "isDelta": true,
        "revisionNumber": 179,
        "contractArea": {
            "identifier": "DE-AMPRION-1022776",
            "deliveryArea": "DE-AMPRION",
            "contractName": "15Q4",
            "deliveryStart": "2022-05-02T13:45:00Z",
            "deliveryEnd": "2022-05-02T14:00:00Z",
            "product": {
                "name": "Intraday_Quarter_Hour_Power",
                "granularity": "QuarterHour",
                "type": "Local"
            }
        },
        "buyOrders": [],
        "sellOrders": [
            {
                "identifier": 322440891,
                "price": 38,
                "quantity": 2.7,
                "entryDate": "2022-05-02T13:11:15.511Z"
            },
            {
                "identifier": 322440886,
                "price": 39.1,
                "quantity": 0,
                "entryDate": "2022-05-02T13:11:06.075Z"
            }
        ]
    }
```
