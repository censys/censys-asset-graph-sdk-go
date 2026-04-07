# RootStoreType

The certificate's type. Options include root, intermediate, or leaf.

## Example Usage

```go
import (
	"github.com/censys/censys-asset-graph-sdk-go/models/components"
)

value := components.RootStoreTypeUnknown

// Open enum: custom values can be created with a direct type cast
custom := components.RootStoreType("custom_value")
```


## Values

| Name                        | Value                       |
| --------------------------- | --------------------------- |
| `RootStoreTypeUnknown`      |                             |
| `RootStoreTypeRoot`         | root                        |
| `RootStoreTypeIntermediate` | intermediate                |
| `RootStoreTypeLeaf`         | leaf                        |