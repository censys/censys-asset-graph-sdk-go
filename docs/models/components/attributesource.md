# AttributeSource

## Example Usage

```go
import (
	"github.com/censys/censys-asset-graph-sdk-go/models/components"
)

value := components.AttributeSourceUnknown

// Open enum: custom values can be created with a direct type cast
custom := components.AttributeSource("custom_value")
```


## Values

| Name                               | Value                              |
| ---------------------------------- | ---------------------------------- |
| `AttributeSourceUnknown`           |                                    |
| `AttributeSourceCensys`            | censys                             |
| `AttributeSourceRecog`             | recog                              |
| `AttributeSourceWappalyzer`        | wappalyzer                         |
| `AttributeSourceThirdParty`        | third_party                        |
| `AttributeSourceHTMLMetaExtractor` | html_meta_extractor                |