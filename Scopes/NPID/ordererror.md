# Order Error

| Field     | Type           | Comment              |
|-----------|----------------|----------------------|
| code      | ErrorCode Enum | See below for values |
| message   | string         |                      |

Values of `ErrorCode` enum:
```
Unknown,
MissingRequiredField,
IllegalField,
FieldOutOfRange,
FieldFormatInvalid,
ItemNotFound,
ItemPending,
AccessModeViolation,
ThirdParty,
InvalidArea,
ParsingError,
RequestOverThrottling,
InternalServerError,
ConcurrentUpdate
```