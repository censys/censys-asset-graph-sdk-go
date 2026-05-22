# StatusEnum

Lifecycle status of the asset graph

## Example Usage

```go
import (
	"github.com/censys/censys-asset-graph-sdk-go/models/components"
)

value := components.StatusEnumActive

// Open enum: custom values can be created with a direct type cast
custom := components.StatusEnum("custom_value")
```


## Values

| Name                 | Value                |
| -------------------- | -------------------- |
| `StatusEnumActive`   | ACTIVE               |
| `StatusEnumDeleting` | DELETING             |