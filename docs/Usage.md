# Installation

- [Usage](#usage)
  - [Read metadata](#read-metadata)
  - [Read data](#read-data)
  - [Write data](#write-data)

Via the IE Flow Creator, we can write and read the SLMP data.

The used flow can be downloaded [here](/src/flow.json) and imported into the IE Flow Creator, that is running on the same IED as the SLMP connector.

## Read metadata

To print out the SLMP Connector metadata, follow these steps:

- create a mqtt in node
- set the server to "ie-databus" with port 1883 and corresponding user name / password ("edge"/"edge")
- set the topic to `ie/m/j/simatic/v1/slmp1/dp`
- create a debug node and connecto to the mqtt in node
- deploy the flow and watch the debug window

![metadata_flow](/docs/graphics/Metadata_Flow.png)

![metadata](/docs/graphics/Metadata.png)

## Read data

## Write data

To write some data on the SLMP tags, follow these steps:

- for the BOOL example, create an inject node with this JSON payload

`{ "vals": [ { "id": <tag id>, "val": "true" } ] }`

- for the INT example, create an inject node with this JSON payload

`{ "vals": [ { "id": <tag id>, "val": "111" } ] }`

- for the REAL example, create an inject node with this JSON payload

`{ "vals": [ { "id": <tag id>, "val": "555.55" } ] }`

- create a mqtt out node
- set the server to "ie-databus" with port 1883 and corresponding user name / password ("edge"/"edge")
- set the topic to `ie/d/j/simatic/v1/slmp1/dp/w/FX5`
- connect all inject nodes to the mqtt out node

![json_bool](/docs/graphics/JSON_Bool.png)

![json_bool](/docs/graphics/JSON_Int.png)

![json_bool](/docs/graphics/JSON_Real.png)
