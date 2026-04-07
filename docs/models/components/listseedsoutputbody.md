# ListSeedsOutputBody


## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   | Example                                                       |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `DollarSchema`                                                | `*string`                                                     | :heavy_minus_sign:                                            | A URL to the JSON Schema for this object.                     | https://graph.data.censys.io/schemas/ListSeedsOutputBody.json |
| `NextPageToken`                                               | `*string`                                                     | :heavy_minus_sign:                                            | Token for the next page of results                            |                                                               |
| `Seeds`                                                       | [][components.Seed](../../models/components/seed.md)          | :heavy_check_mark:                                            | List of seeds                                                 |                                                               |