# Test Scope

The test scope can be used to try out different behaviours that can happen when using the WebSocket API. It consists of multiple channels to which the client can subscribe:
| Name | Code | Urn |
| --- | --- | --- |
| Normal events | test.normal | `urn:ez-api:<Contract>:test:normal` |
| Disordered events | test.disorder | `urn:ez-api:<Contract>:test:disorder` |
| Fast events streaming | test.fast_events | `urn:ez-api:<Contract>:test:fast_events` |
| Event sequences with holes | test.with_holes | `urn:ez-api:<Contract>:test:with_holes` |

The `<Contract>` part of the urn is a required part in all scopes. However, for the Test Scope, this can be any string, because it is not used by the scope.

All events will have an empty json object as payload.
Example:

```json
{
  "type": "event",
  "channel": "urn:ez-api:TestClient:test:normal",
  "sequence": 1,
  "correlation": "ecf9754c-055b-4d79-a307-0e99921fc3d4",
  "data": "{}"
}
```

Each channel focuses on different use cases when using the WebSocket API, which are explained in the following sections.

# Table of Contents

- [Normal events channel](1-normal.md)
- [Fast events channel](2-fast.md)
- [Disordered events channel](3-disordered.md)
- [Events with holes channel](4-withholes.md)
