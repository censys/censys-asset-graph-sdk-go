# GraphExecutions

## Overview

### Available Operations

* [ListGraphExecutions](#listgraphexecutions) - List graph executions
* [CreateGraphExecution](#creategraphexecution) - Create a graph execution
* [GetGraphExecution](#getgraphexecution) - Get a graph execution

## ListGraphExecutions

List all executions for an asset graph. Results are sorted by descending update time.

### Example Usage

<!-- UsageSnippet language="go" operationID="list-graph-executions" method="get" path="/api/v1/asset-graphs/{graph_id}/executions" -->
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

    res, err := s.GraphExecutions.ListGraphExecutions(ctx, "f9d06df8-c919-4692-8a03-99ab20666b9d", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.ListGraphExecutionsOutputBody != nil {
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

**[*operations.ListGraphExecutionsResponse](../../models/operations/listgraphexecutionsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |

## CreateGraphExecution

Start a new on-demand execution for an asset graph. An execution triggers the discovery process using the graph's configured seeds and excluded assets. Creating an execution will preempt and cancel any currently running execution. Executions may take up to several hours to complete.

Censys also periodically runs executions in the background. Older executions are removed automatically.

### Example Usage

<!-- UsageSnippet language="go" operationID="create-graph-execution" method="post" path="/api/v1/asset-graphs/{graph_id}/executions" -->
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

    res, err := s.GraphExecutions.CreateGraphExecution(ctx, "1247f90c-9717-4e5e-b94f-e0549b4268e3")
    if err != nil {
        log.Fatal(err)
    }
    if res.GraphExecution != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `graphID`                                                | `string`                                                 | :heavy_check_mark:                                       | Asset graph ID                                           |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.CreateGraphExecutionResponse](../../models/operations/creategraphexecutionresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |

## GetGraphExecution

Retrieve an execution, including its current status and discovery statistics.

### Example Usage

<!-- UsageSnippet language="go" operationID="get-graph-execution" method="get" path="/api/v1/asset-graphs/{graph_id}/executions/{execution_id}" -->
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

    res, err := s.GraphExecutions.GetGraphExecution(ctx, "988ebf92-1f95-4da7-a1b1-a8227500c320", "27f83f15-95b6-4c8b-a621-784630805a63")
    if err != nil {
        log.Fatal(err)
    }
    if res.GraphExecution != nil {
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
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetGraphExecutionResponse](../../models/operations/getgraphexecutionresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |