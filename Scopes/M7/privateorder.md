# Private order

This object represents orders sent by you or your company as a market participant.

| Field            | Type         | Comment                                               |
|------------------|--------------|-------------------------------------------------------|
| identifier       | long         | Identifier for Epex M7                                |
| clientIdentifier | GUID         | Identifier defined by you when posting the order      |
| revisionNumber   | long         | Revision of this order from Epex M7 point of view     |
| contractArea     | ContractArea |                                                       |
| quantity         | decimal      |                                                       |
| price            | decimal      |                                                       |
| direction |  Enum        | `Buy` or `Sell`                                       |
| executionRestriction | Enum | See below for values                                  | 
| initialQuantity | decimal |                                                       |
| type | Enum | `Regular` or `Iceberg` or `Block`                     |
| comment | string |                                                       |
| entryDate | DateTime |                                                       |
| validityRestriction | Enum | `GoodForSession` or `GoodUntilDate`                   |
| validityDate | DateTime | Present when `validityRestriction` is `GoodUntilDate` |
| state | Enum | See below for values                                  |
| action | Enum | See below for values                                  |
| icebergPriceDelta | decimal | Added to the initial price whenever a new iceberg slice is added |
| icebergDisplayQuantity | decimal | Quantity displayed on screen |
| icebergHidenQuantity | decimal | Remaining hidden quantity |

Values for `state`:
```
Unknown,
Hibernated,
Inactive,
Active,
Pending,
Rejected
```

Values for `action`:
```
Unknown,
AddedByUser,
DeactivatedByUser,
ModifiedByUser,
DeletedByUser,
RejectedByUser,
AddedByMarketOps,
DeactivatedByMarketOps,
ModifiedByMarketOps,
DeletedByMarketOps,
RejectedByMarketOps,
AddedBySystem,
DeactivatedBySystem,
ModifiedBySystem,
DeletedBySystem,
RejectedBySystem,
FullyExecuted,
PartiallyExecuted,
NewIcebergSliceAdded,
QuoteAdded,
QuoteFullyExecuted,
QuotePartiallyExecuted,
SharedOrderBookUnavailability,
SharedError
```

Example:
```json
{
  "identifier": 4654964631,
  "clientIdentifier": "1a449683-e416-4271-8151-a37dde77e272",
  "revisionNumber": 1,
  "contractArea": {
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
  "quantity": 456.2,
  "price": 456.89,
  "direction": "Buy",
  "executionRestriction": "ImmediateOrCancel",
  "initialQuantity": 568.2,
  "type": "Regular",
  "comment": "EZ2_152_45_12.1__I_",
  "entryDate": "2022-02-03T10:25:45Z",
  "validityRestriction": "GoodForSession",
  "state": "Active",
  "action": "PartiallyExecuted",
  "metadata": {}
}
```