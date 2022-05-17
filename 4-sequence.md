# Concept

The `sequence` field on the envelop of the message is there to show the order of events inside a channel. The `sequence` increases incrementally with every event in a channel. The API guarantees that the event with `sequence=n` follows the event `sequence=n-1` with no other event in between.

It can happen that you receive in a different order two events sent simultaneously (but with different `sequence`). The websocket transport protocol makes it unlikely, but it can still happen. Events need to be processed following the sequence order.

The sequence is kept on the API side on a channel subscription basis. When you subscribe to a channel, it is set to 0. If you un-subscribe and re-subscribe, it will be reset to 0.

Upon a successful subscription, an initial state of the resource concerned by the channel, or snapshot, is sent with sequence 0 in order to initialize the state of the resource for the implementing application. If you need to re-initialize the state, you will need to un-subscribe and re-subscribe and use the received 0 sequence event.

You will then the `sequence` to make sure that the events are processed in the right order and that no event is missed.

# Sequence management

The correct management of sequence is critical in order to be sure of the integrity of the data you receive.

## Sequence re-ordering

Sequence re-ordering is needed to make sure that you process events in the correct order. Some data can be cumulative, so processing events in a wrong order will lead to the data being incorrect.
If the item `sequence=n` has been processed and the message `sequence=n+2` is received, then it needs to be put aside and not processed until the message `sequence=n+1` is received and processed. This mechanism needs to ensure that whatever the order in which the events are received, they should be processed according to the sequence.

If you receive an older message like `sequence=n-1` after `sequence=n`, you should not process it and just discard it.

## Sequence breaks

If, during sequence re-ordering, one event is never received, it is a sequence break. Say the event `sequence=n` has been processed and then events with `sequence=n+2`, `sequence=n+3` etc are received. This means the event with `sequence=n+1` will never be received. This is a sequence break.

In case of sequence break, you need to unsubscribe and re-subscribe in order to be sure to have a clean state of data.

Most of the time, sequence break will be detected by the API and you will be automatically unsubscribed.

# Heartbeat

As soon as you are connected to a websocket, you will receive regular heartbeat messages, one every 5 seconds. These heartbeat messages are used to make sure the connection is still up.
The message is of type `heartbeat` and the payload is composed like this:

| Field | Type | Comment |
| --- | --- | --- |
| current | DateTime | Timestamp of this event |
| next | DateTime | Time to expect next heartbeat |
| items | List (see description of items below) | List of subscribed channels and their respective sequences |


| Field | Type | Comment |
| --- | -- | --- |
| channel| URN | The urn of the channel |
| sequence | int | The sequence of the last event of the channel when the heartbeat was issued |

This list is used as part of sequence management. As you get there the sequence of all the channels you are subscribed to, you can check them against the sequence of the last item you received on each channel.

As the heartbeat and the item can be sent almost at the same time, there can be a small difference between them when you get them. If the difference continues to grow between heartbeat, you should unsubscribe and resubscribe to the channel to reset the subscription.

Example:

The sequence received on the item is `n`. The sequence on the heartbeat is `n+1`. It is fine. Then by the time of next heartbeat, if the sequence of the item is still `n` and on the heartbeat it is `n+m`, then there is a problem. If on the item it is `n+m-1`, there is still a difference, but you are receiving items, so it is fine.
