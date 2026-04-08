# Seeds

## Overview

### Available Operations

* [ListSeeds](#listseeds) - List seeds
* [CreateSeed](#createseed) - Create a seed
* [DeleteSeed](#deleteseed) - Delete a seed

## ListSeeds

List all seeds configured for an asset graph.

### Example Usage

<!-- UsageSnippet language="go" operationID="list-seeds" method="get" path="/api/v1/asset-graphs/{graph_id}/seeds" -->
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

    res, err := s.Seeds.ListSeeds(ctx, "af9f272d-bff3-4350-960e-ea83efacf348", nil, nil)
    if err != nil {
        log.Fatal(err)
    }
    if res.ListSeedsOutputBody != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `graphID`                                                | `string`                                                 | :heavy_check_mark:                                       | Asset graph ID                                           |
| `xOrganizationID`                                        | `*string`                                                | :heavy_minus_sign:                                       | Censys organization ID                                   |
| `pageToken`                                              | `*string`                                                | :heavy_minus_sign:                                       | Pagination token from a previous response                |
| `pageSize`                                               | `*int`                                                   | :heavy_minus_sign:                                       | Maximum number of results to return                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.ListSeedsResponse](../../models/operations/listseedsresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |

## CreateSeed

Add a seed to an asset graph. Seeds are persistent starting points used to discover additional assets. Supported seed types include IP addresses, domains, CIDRs, ASNs, certificates, and web properties.

Modifications to seeds take effect during the next execution of the graph.

### Example Usage

<!-- UsageSnippet language="go" operationID="create-seed" method="post" path="/api/v1/asset-graphs/{graph_id}/seeds" -->
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

    s := censysassetgraphsdkgo.New(
        censysassetgraphsdkgo.WithXOrganizationID("<id>"),
        censysassetgraphsdkgo.WithSecurity("<YOUR_BEARER_TOKEN_HERE>"),
    )

    res, err := s.Seeds.CreateSeed(ctx, "79809a54-ce65-490e-9c9c-0362c7b3a4f8", components.AssetRefInput{})
    if err != nil {
        log.Fatal(err)
    }
    if res.Seed != nil {
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
| `xOrganizationID`                                                    | `*string`                                                            | :heavy_minus_sign:                                                   | Censys organization ID                                               |
| `opts`                                                               | [][operations.Option](../../models/operations/option.md)             | :heavy_minus_sign:                                                   | The options for this request.                                        |

### Response

**[*operations.CreateSeedResponse](../../models/operations/createseedresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |

## DeleteSeed

Remove a seed from an asset graph. The removal takes effect during the next execution of the graph.

### Example Usage

<!-- UsageSnippet language="go" operationID="delete-seed" method="delete" path="/api/v1/asset-graphs/{graph_id}/seeds/{seed_id}" -->
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

    res, err := s.Seeds.DeleteSeed(ctx, "58855951-f444-48b8-821d-4dce444208cb", "<id>")
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
| `seedID`                                                 | `string`                                                 | :heavy_check_mark:                                       | Seed identifier                                          |
| `xOrganizationID`                                        | `*string`                                                | :heavy_minus_sign:                                       | Censys organization ID                                   |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.DeleteSeedResponse](../../models/operations/deleteseedresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |