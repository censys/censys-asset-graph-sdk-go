# ListAssetsRequest


## Fields

| Field                                     | Type                                      | Required                                  | Description                               |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| `XOrganizationID`                         | `*string`                                 | :heavy_minus_sign:                        | Censys organization ID                    |
| `GraphID`                                 | `string`                                  | :heavy_check_mark:                        | Asset graph ID                            |
| `ExecutionID`                             | `string`                                  | :heavy_check_mark:                        | Graph execution ID                        |
| `PageToken`                               | `*string`                                 | :heavy_minus_sign:                        | Pagination token from a previous response |
| `PageSize`                                | `*int`                                    | :heavy_minus_sign:                        | Maximum number of results to return       |
| `Risks`                                   | `*bool`                                   | :heavy_minus_sign:                        | If true, only return assets with risks    |