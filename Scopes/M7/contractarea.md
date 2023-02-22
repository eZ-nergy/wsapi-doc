# Contract Area

This object contains information about the contract for a particular area.

| Field         | Type                  | Comment                                                                       |
|---------------|-----------------------|-------------------------------------------------------------------------------|
| identifier    | string                | Uniquely identifies the ContractArea                                          |
| deliveryArea  | string                | See the [DeliveryArea](deliveryarea.md) section for a list of supported areas |
| contractName  | string                | Name of the contract for Epex M7                                              |
| deliveryStart | DateTime              | Start of the delivery period                                                  |
| deliveryEnd   | DateTime              | End of the delivery period                                                    |
| product       | [Product](product.md) |                                                                               |

Example:
```json
{
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
}
```
