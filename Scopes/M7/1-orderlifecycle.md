# Order lifecycle

The API allows to create, modify or cancel orders through the `m7:private_orders` channels. It is done by sending a `request` type message with an `OrderBatch` as the payload.

## Acting on orders

### Order creation

The `type` of the `OrderBatch` is `Creation`.

On the `PrivateOrder` objects, some fields are mandatory, some are not needed.

| Field                  | Presence | Comment |
|------------------------| --- | --- |
| clientIdentifier       | Mandatory | Client identifier is always mandatory |
| identifier             | Null | Identifier should not be present for creation |
| revisionNumber         | Null | RevisionNumber should not be present for creation |
| state                  | Mandatory | State can be `Active` or `Hibernated` |
| action                 | Ignored | Set by the system |
| contractArea           | Mandatory | See below for more info. |
| quantity               | Mandatory |  |
| price                  | Mandatory |  |
| direction              | Mandatory |  |
| executionRestriction   | Optional | Defaults to `None` |
| initialQuantity        | Ignored | Set by the system |
| type                   | Ignored | `Iceberg` is assumed if the relative fields have values |
| comment                | Optional |  |
| entryDate              | Ignored | Set by the system |
| validityRestriction    | Optional | Defaults to `GoodForSession` |
| validityDate           | Optional | Mandatory if `ValidityRestriction` is `GoodUntilDate` |
| icebergVisibleQuantity | Optional | If set, `Type` will be `Iceberg` |
| icebergPriceDelta      | Optional |  |
| icebergHiddenQuantity  | Ignored | Set to `Quantity - IcebergVisibleQuantity` |

Fields of the `contractArea`:

| Field         | Presence | Comment                                                           |
|---------------| --- |-------------------------------------------------------------------|
| identifier    | Optional | If present, the contract used will be the one with the identifier |
| deliveryArea  | Mandatory | Needs to be the same as the one of the channel                    |
| contractName  | Ignored |                                                                   |
| deliveryStart | Optional | Used if no `identifier` is provided                               |
| deliveryEnd   | Optional | Used if no `identifier` is provided                               |
| product       | Ignored |                                                                   |

The `contractArea` should contain either an `identifier` or both `deliveryStart` and `deliveryEnd`. If the `identifier` is provided, then the contract used for the order will be the one specified. If dates are provided, then the contract used will be the one currently active (between local and xbid) for the delivery period.

### Order Modification

The `type` of the `OrderBatch` is `Modification`.

On the `PrivateOrder` objects, some fields are mandatory, some are not needed.

| Field                  | Presence | Comment |
|------------------------| --- | --- |
| clientIdentifier       | Mandatory | Client identifier is always mandatory |
| identifier             | Mandatory | Identifier is mandatory for modification |
| revisionNumber         | Mandatory | RevisionNumber is mandatory for modification |
| state                  | Ignored | Modification cannot change the state. |
| action                 | Ignored | Set by the system |
| contractArea           | Ignored | Cannot be modified |
| quantity               | Optional |  |
| price                  | Optional |  |
| direction              | Ignored | Cannot be modified |
| executionRestriction   | Optional |  |
| initialQuantity        | Ignored | Set by the system |
| type                   | Ignored | `Iceberg` is assumed if the relative fields have values |
| comment                | Optional |  |
| entryDate              | Ignored | Set by the system |
| validityRestriction    | Optional |  |
| validityDate           | Optional | Ignored if `ValidityRestriction` is not `GoodUntilDate` |
| icebergVisibleQuantity | Optional | If set, `Type` will be `Iceberg` |
| icebergPriceDelta      | Optional |  |
| icebergHiddenQuantity  | Ignored | Set to `Quantity - IcebergVisibleQuantity` |

### Order de-activation

The `type` of the `OrderBatch` is `Modification`.

On the `PrivateOrder` objects, some fields are mandatory, some are not needed.

