# Installation

- [Installation](#installation)
  - [Configure IE Databus](#configure-ie-databus)
  - [Install SLMP Configurator and Connector](#install-slmp-configurator-and-connector)
  - [Configure SLMP Connector](#configure-slmp-connector)

## Configure IE Databus

The SLMP Connector sends the transfered data to the Databus on the Industrial Edge Device (IED). From there the data can be used for further processing.

You need to create a user and one or more topics in the Databus configuration, which cover the SLMP data:

- ***ie/m/j/simatic/v1/slmp1/dp*** for SLMP metadata
- ***ie/d/j/simatic/v1/slmp1/dp*** for SLMP data

Therefore follow these steps:

- open the Data Connections in the Industrial Edge Management (IEM)
- open the configuration for the Databus
- add a new user ("edge"/"edge") and the topic "ie/#", set permission to "Publish and Subscribe"
- deploy the configuration

![databus](/docs/graphics/Databus.png)

## Install SLMP Configurator and Connector

Make sure the SLMP Configurator and the SLMP Connector are available in your IEM catalog. Proceed the following steps to install the apps on your IED:

- open the catalog in the IEM
- select the SLMP Configurator
- click 'Install'
- in the tab 'Configurations' click 'Next'
- in the tab 'Devices' choose your IED
- click 'Install Now'
- if needed, allow the installation warnings

Repeat the same steps for the SLMP Connector.

![installation1](/docs/graphics/Installation1.png)

![installation2](/docs/graphics/Installation2.png)

## Configure SLMP Connector

The SLMP Configurator allows you to add field devices to the IED and to create data points. Both SLMP apps need to be installed on your IED. Login to the IED and open the SLMP Configurator UI.

To add a new connection to a Mitsubishi PLC, follow these steps:

- click 'Add Data Source' to configure a new connection
- in 'Data Source Type' field choose 'SLMP'
- in 'Name' field enter a name for the data source
- in 'IP Address' field enter the IP address of the source PLC
- in 'Port' field enter the port number as configured for the PLC module (from 1-65534)
- in 'CPU Type' field choose the proper type (Mitsubishi iQR series / Mitsubishi iQF series)
- click 'Add'

![configuration1](/docs/graphics/Configuration1.png)

To add one or more data points, follow these steps:

- click on the '+' icon at the right site of the data source row
- in 'Name' field enter a name for the tag
- in 'Address' field enter the address of the data point in the PLC (format `<operand> <address>`)
- in 'Data Type' field choose the proper data type
- in 'Acquisition Cycle' field choose the cycle time with which the data is sent to the Databus (100 ms - 10 s)
- in 'Acquitition Mode' field choose 'CyclicOnChange'
- in 'Access Mode' field choose 'Read and Write'
- click 'Add Tags'

![configuration2](/docs/graphics/Configuration2.png)

Here is an overview of permitted data types for the Mitsubishi iQR/iQF PLCs:

| Data type   | Operand | Length |
| ----------- | ----------- |----------- |
| Bool        | D, M, X, Y, F, B, SB, W, SW, SD, SM, CC, CS, TS, TC, LCS, LCC, STS, STC, LTS, LTC, LSTS, LSTC, L | 1 Bit            |
| Int         | D, CN, W, TN, STN, SW     | 2 Byte            |
| Word        | D, TN, CN, SW, STN, W, SD | 2 Byte            |
| DWord       | D, LCN, W, SW, LTN, LSTN  | 4 Byte            |
| DInt        | D, LCN, W, SW, LTN, LSTN  | 4 Byte            |
| Real        | D, W, SW                  | 4 Byte            |
| LReal       | D, W, SW                  | 8 Byte            |
| String      | D, W, SW                  | 1 - 80 characters |

To configure the connection to the Databus, follow these steps:

- click on the settings icon on the top right site
- in 'UserName' field enter the user name according to the Databus configuration
- in 'Password' field enter the password according to the Databus configuration
- click 'Save'

![configuration3](/docs/graphics/Configuration3.png)

Finally click the **'Deploy'** button to save the configuration for the SLMP Connector. Then click the **'Start Project'** button to start the project.

Now data can be transferred via the SLMP connection. Please find more information in the  [Usage](/docs/Usage.md) documentation.
