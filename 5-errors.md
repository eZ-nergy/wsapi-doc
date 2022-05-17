# Errors

When an error occurs, it is sent as an event of type `error`. Depending on the error, the `channel` field may or may not be present. If the error is due to an action in a channel, it will be present. Otherwise, it will not be there.

The payload of the error is as is:

| Field | Type | Comment |
| --- | --- | --- |
| code | string | The code for the error |
| message | string | A message giving more context on the error |

## Generic error codes

These error message will not have a channel:

| Error code | Comment | Message |
| --- | --- | --- |
| error.unknown_channel | Happens when trying to subscribe to a channel that does not exists | The message contains the channel |
| error.already_subscribed | Happens when trying to subscribe to a channel you are already subscribed to | No message. Use correlation to match with request |
| error.not_subscribed | Happens when un-subscribing to a channel you are not subscribed to | The message contains the scope of the channel |
| error.unauthorized | Happens when trying to access a resource that is not allowed for this user | Use correlation to match with request |
| error.not_processed | Happens when an error prevented the request to be processed. See the message for more information. | The message contains the request that was not processed |

## Specific error codes

More information on scope or channel specific error codes can be found in the section of the documentation about the channels.
