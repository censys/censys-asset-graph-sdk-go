# CertificateRevocationRevocationInfoReason

An enumerated value indicating the issuer-supplied reason for the revocation.

## Example Usage

```go
import (
	"github.com/censys/censys-asset-graph-sdk-go/models/components"
)

value := components.CertificateRevocationRevocationInfoReasonUnknown

// Open enum: custom values can be created with a direct type cast
custom := components.CertificateRevocationRevocationInfoReason("custom_value")
```


## Values

| Name                                                            | Value                                                           |
| --------------------------------------------------------------- | --------------------------------------------------------------- |
| `CertificateRevocationRevocationInfoReasonUnknown`              |                                                                 |
| `CertificateRevocationRevocationInfoReasonUnspecified`          | unspecified                                                     |
| `CertificateRevocationRevocationInfoReasonKeyCompromise`        | key_compromise                                                  |
| `CertificateRevocationRevocationInfoReasonCaCompromise`         | ca_compromise                                                   |
| `CertificateRevocationRevocationInfoReasonAffiliationChanged`   | affiliation_changed                                             |
| `CertificateRevocationRevocationInfoReasonSuperseded`           | superseded                                                      |
| `CertificateRevocationRevocationInfoReasonCessationOfOperation` | cessation_of_operation                                          |
| `CertificateRevocationRevocationInfoReasonCertificateHold`      | certificate_hold                                                |
| `CertificateRevocationRevocationInfoReasonRemoveFromCrl`        | remove_from_crl                                                 |
| `CertificateRevocationRevocationInfoReasonPrivilegeWithdrawn`   | privilege_withdrawn                                             |
| `CertificateRevocationRevocationInfoReasonAaCompromise`         | aa_compromise                                                   |