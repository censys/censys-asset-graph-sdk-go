# ListAssetGraphsOutputBody


## Fields

| Field                                                               | Type                                                                | Required                                                            | Description                                                         | Example                                                             |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `DollarSchema`                                                      | `*string`                                                           | :heavy_minus_sign:                                                  | A URL to the JSON Schema for this object.                           | https://graph.data.censys.io/schemas/ListAssetGraphsOutputBody.json |
| `AssetGraphs`                                                       | [][components.AssetGraph](../../models/components/assetgraph.md)    | :heavy_check_mark:                                                  | List of asset graphs                                                |                                                                     |
| `NextPageToken`                                                     | `*string`                                                           | :heavy_minus_sign:                                                  | Token for the next page of results                                  |                                                                     |