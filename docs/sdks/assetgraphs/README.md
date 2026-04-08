# AssetGraphs

## Overview

### Available Operations

* [ListAssetGraphs](#listassetgraphs) - List asset graphs
* [CreateAssetGraph](#createassetgraph) - Create an asset graph
* [DeleteAssetGraph](#deleteassetgraph) - Delete an asset graph
* [GetAssetGraph](#getassetgraph) - Get an asset graph

## ListAssetGraphs

List all asset graphs belonging to your Censys organization.

### Example Usage

<!-- UsageSnippet language="go" operationID="list-asset-graphs" method="get" path="/api/v1/asset-graphs" -->
```go
package main

import(
	"context"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := censysassetgraphsdkgo.New(
        censysassetgraphsdkgo.WithXOrganizationID("<id>"),
        censysassetgraphsdkgo.WithSecurity("<YOUR_BEARER_TOKEN_HERE>"),
    )

    res, err := s.AssetGraphs.ListAssetGraphs(ctx, nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.ListAssetGraphsOutputBody != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `pageToken`                                              | `*string`                                                | :heavy_minus_sign:                                       | Pagination token from a previous response                |
| `pageSize`                                               | `*int`                                                   | :heavy_minus_sign:                                       | Maximum number of results to return                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.ListAssetGraphsResponse](../../models/operations/listassetgraphsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |

## CreateAssetGraph

Create a new asset graph. An asset graph provides comprehensive visibility into your Internet-facing assets. It is the parent resource for seeds, excluded assets, and executions.

### Example Usage

<!-- UsageSnippet language="go" operationID="create-asset-graph" method="post" path="/api/v1/asset-graphs" -->
```go
package main

import(
	"context"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := censysassetgraphsdkgo.New(
        censysassetgraphsdkgo.WithXOrganizationID("<id>"),
        censysassetgraphsdkgo.WithSecurity("<YOUR_BEARER_TOKEN_HERE>"),
    )

    res, err := s.AssetGraphs.CreateAssetGraph(ctx, "<value>", nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.AssetGraph != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `name`                                                   | `string`                                                 | :heavy_check_mark:                                       | User-defined name for this asset graph                   |
| `description`                                            | `*string`                                                | :heavy_minus_sign:                                       | Optional description                                     |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.CreateAssetGraphResponse](../../models/operations/createassetgraphresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |

## DeleteAssetGraph

Permanently delete an asset graph and all of its associated data, including seeds, excluded assets, and executions.

### Example Usage

<!-- UsageSnippet language="go" operationID="delete-asset-graph" method="delete" path="/api/v1/asset-graphs/{id}" -->
```go
package main

import(
	"context"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := censysassetgraphsdkgo.New(
        censysassetgraphsdkgo.WithXOrganizationID("<id>"),
        censysassetgraphsdkgo.WithSecurity("<YOUR_BEARER_TOKEN_HERE>"),
    )

    res, err := s.AssetGraphs.DeleteAssetGraph(ctx, "009429a2-6b82-497f-9ae1-223df79f1e72")
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
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | Asset graph ID                                           |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.DeleteAssetGraphResponse](../../models/operations/deleteassetgraphresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |

## GetAssetGraph

Retrieve an asset graph, including its active execution if one exists.

### Example Usage

<!-- UsageSnippet language="go" operationID="get-asset-graph" method="get" path="/api/v1/asset-graphs/{id}" -->
```go
package main

import(
	"context"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := censysassetgraphsdkgo.New(
        censysassetgraphsdkgo.WithXOrganizationID("<id>"),
        censysassetgraphsdkgo.WithSecurity("<YOUR_BEARER_TOKEN_HERE>"),
    )

    res, err := s.AssetGraphs.GetAssetGraph(ctx, "c3a969eb-c4a5-4c72-9e09-5924e3fec791")
    if err != nil {
        log.Fatal(err)
    }
    if res.AssetGraph != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | `string`                                                 | :heavy_check_mark:                                       | Asset graph ID                                           |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetAssetGraphResponse](../../models/operations/getassetgraphresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |