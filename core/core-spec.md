# Hazard Core Specification

This document explains the structure and content of a core hazard object. Hazard objects represent a logical grouping of indicators and models. These items can and should be linked in one-to-many and many-to-many relationships.

A hazard can be of three kinds:

- Acute
- Chronic
- Unknown

Each hazard can be measured using two types of models:

- Event-based models
- Return-period models

We will define models for the different model types to build this core specification.

A JSON object with the following required fields is a valid hazard object.

- [Examples](../examples)
  - See an example for a [base hazard](../examples/hazard-example.json).
- [Vulnerability Model](./schema/vulnerability_model.json)
- [Core Schema](./schema/schema.json)
- [Hazard Type](./schema/hazard_type.json)

## Hazard Type Schema Specification

This document describes the schema definitions and relationships for representing metadata about various hazards.
## Schema Files

### [`vulnerability_model.json`](./schema/vulnerability_model.json)

The `vulnerability_model.json` file defines the structure of the `vulnerability_model` property, which can represent event-based or return-period-based details.

#### Event-based Details

| Field             | Type    | Description                          | Required |
|-------------------|---------|--------------------------------------|----------|
| `event_based`     | boolean | Indicates if the hazard is event-based | Yes      |
| `event_description` | string  | Description of the event              | Yes      |

#### Return-period-based Details

| Field                     | Type   | Description                           | Required |
|---------------------------|--------|---------------------------------------|----------|
| `return_period_based`     | boolean| Indicates if the hazard is return-period-based | Yes      |
| `return_period_description` | string | Description of the return period      | Yes      |

### 2. [`schema.json`](./schema.json)

The `schema.json` file defines the general structure for representing hazard metadata. It includes properties such as `hazard_version`, `id`, `hazard_kind`, `name`, `description`, `links`, and references the `vulnerability_model` property from `vulnerability_model.json`.

#### Properties

| Field          | Type   | Description                                   | Required |
|----------------|--------|-----------------------------------------------|----------|
| `hazard_version` | string | The version of the hazard schema              | Yes      |
| `id`             | string | The identifier for the hazard                 | Yes      |
| `hazard_kind`    | string | The kind of hazard. One of `chronic`, `acute`, or `unknown`                           | Yes      |
| `name`           | string | The name of the hazard                        | Yes      |
| `description`    | string | A description of the hazard                   | Yes      |
| links          | array of [`link objects`](#links-object)      | Links to hazard relations                     | No       |
| vulnerability_model        | object |One of [event-based](/#Event-based-Details) or [return-period-based](/#return-period-Details) | No       |

#### Links Object

| Field | Type   | Description                   | Required |
|-------|--------|-------------------------------|----------|
| `href`  | string | Link reference in IRI format  | Yes      |
| `rel`   | string | Link relation type            | Yes      |
| `type`  | string | Link type                     | No       |
| `title` | string | Link title                    | No       |

### 3. [`hazard_type.json`](./hazard_type.json)

The `hazard_type.json` file extends `schema.json` and restricts the `hazard_type` to a specific list of predefined hazards. From this list, indicators are grouped.

#### Properties

| Field       | Type   | Description           | Required |
|-------------|--------|-----------------------|----------|
| `hazard_type` | string | The type of hazard. One of [Allowed Hazard Types](#allowed-hazard-types)    | Yes      |

#### Allowed Hazard Types

| Hazard Type          |
|----------------------|
| ChronicHeat          |
| AirTemperature       |
| ChronicWind          |
| CoastalInundation    |
| CombinedInundation   |
| Drought              |
| Fire                 |
| Hail                 |
| Hazard               |
| Inundation           |
| PluvialInundation    |
| Precipitation        |
| RiverineInundation   |
| WaterRisk            |
| WaterTemperature     |
| Wind                 |
