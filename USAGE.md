<!-- Start SDK Example Usage [usage] -->
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