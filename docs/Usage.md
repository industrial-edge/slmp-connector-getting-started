# Usage

- [Usage](#usage)
  - [Read metadata](#read-metadata)
  - [Write data](#write-data)
  - [Read data](#read-data)
  - [Use IIH Essentials](#use-IIH-Essentials)
  
Via the Flow Creator, we can write and read the SLMP data.

The used flow can be downloaded [here](/src/flow.json) and imported into the Flow Creator, that is running on the same IED as the SLMP Connector.

## Read metadata

To print out the SLMP Connector metadata, follow these steps:

- create a mqtt in node
- set the server to 'ie-databus' with port 1883 and corresponding user name/password ('edge'/'edge')
- set the topic to `ie/m/j/simatic/v1/slmp1/dp`
- create a debug node and connecto to the mqtt in node
- deploy the flow and watch the debug window

![Metadata_Flow](/docs/graphics/Metadata_Flow.png)

![SLMPreaddata](/docs/graphics/SLMPmetadatnew.PNG)

Now you can see the configured datapoints according to SLMP Configurator settings:

- ***Tag1*** with unique id 102
- ***Tag2*** with unique id 103
- ***Tag3*** with unique id 104
  
## Write data

To write some data on the SLMP tags, you must fetch the tag ID from metadata payload based on the tag name. Please follow these steps:

- for the ***Tag3*** tag, create an inject node to write the value 4444 with this JSON payload: `{"vals":[{"id":"104","val":"4444"}]}`
- for the ***Tag3*** tag, create another inject node to write the value 9999 with this JSON payload: `{"vals":[{"id":"104","val":"9999"}]}`
- create a mqtt out node
- set the server to 'ie-databus' with port 1883 and corresponding user name/password ('edge'/'edge')
- set the topic to `ie/d/j/simatic/v1/slmp1/dp/w/FX5`
- connect the inject nodes to the mqtt out node
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

The tag ***Tag2*** with ID 103 is filled automatically by the PLC program (counter) and the output is printed continuously:

![SLMPdataauto](/docs/graphics/SLMPdataauto.PNG)

If some data is written on tag ***Tag3*** with ID 104, the output looks like the following:

![SLMPdatawrite](/docs/graphics/SLMPdatawrite.PNG)

## Use IIH Essentials 

The app IIH Essentials collects the data out of different connectors and stores it for a defined time period. This is a prerequisite for other apps like Performance Insight.

To activate the data transfer from the SLMP Connector, proceed as following:

- open the IED web interface
- open the app IIH Essentials
- go to tab 'Connectors' and select 'SLMP Connector' 
- select the edit button and activate the connector 
- activate the adapter and save

![DataServiceAdapter](/docs/graphics/DataService_Adapter.png)

- go to tab 'Assets & Connectivity' and add the variables, that were configured within the SLMP Connector

![DataServiceAdapter](/docs/graphics/DataService_Add.png)

- data is now collected by the IIH Essentials and can be used by further apps
