# Shards

## Overview

### Available Operations

* [ListShards](#listshards) - List shards

## ListShards

List shards for a completed graph execution. Each shard represents an approximately-equal partition of the execution's assets. Use the shard ID with the list assets endpoint to paginate within a single shard.

### Example Usage

<!-- UsageSnippet language="go" operationID="list-shards" method="get" path="/api/v1/asset-graphs/{graph_id}/executions/{execution_id}/shards" -->
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
        censysassetgraphsdkgo.WithXOrganizationID("b6b95e3a-683b-4315-8ff6-4577e4d17490"),
        censysassetgraphsdkgo.WithSecurity("<YOUR_BEARER_TOKEN_HERE>"),
    )

    res, err := s.Shards.ListShards(ctx, "65f6869f-38a1-482e-acf9-4191516b36b8", "64ea342e-81b6-451c-952b-7ea00509ae35", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.ListShardsOutputBody != nil {
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
| `pageToken`                                              | `*string`                                                | :heavy_minus_sign:                                       | Pagination token from a previous response                |
| `pageSize`                                               | `*int`                                                   | :heavy_minus_sign:                                       | Maximum number of results to return                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.ListShardsResponse](../../models/operations/listshardsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |