# github.com/censys/censys-asset-graph-sdk-go

[![Built by Speakeasy](https://img.shields.io/badge/Built_by-SPEAKEASY-374151?style=for-the-badge&labelColor=f3f4f6)](https://www.speakeasy.com/?utm_source=censysassetgraphsdkgo&utm_campaign=go)
[![License: MIT](https://img.shields.io/badge/LICENSE_//_MIT-3b5bdb?style=for-the-badge&labelColor=eff6ff)](https://opensource.org/licenses/MIT)


<!-- Start Summary [summary] -->
## Summary

Asset Graph API: # Asset Graph API

The Asset Graph API provides comprehensive visibility into your Internet-facing assets. Use this API to build and manage attack surfaces by creating asset graphs, configuring seeds and exclusions, running discovery executions, and retrieving discovered assets and risk metadata.

### Authentication

All requests must include a valid Censys personal access token (PAT) in the `Authorization` header:

```
Authorization: Bearer <your-api-token>
```

An `X-Organization-ID` header must also be present on every request. This identifies the Censys organization that owns the resources being accessed.

```
X-Organization-ID: <your-organization-id>
```

### Core Concepts

- **Asset Graph**: The parent resource representing an attack surface. Each asset graph contains seeds, excluded assets, and executions.
- **Seeds**: Persistent starting points used to discover additional assets. Supported types include IP addresses, domains, CIDRs, ASNs, certificates, and web properties.
- **Excluded Assets**: Assets explicitly excluded from the graph. Excluded assets will not appear in execution results and will not be used to discover additional assets.
- **Executions**: A discovery process that uses the graph's configured seeds and excluded assets to generate a complete snapshot of the attack surface. Censys periodically runs executions in the background, or they can be triggered on-demand.
- **Assets**: Internet-facing resources discovered during an execution, including hosts, domains, certificates, and web properties. Each asset includes discovery paths showing how it was found from your seeds.
- **Risks**: Vulnerabilities, exposures, misconfigurations, and threats identified on discovered assets.

### Getting Started

1. **Create an asset graph** to represent your attack surface.
2. **Add seeds** — the known assets that Censys will use as starting points for discovery.
3. **Optionally add excluded assets** to omit specific assets from results.
4. **Create an execution** to trigger the discovery process, or wait for Censys to run one automatically.
5. **List assets** from a completed execution to view your discovered attack surface.
6. **Look up risk metadata** for any risk IDs found on your assets.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [censysassetgraphsdkgo](#censysassetgraphsdkgo)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

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

	s := censysassetgraphsdkgo.New()

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

	s := censysassetgraphsdkgo.New()

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

	s := censysassetgraphsdkgo.New()

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
