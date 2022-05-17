# Product

| Field | Type | Comment                                                    |
| --- | --- |------------------------------------------------------------|
| name | string | |
| granularity | Enum | Vlaues can be `Hour`, `HalfHour` and `QuarterHour` |
| type | Enum | `Local` or `Xbid`|

Example:
```json
{
  "name": "Intraday_Quarter_Hour_Power",
  "granularity": "QuarterHour",
  "type": "Local"
}
```