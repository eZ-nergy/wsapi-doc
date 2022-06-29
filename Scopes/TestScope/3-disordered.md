# Disordered events channel

## What is it?

This channel will output an event every 200ms and at random moments, send a message with a higher sequence before the next sequence.
The random aspect is set to a 20% chance for each event. **This does not mean that 1 in 5 events will be disordered.** It means that the probability for each event to be disordered is 20%.

The sequences of the events in a stream <u>could</u> look like this:

```
# events with sequence 3 and 4 and with sequence 6 and 7 and disordered
1 -- 2 -- 4 -- 3 -- 5 -- 7 -- 6 -- 8 -- 9 -- 10 -- ...
```

## What can I use it for?

As stated on the messages page ([`Message`](../../3-message.md)), all messages should have a sequence that is incremental by 1 each time. If a message with a sequence that is lower or higher than the `last received sequence + 1`, something went wrong and you should unsubscribe and resubscribe to get a new snapshot and continue to receive the correct events stream.
