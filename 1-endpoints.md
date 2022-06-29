# API endpoints

## Websocket endpoint

The main transport protocol of this API is [Websocket](https://en.wikipedia.org/wiki/WebSocket) providing a full duplex channel on a single TCP connection. This allows a client to receive and send data using one single connection. This endpoint is to receive live data without the need of regularly querying.

The URL of the endpoint is:

```
wss://<eZ-Ops host>/ws
```

## REST endpoint

A companion REST endpoint is also provided in order to be able to query data that was not received live, like past data for example.

The URL of the endpoint is:

```
https://<eZ-Ops host>/api
```

# Authentication

## Getting an auth token

The first step in order to be able to connect to the API is to request an Auth token. It is done by POSTing a request with your credentials on the auth REST endpoint.

| Field   | Value |
|---------| --- |
| Method  | POST |
| URL     | https://\<eZ-Ops host\>/api/auth |
| Headers | Content-Type: application/json<br />Accept: application/json |
| Body    | `{  "username": "<username>",  "password": "<password>"}` |

HTTP response code will tell the success of the request:

| Code | Result |
| --- | --- |
| 200 | The user is authenticated and a token is provided |
| 401 | The user is not authenticated |

In case of a 200, the body is a json object containing the token. Example:

```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJhd3MtZnJ0LXdlYi0xLmV6LW5lcmd5LmxvY2FsOjkwMTQiLCJzdWIiOiJlei13c2FwaS10ZXN0cyIsImdyb3VwcyI6IkVaMjRlMWQ5ZjJkMyIsInN0a24iOiIwZTQwOWU4Mi1iMWU1LTQxOWYtOTBhMy1jMjRhODAwMzM1ODYiLCJuYmYiOjE2NTE4NDEyMTMsImV4cCI6MTY1MTkwMTIxMywiaWF0IjoxNjUxODQxMjEzfQ.ROsZZAD37Xkqtj589cxBjZE5uMNNcmMG2_5IfnW9CPw"
}
```

## Using the token

The token is then used in all subsequent calls to the API, be them websocket connection or REST calls. It is used in an `Authorization` header of type `bearer`. See following example:

```
Authorization: bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJhd3MtZnJ0LXdlYi0xLmV6LW5lcmd5LmxvY2FsOjkwMTQiLCJzdWIiOiJlei13c2FwaS10ZXN0cyIsImdyb3VwcyI6IkVaMjRlMWQ5ZjJkMyIsInN0a24iOiIwZTQwOWU4Mi1iMWU1LTQxOWYtOTBhMy1jMjRhODAwMzM1ODYiLCJuYmYiOjE2NTE4NDEyMTMsImV4cCI6MTY1MTkwMTIxMywiaWF0IjoxNjUxODQxMjEzfQ.ROsZZAD37Xkqtj589cxBjZE5uMNNcmMG2_5IfnW9CPw
```

If this header is missing or ill-formed, or if the token is expired, the api will return a 401 instead of the expected response.

> Note: the token can expire. If so, it will stop working and respond with 401. In that case, you should request a new one.  
While connected to the websocket, you will receive a message when the token is nearing expiration, about 5 minutes before it expires. See [Message Type Token refresh](3-message.md#token_refresh)
