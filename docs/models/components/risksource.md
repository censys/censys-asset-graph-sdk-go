# RiskSource

## Example Usage

```go
import (
	"github.com/censys/censys-asset-graph-sdk-go/models/components"
)

value := components.RiskSourceUnknown

// Open enum: custom values can be created with a direct type cast
custom := components.RiskSource("custom_value")
```


## Values

| Name                          | Value                         |
| ----------------------------- | ----------------------------- |
| `RiskSourceUnknown`           |                               |
| `RiskSourceCensys`            | censys                        |
| `RiskSourceRecog`             | recog                         |
| `RiskSourceWappalyzer`        | wappalyzer                    |
| `RiskSourceThirdParty`        | third_party                   |
| `RiskSourceHTMLMetaExtractor` | html_meta_extractor           |