| Field                  | Presence | Comment                                         |
|------------------------| --- |-------------------------------------------------|
| clientIdentifier       | Mandatory | Client identifier is always mandatory           |
| identifier             | Mandatory | Identifier is mandatory for de-activation       |
| revisionNumber         | Mandatory | RevisionNumber is mandatory for de-activation   |
| state                  | Ignored | Will be modified to `Hibernated`                |
| action                 | Ignored | Set by the system                               |
| contractArea           | Ignored | Cannot be modified                              |
| quantity               | Ignored | Cannot modify values and state at the same time |
| price                  | Ignored | Cannot modify values and state at the same time |
| direction              | Ignored | Cannot be modified                              |
| executionRestriction   | Ignored | Cannot modify values and state at the same time |
| initialQuantity        | Ignored | Set by the system                               |
| type                   | Ignored | Cannot modify values and state at the same time |
| comment                | Ignored | Cannot modify values and state at the same time |
| entryDate              | Ignored | Set by the system                               |
| validityRestriction    | Ignored | Cannot modify values and state at the same time |
| validityDate           | Ignored | Cannot modify values and state at the same time |
| icebergVisibleQuantity | Ignored | Cannot modify values and state at the same time |
| icebergPriceDelta      | Ignored | Cannot modify values and state at the same time |
| icebergHiddenQuantity  | Ignored | Cannot modify values and state at the same time |

### Order activation

The `type` of the `OrderBatch` is `Modification`.

On the `PrivateOrder` objects, some fields are mandatory, some are not needed.

| Field                  | Presence | Comment |
|------------------------| --- | --- |
| clientIdentifier       | Mandatory | Client identifier is always mandatory |
| identifier             | Mandatory | Identifier is mandatory for de-activation |
| revisionNumber         | Mandatory | RevisionNumber is mandatory for de-activation |
| state                  | Ignored | Will be modified to `Active` |
| action                 | Ignored | Set by the system |
| contractArea           | Ignored | Cannot be modified |
| quantity               | Ignored | Cannot modify values and state at the same time |
| price                  | Ignored | Cannot modify values and state at the same time |
| direction              | Ignored | Cannot be modified |
| executionRestriction   | Ignored | Cannot modify values and state at the same time |
| initialQuantity        | Ignored | Set by the system |
| type                   | Ignored | Cannot modify values and state at the same time |
| comment                | Ignored | Cannot modify values and state at the same time |
| entryDate              | Ignored | Set by the system |
| validityRestriction    | Ignored | Cannot modify values and state at the same time |
| validityDate           | Ignored | Cannot modify values and state at the same time |
| icebergVisibleQuantity | Ignored | Cannot modify values and state at the same time |
| icebergPriceDelta      | Ignored | Cannot modify values and state at the same time |
| icebergHiddenQuantity  | Ignored | Cannot modify values and state at the same time |

### Order cancellation

The `type` of the `OrderBatch` is `Modification`.

On the `PrivateOrder` objects, some fields are mandatory, some are not needed.

| Field                  | Presence | Comment |
|------------------------| --- | --- |
| clientIdentifier       | Mandatory | Client identifier is always mandatory |
| identifier             | Mandatory | Identifier is mandatory for de-activation |
| revisionNumber         | Mandatory | RevisionNumber is mandatory for de-activation |
| state                  | Ignored | Will be modified to `Inactive` |
| action                 | Ignored | Set by the system |
| contractArea           | Ignored | Cannot be modified |
| quantity               | Ignored | Cannot modify values and state at the same time |
| price                  | Ignored | Cannot modify values and state at the same time |
| direction              | Ignored | Cannot be modified |
| executionRestriction   | Ignored | Cannot modify values and state at the same time |
| initialQuantity        | Ignored | Set by the system |
| type                   | Ignored | Cannot modify values and state at the same time |
| comment                | Ignored | Cannot modify values and state at the same time |
| entryDate              | Ignored | Set by the system |
| validityRestriction    | Ignored | Cannot modify values and state at the same time |
| validityDate           | Ignored | Cannot modify values and state at the same time |
| icebergVisibleQuantity | Ignored | Cannot modify values and state at the same time |
| icebergPriceDelta      | Ignored | Cannot modify values and state at the same time |
| icebergHiddenQuantity  | Ignored | Cannot modify values and state at the same time |

## Order lifecycle: `state` and `action`

Throughout the life of an order, its `clientIdentifier` remains the same. It can be used as the primary identifier for the order.
The `idenitifier` and the `revisionNumber` identify the order at Epex M7. Note that the same order can change `identifier` if it is modified.
The `state` shows the status of the order in the system and `action` shows how it got into this state.

