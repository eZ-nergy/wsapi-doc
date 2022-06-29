# Fast events streaming channel

## What is it?

This channel will output an event on every tick on the server. Most of the time, this will result in about 2000-3000 events per second. The sequences will be in the correct order.

The sequences of the events in a stream will look like this:

```
1 -- 2 -- 3 -- 4 -- 5 -- 6 -- 7 -- 8 -- 9 -- 10 -- ...
```

## What can I use it for?

Stress testing of your client to see it can handle a massive amount of events in a short time period.
