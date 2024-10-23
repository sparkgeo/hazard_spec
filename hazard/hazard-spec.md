# Chronic Heat Hazard Indicator Schema

## Overview

The `hazard_indicator.json` file defines the schema for hazard indicators and specifically Chronic Heat.

## Schema Details

This schema adheres to the JSON Schema Draft-07 standard and includes the following key properties:

- **$schema**: The JSON Schema version.
- **$id**: The identifier for this schema.
- **title**: The title of the schema.
- **type**: The type of the schema object.
- **required**: An array of required properties.
- **description**: A description of the schema.
- **properties**: An object defining the properties of the schema.

### Required Fields

The following fields are required in the `hazard_indicator.json` schema:

- `hazard_version`: The version of the hazard schema.
- `id`: The identifier for the hazard.
- `hazard_kind`: The kind of hazard. One of `chronic`, `acute`, or `unknown`.
- `name`: The name of the hazard.
- `description`: A description of the hazard.

### Properties

- **indicator**: Represents the hazard indicator. It includes a `title` and a `const` value. The `indicator` property can have one of the following values:
  - "Mean degree days above 32°C"
  - "Days per year above 35°C (Jupiter)"
  - "Mean work loss, low intensity"

## Example

Here is an example of a JSON document that conforms to the `hazard_indicator.json` schema:

```json
{
    "$schema": "http://json-schema.org/draft-07/schema#",
    "$id": "./schema.json",
    "title": "Chronic Heat Hazard Indicator Schema",
    "type": "object",
    "required": ["hazard_version", "id", "hazard_kind", "name", "description"],
    "description": "This object represents the metadata for Chronic Heat hazards indicators.",
    "properties": {
        "indicator": {
            "title": "Hazard Indicator",
            "type": "string",
            "oneOf": [
                {
                    "title": "Mean degree days above 32\u00b0C",
                    "const": "chronic_heat_osc_v2_mean_degree_days_v2_above_32c"
                },
                {
                    "title": "Days per year above 35\u00b0C (Jupiter)",
                    "const": "chronic_heat_jupiter_v1_days_above_35c"
                },
                {
                    "title": "Mean work loss, low intensity",
                    "const": "chronic_heat_osc_v2_mean_work_loss_low"
                }
            ]
        }
    }
}