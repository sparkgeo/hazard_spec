# OS-C Hazard Core Specification

This specification describes the core data and metadata properties for both at the Record and Feature level.
The atomic unit is a OGC Record as described here: [OGC Records]([https://docs.ogc.org/DRAFTS/20-004.html#clause-record-core) and [schema](https://github.com/opengeospatial/ogcapi-records/blob/master/core/openapi/schemas/recordJSON.yaml).

- A Record referes to a specific hazard that encompasses one or more hazard indicators.
- A Feature is a single field geometry with additional properties.

A hazard can be of three kinds:

- Acute
- Chronic
- Unknown

Hazards exist over a space and time, so geojson is used as a foundational building blog for this specification. By default, we have hazards existing any where, anytime. In accordance with best practices from other specificaitons, 