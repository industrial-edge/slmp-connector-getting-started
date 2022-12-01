# Usage

- [Usage](#usage)
  - [Read metadata](#read-metadata)
  - [Write data](#write-data)
  - [Read data](#read-data)
  - [Use Data Service](#use-data-service)
  
Via the IE Flow Creator, we can write and read the SLMP data.

The used flow can be downloaded [here](/src/flow.json) and imported into the IE Flow Creator, that is running on the same IED as the SLMP Connector.

## Read metadata

To print out the SLMP Connector metadata, follow these steps:

- create a mqtt in node
- set the server to 'ie-databus' with port 1883 and corresponding user name/password ('edge'/'edge')
- set the topic to `ie/m/j/simatic/v1/slmp1/dp`
- create a debug node and connecto to the mqtt in node
- deploy the flow and watch the debug window

![metadata_flow](/docs/graphics/Metadata_Flow.png)

![metadata](/docs/graphics/Metadata.png)

Now you can see the configured datapoints according to SLMP Configurator settings:

- ***Tag_Word*** with unique id 102
- ***Tag_Bool*** with unique id 103

## Write data

To write some data on the SLMP tags, you must fetch the tag ID from metadata payload based on the tag name. Please follow these steps:

- for the ***Tag_Word*** tag, create an inject node with this JSON payload: `{ "vals": [ { "id": "102", "val": "111" } ] }` ***TODO*** ?? raus ??
- for the ***Tag_Bool*** tag, create an inject node with this JSON payload: `{ "vals": [ { "id": "103", "val": "true" } ] }` ***TODO***
- create a mqtt out node
- set the server to 'ie-databus' with port 1883 and corresponding user name/password ('edge'/'edge')
- set the topic to `ie/d/j/simatic/v1/slmp1/dp/w/FX5`
- connect all inject nodes to the mqtt out node
- deploy the flow
- click the single inject buttons, to write the values

![write_data_flow](/docs/graphics/Write_Data_Flow.png)

## Read data

To print out the transfered SLMP Connector data, you must fetch the tag ID from metadata payload based on the tag name. Please follow these steps:

- create a mqtt in node
- set the server to 'ie-databus' with port 1883 and corresponding user name/password ('edge'/'edge')
- set the topic to `ie/d/j/simatic/v1/slmp1/dp/r/#`
- create a debug node and connecto to the mqtt in node
- deploy the flow
- as soon as the value for a configured tag changes, you can see it in the debug window

![read_data_flow](/docs/graphics/Read_Data_Flow.png)

Output for tag ***Tag_Word*** with ID 102:

![read_bool](/docs/graphics/Read_1.png)

Output for tag ***Tag_Bool*** with ID 103:

![read_int](/docs/graphics/Read_2.png)

## Use Data Service

The app Data Service collects the data out of different connectors and stores it for a defined time period. This is a prerequisite for other apps like Performance Insight.

To activate the data transfer from the SLMP Connector, proceed as following:

- open the IED web interface
- open the app Data Service
- go to tab 'Connectors' and select 'SLMP Connector'
- select the edit button and enter the user name and the password for the Databus user ('edge'/'edge')
- activate the adapter and save

![DataServiceAdapter](/docs/graphics/DataService_Adapter.png)

- go to tab 'Assets & Connectivity' and add the variables, that were configured within the SLMP Connector

![DataServiceAdapter](/docs/graphics/DataService_Add.png)

- data is now collected by the Data Service and can be used by further apps
