# ExcludedAssets

## Overview

### Available Operations

* [ListExcludedAssets](#listexcludedassets) - List excluded assets
* [CreateExcludedAsset](#createexcludedasset) - Create an excluded asset
* [DeleteExcludedAsset](#deleteexcludedasset) - Delete an excluded asset

## ListExcludedAssets

List all excluded assets configured for an asset graph.

### Example Usage

<!-- UsageSnippet language="go" operationID="list-excluded-assets" method="get" path="/api/v1/asset-graphs/{graph_id}/excluded-assets" -->
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

    res, err := s.ExcludedAssets.ListExcludedAssets(ctx, "d35e689a-f077-4c42-9a51-c910d405951a", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.ListExcludedAssetsOutputBody != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `graphID`                                                | `string`                                                 | :heavy_check_mark:                                       | Asset graph ID                                           |
| `pageToken`                                              | `*string`                                                | :heavy_minus_sign:                                       | Pagination token from a previous response                |
| `pageSize`                                               | `*int`                                                   | :heavy_minus_sign:                                       | Maximum number of results to return                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.ListExcludedAssetsResponse](../../models/operations/listexcludedassetsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |

## CreateExcludedAsset

Exclude an asset from an asset graph. Excluded assets will not appear in the graph and will not be used to discover additional assets.

Modifications to excluded assets take effect during the next execution of the graph.

### Example Usage

<!-- UsageSnippet language="go" operationID="create-excluded-asset" method="post" path="/api/v1/asset-graphs/{graph_id}/excluded-assets" -->
```go
package main

import(
	"context"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"github.com/censys/censys-asset-graph-sdk-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := censysassetgraphsdkgo.New()

    res, err := s.ExcludedAssets.CreateExcludedAsset(ctx, "7963bfbf-3604-4856-9d82-e629613f61d0", components.AssetRefInput{})
    if err != nil {
        log.Fatal(err)
    }
    if res.ExcludedAsset != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `ctx`                                                                | [context.Context](https://pkg.go.dev/context#Context)                | :heavy_check_mark:                                                   | The context to use for the request.                                  |
| `graphID`                                                            | `string`                                                             | :heavy_check_mark:                                                   | Asset graph ID                                                       |
| `body`                                                               | [components.AssetRefInput](../../models/components/assetrefinput.md) | :heavy_check_mark:                                                   | N/A                                                                  |
| `opts`                                                               | [][operations.Option](../../models/operations/option.md)             | :heavy_minus_sign:                                                   | The options for this request.                                        |

### Response

**[*operations.CreateExcludedAssetResponse](../../models/operations/createexcludedassetresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |

## DeleteExcludedAsset

Remove an asset exclusion from an asset graph. The asset may reappear in future execution results.

The removal takes effect during the next execution of the graph.

### Example Usage

<!-- UsageSnippet language="go" operationID="delete-excluded-asset" method="delete" path="/api/v1/asset-graphs/{graph_id}/excluded-assets/{excluded_asset_id}" -->
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

    res, err := s.ExcludedAssets.DeleteExcludedAsset(ctx, "160820a0-7989-4300-88e0-d23b52a8630c", "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.ErrorModel != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `graphID`                                                | `string`                                                 | :heavy_check_mark:                                       | Asset graph ID                                           |
| `excludedAssetID`                                        | `string`                                                 | :heavy_check_mark:                                       | Excluded asset identifier                                |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.DeleteExcludedAssetResponse](../../models/operations/deleteexcludedassetresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |