# PathRelationship


## Fields

| Field                                                              | Type                                                               | Required                                                           | Description                                                        |
| ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| `Type`                                                             | `string`                                                           | :heavy_check_mark:                                                 | Edge type (e.g. FORWARD_DNS)                                       |
| `Weight`                                                           | `*float64`                                                         | :heavy_minus_sign:                                                 | Edge weight from 0 to 1.0; lower means higher-confidence discovery |