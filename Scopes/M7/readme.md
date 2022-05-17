# About M7 scope

Note: it is assumed that you have a basic knowledge about Epex M7.

# Channels

The M7 scope has the following channels.

| Name | Code | Area | Product | Urn |
| --- | --- | --- | --- | --- |
| Public order books | m7.public_order_books | X | X | `urn:ez-api:<Contract>:m7:public_order_books:<ClientGuid>:<Area>:<Product>` |
| Market information | m7.market_information | X | X | `urn:ez-api:<Contract>:m7:market_information:<ClientGuid>:<Area>:<Product>` |
| Private trades | m7.private_trades | X |  | `urn:ez-api:<Contract>:m7:private_trades:<ClientGuid>:<Area>` |
| Contract area states | m7.contract_area_states | X |  | `urn:ez-api:<Contract>:m7:contract_area_states:<ClientGuid>:<Area>` |
| Private orders | m7.private_orders | X |  | `urn:ez-api:<Contract>:m7:private_orders:<ClientGuid>:<Area>` |
| Public trades | m7.public_trades | X |  | `urn:ez-api:<Contract>:m7:public_trades:<ClientGuid>:<Area>` |

You need to subscribe per channel and provide area and product if area or product are required.

Unsubscribe is done using the same URN you provided to subscribe.

## Initial snapshot

When you subscribe, the first event you receive (`sequence=0`) is the initial set of data for the channel. It contains the data from the time of the subscription to 24 hours later in term of delivery date.

For example, for public trades, it will contain all the trades done for the delivery period of the next 24 hours. In case, there are too many, the initial snapshot can be split as explained in the section about split messages.

# Table of Contents

* [Order lifecycle](1-orderlifecycle.md)
* [ContractArea](contractarea.md)
* [ContractAreaState](contractareastate.md)
* [MarketInformation](marketinformation.md)
* [OrderBatch](orderbatch.md)
* [PrivateOrder](privateorder.md)
* [PrivateTrade](privatetrade.md)
* [Product](product.md)
* [PublicOrder](publicorder.md)
* [PublicOrderBook](publicorderbook.md)
* [PublicTrade](publictrade.md)
* [TradeSide](tradeside.md)
