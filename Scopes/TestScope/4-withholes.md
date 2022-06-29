# Event sequences with holes channel

## What is it?

This channel will output an event every 1 second and leave one event out at random in a 20 second time range. The random aspect is 10% change for each event. These rules apply:

- If there has already been a hole in the sequence, the events until the end of the current 20 seconds range will not be skipped.
- If no event was skipped after the current 20 second range is finished, the last event of this range will be skipped.
- If a 20 second range is finished, the next range will start and the `skip event`-functionality will be reset.

The sequences of the events in a stream <u>could</u> look like this:

```
# event with sequence 4 is left out
1 -- 2 -- 3 -- 5 -- 7 -- 6 -- 8 -- 9 -- 10 -- ...
```

## What can I use it for?

As stated on the messages page ([`Message`](../../3-message.md)), all messages should have a sequence that is incremental by 1 each time. If a message with a sequence that is lower or higher than the `last received sequence + 1`, something went wrong and you should unsubscribe and resubscribe to get a new snapshot and continue to receive the correct events stream.
