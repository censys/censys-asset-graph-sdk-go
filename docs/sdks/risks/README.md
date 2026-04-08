# Risks

## Overview

### Available Operations

* [GetRiskMetadata](#getriskmetadata) - Get static risk metadata

## GetRiskMetadata

Retrieve additional metadata for a risk, such as long-form descriptions and references. Risk IDs can be found on asset data in vulnerabilities, exposures, misconfigurations, and threats.

### Example Usage

<!-- UsageSnippet language="go" operationID="get-risk-metadata" method="get" path="/api/v1/risks/{risk_id}" -->
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

    res, err := s.Risks.GetRiskMetadata(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.RiskMetadata != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                             | Type                                                                                                                  | Required                                                                                                              | Description                                                                                                           |
| --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                 | [context.Context](https://pkg.go.dev/context#Context)                                                                 | :heavy_check_mark:                                                                                                    | The context to use for the request.                                                                                   |
| `riskID`                                                                                                              | `string`                                                                                                              | :heavy_check_mark:                                                                                                    | A Censys risk ID (e.g. CENSYS-2025-1), threat ID (e.g. THREAT-1) or an external risk identifier (e.g. CVE-2025-00001) |
| `xOrganizationID`                                                                                                     | `*string`                                                                                                             | :heavy_minus_sign:                                                                                                    | Censys organization ID                                                                                                |
| `opts`                                                                                                                | [][operations.Option](../../models/operations/option.md)                                                              | :heavy_minus_sign:                                                                                                    | The options for this request.                                                                                         |

### Response

**[*operations.GetRiskMetadataResponse](../../models/operations/getriskmetadataresponse.md), error**

### Errors

| Error Type         | Status Code        | Content Type       |
| ------------------ | ------------------ | ------------------ |
| apierrors.SDKError | 4XX, 5XX           | \*/\*              |