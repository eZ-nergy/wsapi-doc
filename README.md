# About

Welcome to the documentation for eZ-nergy Websocket API.

# Audience

The target audience for this documentation is a developer wanting to implement a client for eZ-nergy websocket API. Knowing how to connect to a websocket and how to consume REST APIs in the target language is a pre-requisite.

# Revisions

| Date | Author | Description |
| --- | --- | --- |
| 2022-05-10 | Callixte Cauchois | Initial version |


# Table of content

* Endpoints and connection
  * WS and REST endpoints
  * authentication workflow
* Scopes and Channels
  * concepts
  * WS URN vs REST URL
  * subscription, unsubscription, resubscription
  * heartbeats
* Messages encapsulation
  * message format
  * message types
  * correlation
* Sequence
  * concept
  * heartbeats
  * sequence re-ordering
  * sequence break
* Errors
  * error types
* Scopes
  * M7
    * Contract area states
    * Public order books
    * Public trades
    * Market information
    * Private trades
    * Private orders
      * workflow
    * Private trades
  * Nordpool Intraday
    * Contract area states
    * Public order books
    * Public trades
    * Market information
    * Private trades
    * Private orders
      * workflow
    * Private trades
