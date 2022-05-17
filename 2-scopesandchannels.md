# Concepts

## Scopes

The complete business domain covered by the API is split into functional units called scopes. A scope is a set of related resources that can be accessed through the API.

A scope is for example the resources linked to the access to Epex M7 or related to manipulating Time Series. It is a logical group of resources that are related together.

## Channels

Channels are logical streams of data representing a certain resource. For example, the values for a specific time series is a channel. The different public order books for particular delivery area and product is a channel.

Some channel are generic. Other will require some attributes, for example, the id of the time series, the delivery area and product for the public order book.

For more details about a channel and its parameters, see the documentation for the channel.

## Channel urn

Every channel is represented by its [uniform resource name (or URN)](https://en.wikipedia.org/wiki/Uniform_Resource_Name).

They follow the same pattern: `urn:ez-api:<Contract>:<ResourceType>:<ResourceParamters>`.

For example, below is the URN for the M7 public order book for RTE and the quarter hour product:
```
urn:ez-api:EZ4a26927fea:m7:public_order_books:6395d740-6e55-11e8-b566-0800200c9a66:FR-RTE:QuarterHour
```
If there is a REST endpoint to complement the channel, its URL will follow the same pattern `https://<eZ-Ops host>/api/<Contract>/<ResourceType>/<ResourceParamters>`.

For example, the URL to get the M7 public order book for RTE and the quarter hour product:
```
https://<eZ-Ops host>/api/EZ4a26927fea/m7/public_order_books/6395d740-6e55-11e8-b566-0800200c9a66/FR-RTE/QuarterHour
```

# Subscriptions

It order to start receiving events in a channel, you need to subscribe to it. It is done by sending a `subscribe` request. (See the `Message` section of the documentation). The API will acknowledge the subscription with a `subscribed` event.

It is not possible to subscribe twice to the same channel (inside a single connection). An error message `error.already_subscribed` will be sent back if this happens.

If the subscription is not needed anymore, you can unsubscribe by sending an `unsubscribe` message which will be acknowledged by a `unsubscribed` event.

It can happen that an error forces the API to unsubscribe a channel. It can be because it cannot maintain the sequence of event or that the consumption of events is too slow. In this case, an `unsubscribed` event is sent and no further events are sent from the channel.