Note that you will receive on a `m7:private_orders` channel reports for all the orders made by you or your company as a market participant. You will need to use the `clientIdentifier` to keep track of your own orders.

Here are the lists of the different events you will receive after each of the different actions.

For the event numbers below, the letter indicates different possibilities.

### Order creation

| Event | clientIdentifier | identifier | revisionNumber | state        | action        | correlation      | Comment                                                                         |
|-------| --- |------------|----------------|--------------|---------------|------------------|---------------------------------------------------------------------------------|
| 1     | Same as in request | no value   | no value       | `Pending`    | `AddedByUser` | Same as in request | Acknowledgement                                                                 |
| 2a    | Same as in request | new value  | 1              | `Active`     | `AddedByUser` |                  | Order is on screen                                                              |
| 2b    | Same as in request | new value  | 1              | `Hibernated` | `AddedByUser` |                  | Order is on screen but inactive because it was created with `state` `Hibernated` |
| 2c    | Same as in request | -        | -              | `Rejected`   | `AddedByUser`    |  | Order has been rejected                                                         |

### Order modification

| Event | clientIdentifier | identifier | revisionNumber             | state      | action           | correlation      | Comment                                                       |
|-------| --- |------------|----------------------|------------|------------------|------------------|---------------------------------------------------------------|
| 1     | Same as in request | Same as in request   | Same as in request   | `Pending`  | `ModifiedByUser` | Same as in request | Acknowledgement                                               |
| 2a    | Same as in request | new value  | 1                    | `Active`   | `AddedByUser`    |                  | Order position in orderbook changed, M7 created a new order   |
| 2b    | Same as in request | Same as in request   | Value in request + 1 | `Active`   | `ModifiedByUser`       |  | Order position in orderbook has not changed                   |
| 2c    | Same as in request | Same as in request   | Same as in request   | `Rejected` | `ModifiedByUser`       |  | Order modification has been rejected                          |
| 3a    | Same as in request | Same as in request   | Value in request + 1  | `Inactive` | `AddedByUser`    |                  | Order position in orderbook changed, M7 removed the old order |

Note that the sequence of the different events is not guaranteed. You can receive event #3 before event #2.

### Order de-activation

| Event | clientIdentifier | identifier | revisionNumber             | state        | action           | correlation      | Comment                                     |
|-------| --- |------------|----------------------|--------------|------------------|------------------|---------------------------------------------|
| 1     | Same as in request | Same as in request   | Same as in request   | `Pending`    | `DeactivatedByUser` | Same as in request | Acknowledgement                             |
| 2a    | Same as in request | Same as in request  | Value in request + 1  | `Hibernated` | `ModifiedByUser`    |  | Order was de-activated                      |
| 2b    | Same as in request | Same as in request   | Same as in request   | `Rejected`   | `ModifiedByUser`    |  | Order modification has been rejected        |

### Order activation

| Event | clientIdentifier | identifier | revisionNumber             | state      | action           | correlation      | Comment                                     |
|-------| --- |------------|----------------------|------------|------------------|------------------|---------------------------------------------|
| 1     | Same as in request | Same as in request   | Same as in request   | `Pending`  | `AddedByUser`    | Same as in request | Acknowledgement                             |
| 2a    | Same as in request | Same as in request  | Value in request + 1  | `Active`   | `ModifiedByUser` |  | Order was activated                      |
| 2b    | Same as in request | Same as in request   | Same as in request   | `Rejected` | `ModifiedByUser` |  | Order modification has been rejected        |

### Order cancellation

| Event | clientIdentifier | identifier | revisionNumber             | state      | action           | correlation      | Comment                              |
|-------| --- |------------|----------------------|------------|------------------|------------------|--------------------------------------|
| 1     | Same as in request | Same as in request   | Same as in request   | `Pending`  | `DeletedByUser` | Same as in request | Acknowledgement                      |
| 2a    | Same as in request | Same as in request  | Value in request + 1  | `Inactive` | `ModifiedByUser`    |  | Order was cancelled                  |
| 2b    | Same as in request | Same as in request   | Same as in request   | `Rejected` | `DeletedByUser`    |  | Order cancellation has been rejected |
