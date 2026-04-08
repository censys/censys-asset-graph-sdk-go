# github.com/censys/censys-asset-graph-sdk-go

[![Built by Speakeasy](https://img.shields.io/badge/Built_by-SPEAKEASY-374151?style=for-the-badge&labelColor=f3f4f6)](https://www.speakeasy.com/?utm_source=censysassetgraphsdkgo&utm_campaign=go)
[![License: MIT](https://img.shields.io/badge/LICENSE_//_MIT-3b5bdb?style=for-the-badge&labelColor=eff6ff)](https://opensource.org/licenses/MIT)

<!-- No Summary [summary] -->

<!-- No Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

To add the SDK as a dependency to your project:
```bash
go get github.com/censys/censys-asset-graph-sdk-go
```
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```go
package main

import (
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
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name                  | Type | Scheme      |
| --------------------- | ---- | ----------- |
| `PersonalAccessToken` | http | HTTP Bearer |

You can configure it using the `WithSecurity` option when initializing the SDK client instance. For example:
```go
package main

import (
	"context"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"log"
)

func main() {
	ctx := context.Background()

	s := censysassetgraphsdkgo.New(
		censysassetgraphsdkgo.WithSecurity("<YOUR_BEARER_TOKEN_HERE>"),
		censysassetgraphsdkgo.WithXOrganizationID("<id>"),
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
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [AssetGraphs](docs/sdks/assetgraphs/README.md)

* [ListAssetGraphs](docs/sdks/assetgraphs/README.md#listassetgraphs) - List asset graphs
* [CreateAssetGraph](docs/sdks/assetgraphs/README.md#createassetgraph) - Create an asset graph
* [DeleteAssetGraph](docs/sdks/assetgraphs/README.md#deleteassetgraph) - Delete an asset graph
* [GetAssetGraph](docs/sdks/assetgraphs/README.md#getassetgraph) - Get an asset graph

### [Assets](docs/sdks/assets/README.md)

* [ListAssets](docs/sdks/assets/README.md#listassets) - List assets
* [GetAsset](docs/sdks/assets/README.md#getasset) - Get an asset

### [ExcludedAssets](docs/sdks/excludedassets/README.md)

* [ListExcludedAssets](docs/sdks/excludedassets/README.md#listexcludedassets) - List excluded assets
* [CreateExcludedAsset](docs/sdks/excludedassets/README.md#createexcludedasset) - Create an excluded asset
* [DeleteExcludedAsset](docs/sdks/excludedassets/README.md#deleteexcludedasset) - Delete an excluded asset

### [GraphExecutions](docs/sdks/graphexecutions/README.md)

* [ListGraphExecutions](docs/sdks/graphexecutions/README.md#listgraphexecutions) - List graph executions
* [CreateGraphExecution](docs/sdks/graphexecutions/README.md#creategraphexecution) - Create a graph execution
* [GetGraphExecution](docs/sdks/graphexecutions/README.md#getgraphexecution) - Get a graph execution

### [Risks](docs/sdks/risks/README.md)

* [GetRiskMetadata](docs/sdks/risks/README.md#getriskmetadata) - Get static risk metadata

### [Seeds](docs/sdks/seeds/README.md)

* [ListSeeds](docs/sdks/seeds/README.md#listseeds) - List seeds
* [CreateSeed](docs/sdks/seeds/README.md#createseed) - Create a seed
* [DeleteSeed](docs/sdks/seeds/README.md#deleteseed) - Delete a seed

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `retry.Config` object to the call by using the `WithRetries` option:
```go
package main

import (
	"context"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"github.com/censys/censys-asset-graph-sdk-go/retry"
	"log"
	"models/operations"
)

func main() {
	ctx := context.Background()

	s := censysassetgraphsdkgo.New(
		censysassetgraphsdkgo.WithXOrganizationID("<id>"),
		censysassetgraphsdkgo.WithSecurity("<YOUR_BEARER_TOKEN_HERE>"),
	)

	res, err := s.AssetGraphs.ListAssetGraphs(ctx, nil, nil, operations.WithRetries(
		retry.Config{
			Strategy: "backoff",
			Backoff: &retry.BackoffStrategy{
				InitialInterval: 1,
				MaxInterval:     50,
				Exponent:        1.1,
				MaxElapsedTime:  100,
			},
			RetryConnectionErrors: false,
		}))
	if err != nil {
		log.Fatal(err)
	}
	if res.ListAssetGraphsOutputBody != nil {
		// handle response
	}
}

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `WithRetryConfig` option at SDK initialization:
```go
package main

import (
	"context"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"github.com/censys/censys-asset-graph-sdk-go/retry"
	"log"
)

func main() {
	ctx := context.Background()

	s := censysassetgraphsdkgo.New(
		censysassetgraphsdkgo.WithRetryConfig(
			retry.Config{
				Strategy: "backoff",
				Backoff: &retry.BackoffStrategy{
					InitialInterval: 1,
					MaxInterval:     50,
					Exponent:        1.1,
					MaxElapsedTime:  100,
				},
				RetryConnectionErrors: false,
			}),
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
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or an error, they will never return both.

By Default, an API error will return `apierrors.SDKError`. When custom error responses are specified for an operation, the SDK may also return their associated error. You can refer to respective *Errors* tables in SDK docs for more details on possible error types for each operation.

For example, the `ListAssetGraphs` function may return the following errors:

| Error Type         | Status Code | Content Type |
| ------------------ | ----------- | ------------ |
| apierrors.SDKError | 4XX, 5XX    | \*/\*        |

### Example

```go
package main

import (
	"context"
	"errors"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"github.com/censys/censys-asset-graph-sdk-go/models/apierrors"
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

		var e *apierrors.SDKError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}
	}
}

```
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Override Server URL Per-Client

The default server can be overridden globally using the `WithServerURL(serverURL string)` option when initializing the SDK client instance. For example:
```go
package main

import (
	"context"
	censysassetgraphsdkgo "github.com/censys/censys-asset-graph-sdk-go"
	"log"
)

func main() {
	ctx := context.Background()

	s := censysassetgraphsdkgo.New(
		censysassetgraphsdkgo.WithServerURL("https://graph.data.censys.io"),
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
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Go SDK makes API calls that wrap an internal HTTP client. The requirements for the HTTP client are very simple. It must match this interface:

```go
type HTTPClient interface {
	Do(req *http.Request) (*http.Response, error)
}
```

The built-in `net/http` client satisfies this interface and a default client based on the built-in is provided by default. To replace this default with a client of your own, you can implement this interface yourself or provide your own client configured as desired. Here's a simple example, which adds a client with a 30 second timeout.

```go
import (
	"net/http"
	"time"

	"github.com/censys/censys-asset-graph-sdk-go"
)

var (
	httpClient = &http.Client{Timeout: 30 * time.Second}
	sdkClient  = censysassetgraphsdkgo.New(censysassetgraphsdkgo.WithClient(httpClient))
)
```

This can be a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration.
<!-- End Custom HTTP Client [http-client] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=censysassetgraphsdkgo&utm_campaign=go)
