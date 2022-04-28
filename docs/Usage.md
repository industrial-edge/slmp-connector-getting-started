# Installation

- [Usage](#usage)
  - [Read metadata](#read-metadata)
  - [Write data](#write-data)
  - [Read data](#read-data)

Via the IE Flow Creator, we can write and read the SLMP data.

The used flow can be downloaded [here](/src/flow.json) and imported into the IE Flow Creator, that is running on the same IED as the SLMP connector.

## Read metadata

To print out the SLMP Connector metadata, follow these steps:

- create a mqtt out node
- set the server to "ie-databus" with port 1883 and corresponding user name / password ("edge"/"edge")
- set the topic to `ie/m/j/simatic/v1/slmp1/dp`
- create a debug node and connecto to the mqtt out node
- deploy the flow and watch the debug window

![metadata_flow](/docs/graphics/Metadata_Flow.png)

![metadata](/docs/graphics/Metadata.png)

## Write data

xxx

## Read data
