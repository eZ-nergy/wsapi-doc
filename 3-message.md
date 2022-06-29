# Message format

The messages sent back and forth all follow the same format. They are `json` messages. The name of the fields is lowercase with no space. The values, when from a string enum, are Pascal case (like this PascalCase).

Dates and times are expressed in ISO-8601 format in UTC like this: `2022-05-22T15:02.23Z`.

The messages are comprised of an envelop and a payload. The fields of the envelop are strictly defined.

| Field       | Type   | Comment                                                                                                                                            |
| ----------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| type        | string | Type of the message. See below.                                                                                                                    |
| channel     | URN    | Channel of the message                                                                                                                             |
| sequence    | long   | Sequence of the message for the channel. Only for event messages                                                                                   |
| correlation | string | Set on a request sent to the API, it will be present on all the responses from the API                                                             |
| part        | int    | In case of split messages, indicate the part of the message (From 0 to N)                                                                          |
| totalparts  | int    | In case of split messages, indicates the total number of parts to expect (N)                                                                       |
| data        | string | Content of the message. It is a json object or list serialized. See the specific documentation of the channel for more information about the type. |

## Correlation

As the message exchange happens on a single full duplex connection, requests and responses may not be easy to match. `correlation` is there to help with this problem. Whenever you send a message to the API, you can add a `correlation` string. This `correlation` string will be added by the API to responses of the message.
For example, if a `subscribe` message has a correlation, the corresponding `subscribed` will have the same. It can be useful if you send several messages at once to verify which ones are successful or not.

`correlation` is a string less than 512 bytes long. Best practice is to use something like a GUID as it is random with virtually no risk of collision.

## Split messages

If the payload of the message is too big, it can be split into several messages. In that case, two fields will be added: `part` containing the index of the current part and `totalparts` the total number of parts. The `sequence` will increase as for other messages.

Example: a message is split in four parts.

Message #1:

```json
{
  ...
  "sequence": 45,
  "part": 1,
  "totalparts": 4,
  ...
}
```

Message #2:

```json
{
  ...
  "sequence": 46,
  "part": 2,
  "totalparts": 4,
  ...
}
```

Message #3:

```json
{
  ...
  "sequence": 47,
  "part": 3,
  "totalparts": 4,
  ...
}
```

Message #4:

```json
{
  ...
  "sequence": 48,
  "part": 4,
  "totalparts": 4,
  ...
}
```

The client will need to merge all the partial messages before processing them. The merging will depend on the type of message, that is to say the channel. If the data is a list, then the final list is the concatenation of the partial lists.
In case of other object, please refer to the dedicated part of the documentation to know how to handle them.

# Message types

There is a fixed number of message types:

| Name          | Direction | Comment                                                                                                            |
| ------------- | --------- | ------------------------------------------------------------------------------------------------------------------ |
| subscribe     | emission  | Used to subscribe to a channel                                                                                     |
| subscribed    | reception | Sent upon a successful subscription                                                                                |
| unsubscribe   | emission  | Used to un-subscribe to a channel                                                                                  |
| unsubscribed  | reception | Sent upon an un-subscription of a channel.                                                                         |
| request       | emission  | Sent to request an action on a channel. See the specific documentation of the channel for more information.        |
| event         | reception | Used to represent data flowing on the channel. See the specific documentation of the channel for more information. |
| heartbeat     | reception | Regular heartbeat message. It contains the sequence of all the channels currently subscribed.                      |
| error         | reception | Used to represent an error that occurred                                                                           |
| token_refresh | reception | Sent when the acess token is about to expire                                                                       |

## Token refresh

The `token refresh` event will be sent out in the 5 minutes before the access token is about to expire. The payload of the event will contain a new access token that is valid for the whole period again.

```json
{
  "type": "token_refresh",
  "data": "{\"token\": \"<new access token>\"}"
}
```

The new token can be read from the payload and used to make new rest calls. Internally, the new is automatically refreshed for the open websocket connections.
