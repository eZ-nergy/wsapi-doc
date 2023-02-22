# Order batch

This object is used to send orders to the API for creation, modification, de-activation or cancellation.

Please refer to the `Order Lifecycle` section for more information.

| Field  | Type                                     | Comment                                                                               |
|--------|------------------------------------------|---------------------------------------------------------------------------------------|
| type   | Enum                                     | Values are `Creation`, `Modification`, `Activation`, `Deactivation` or `Cancellation` |
| orders | List of [PrivateOrders](privateorder.md) |                                                                                       |
