# Usage

- [Usage](#usage)
  - [Read metadata](#read-metadata)
  - [Write data](#write-data)
  - [Read data](#read-data)
  
Via the IE Flow Creator, we can write and read the SLMP data.

The used flow can be downloaded [here](/src/flow.json) and imported into the IE Flow Creator, that is running on the same IED as the SLMP connector.

## Read metadata

To print out the SLMP Connector metadata, follow these steps:

- create a mqtt in node
- set the server to "ie-databus" with port 1883 and corresponding user name/password ("edge"/"edge")
- set the topic to `ie/m/j/simatic/v1/slmp1/dp`
- create a debug node and connecto to the mqtt in node
- deploy the flow and watch the debug window

![metadata_flow](/docs/graphics/Metadata_Flow.png)

![metadata](/docs/graphics/Metadata.png)

Now you can see three configured datapoints according to SLMP Configurator settings:

- ***Bool*** with unique id 102
- ***Int*** with unique id 103
- ***Real*** with unique id 104

## Write data

To write some data on the SLMP tags, you must fetch the tag ID from metadata payload based on the tag name. Please follow these steps:

- for the ***BOOL*** tag, create an inject node with this JSON payload: `{ "vals": [ { "id": "102", "val": "true" } ] }`
- for the ***Int*** tag, create an inject node with this JSON payload: `{ "vals": [ { "id": "103", "val": "111" } ] }`
- for the ***Real*** tag, create an inject node with this JSON payload: `{ "vals": [ { "id": "104", "val": "555.55" } ] }`
- create a mqtt out node
- set the server to "ie-databus" with port 1883 and corresponding user name/password ("edge"/"edge")
- set the topic to `ie/d/j/simatic/v1/slmp1/dp/w/FX5`
- connect all inject nodes to the mqtt out node
- deploy the flow
- click the single inject buttons, to write the values

![write_data_flow](/docs/graphics/Write_Data_Flow.png)

## Read data

To print out the transfered SLMP Connector data, you must fetch the tag ID from metadata payload based on the tag name. Please follow these steps:

- create a mqtt in node
- set the server to "ie-databus" with port 1883 and corresponding user name/password ("edge"/"edge")
- set the topic to `ie/d/j/simatic/v1/slmp1/dp/r/#`
- create a debug node and connecto to the mqtt in node
- deploy the flow
- as soon as the value for a configured tag changes, you can see it in the debug window

![read_data_flow](/docs/graphics/Read_Data_Flow.png)

Output for tag ***Bool*** with ID 102:

![read_bool](/docs/graphics/Read_Bool.png)

Output for tag ***Int*** with ID 103:

![read_int](/docs/graphics/Read_Int.png)

Output for tag ***Real*** with ID 104:

![read_real](/docs/graphics/Read_Real.png)
