# RiskSeverity

## Example Usage

```go
import (
	"github.com/censys/censys-asset-graph-sdk-go/models/components"
)

value := components.RiskSeverityUnknown

// Open enum: custom values can be created with a direct type cast
custom := components.RiskSeverity("custom_value")
```


## Values

| Name                   | Value                  |
| ---------------------- | ---------------------- |
| `RiskSeverityUnknown`  |                        |
| `RiskSeverityLow`      | low                    |
| `RiskSeverityMedium`   | medium                 |
| `RiskSeverityHigh`     | high                   |
| `RiskSeverityCritical` | critical               |