# Assets

## Overview

### Available Operations

* [ListAssets](#listassets) - List assets
* [GetAsset](#getasset) - Get an asset

## ListAssets

List assets discovered in a graph execution. Each execution represents a complete snapshot of the attack surface.

Only partial asset data is returned when listing. Use the get asset endpoint to retrieve full asset data including discovery paths.

### Example Usage

<!-- UsageSnippet language="go" operationID="list-assets" method="get" path="/api/v1/asset-graphs/{graph_id}/executions/{execution_id}/assets" -->
```go
package main

import(
	"context"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"github.com/censys/censys-asset-graph-sdk-go/models/operations"
	"log"
)

func main() {
    ctx := context.Background()

    s := censysassetgraphsdkgo.New()

    res, err := s.Assets.ListAssets(ctx, operations.ListAssetsRequest{
        GraphID: "b5bc5310-a2a3-4f4b-8ba7-0eed4e23a166",
        ExecutionID: "<id>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.ListAssetsOutputBody != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                    | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `ctx`                                                                        | [context.Context](https://pkg.go.dev/context#Context)                        | :heavy_check_mark:                                                           | The context to use for the request.                                          |
| `request`                                                                    | [operations.ListAssetsRequest](../../models/operations/listassetsrequest.md) | :heavy_check_mark:                                                           | The request object to use for the request.                                   |
| `opts`                                                                       | [][operations.Option](../../models/operations/option.md)                     | :heavy_minus_sign:                                                           | The options for this request.                                                |

### Response

**[*operations.ListAssetsResponse](../../models/operations/listassetsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |

## GetAsset

Retrieve full data for a single discovered asset, including discovery paths showing how it was found from your seeds.

### Example Usage

<!-- UsageSnippet language="go" operationID="get-asset" method="get" path="/api/v1/asset-graphs/{graph_id}/executions/{execution_id}/assets/{asset_id}" -->
```go
package main

import(
	"context"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := censysassetgraphsdkgo.New()

    res, err := s.Assets.GetAsset(ctx, "f04de8ec-9e82-4cbd-a275-517e1de9a07f", "<id>", "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.AssetResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `graphID`                                                | `string`                                                 | :heavy_check_mark:                                       | Asset graph ID                                           |
| `executionID`                                            | `string`                                                 | :heavy_check_mark:                                       | Graph execution ID                                       |
| `assetID`                                                | `string`                                                 | :heavy_check_mark:                                       | Hex-encoded asset identifier                             |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetAssetResponse](../../models/operations/getassetresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |