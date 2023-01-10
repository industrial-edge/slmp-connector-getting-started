# Configuration

- [Configuration](#configuration)
  - [Overview](#overview)
  - [Install SLMP Connector](#install-slmp-connector)
  - [Configure IE Databus](#configure-ie-databus)
  - [Configure SLMP via IIH Configurator](#configure-slmp-via-iih-configurator)

## Overview

When working with connectors on Industrial Edge, the **IE Databus** app is required to exchange the data via MQTT. The configuration of the connectors is done via the **IIH Configurator** app. Therefore also the **Registry Service** app is necessary, to find installed connectors on an Industrial Edge Device.

Make sure the following apps are installed and running on the Industrial Edge Device (IED):
- IE Databus
- IIH Configurator
- Registry Service

## Install SLMP Connector

The SLMP Connector app must be available in your IEM catalog. Proceed the following steps to install the app on your IED:

- open the catalog in the IEM
- select the SLMP Connector
- click 'Install'
- in the tab 'Configurations' click 'Next'
- in the tab 'Devices' choose your IED
- click 'Install Now'
- click 'Install' to allow the installation

![app](/docs/graphics/SLMP_App.png)

## Configure IE Databus

The system app Databus is essential to exchange data between a PLC and the IED. The SLMP Connector sends the transfered data to the Databus on the IED. From there the data can be used for further processing.

You need to create a user and one or more topics in the Databus configuration, which cover the SLMP data:

- ***ie/m/j/simatic/v1/slmp1/dp*** for SLMP metadata
- ***ie/d/j/simatic/v1/slmp1/dp*** for SLMP data

Therefore follow these steps:

- open the Industrial Edge Management (IEM)
- go to 'Data Connections' > IE Databus
- select the corresponding IED
- create the topic `ie/#`and a dedicated user with username and password ('edge'/'edge'), set permissions to 'Publish and Subscribe'
- deploy the configuration and wait for the job to be finished successfully

![databus](/docs/graphics/Databus.png)

## Configure SLMP via IIH Configurator

With the IIH Configurator, you can configure several connectors and publish the data to the IE Databus. Therefore, you must enter the Databus credentials within the IIH Configurator:

- open the IED web interface
- open the app IIH Configurator
- go to the tab 'Settings' and select the menu 'Databus credentials'
- enter the databus service name: 'ie-databus:1883'
- in tab 'Data Publisher settings' enter the databus user name and password ('edge'/'edge')
- in tab 'Data Subscriber settings' enter the databus user name and password ('edge'/'edge')
- Save the settings

![IIH_Settings](/docs/graphics/IIH_Settings.png)

As soon as the SLMP Connector is installed and started on the same IED as the IIH Configurator, the connector is visible within the configurator. In this example we want to configure an SLMP connection to a Mitsubishi FX5U (iQF) PLC.

Here is an overview of permitted data types for the Mitsubishi iQR/iQF PLCs:

| Data type   | Operand     | Length     |
| ----------- | ----------- |----------- |
| Bool        | D, M, X, Y, F, B, SB, W, SW, SD, SM, CC, CS, TS, TC, LCS, LCC, STS, STC, LTS, LTC, LSTS, LSTC, L | 1 Bit            |
| Int         | D, CN, W, TN, STN, SW     | 2 Byte            |
| Word        | D, TN, CN, SW, STN, W, SD | 2 Byte            |
| DInt        | D, LCN, W, SW, LTN, LSTN  | 4 Byte            |
| DWord       | D, LCN, W, SW, LTN, LSTN  | 4 Byte            |
| Real        | D, W, SW                  | 4 Byte            |
| LReal       | D, W, SW                  | 8 Byte            |
| String      | D, W, SW                  | 1 - 80 characters |

The PLC has the following configuration within GX Works 3:

![GXWorks_Config](/docs/graphics/GXWorks_Config.png)

The PLC program looks like the following:

![GXWorks_Program](/docs/graphics/GXWorks_Program.png)

To configure the SLMP Connector, proceed as following:

- go to the tab 'Get data' and select tab 'Databus connectors'
- select the SLMP Connector

![ConnectorOverview](/docs/graphics/IIH_Connector_Overview.png)

- switch to tab 'Tags'
- choose 'Add data source'
- configure the PLC accordingly and save

![configuration1](/docs/graphics/Configuration1.png)

- under column 'Actions' of the newly created PLC, choose 'Add tag'
- configure the seetins for tag 'Tag_Word' as needed and save
- under column 'Actions' of the newly created PLC, choose 'Add tag'
- configure the seetins for tag 'Tag_Bool' as needed and save

![configuration2](/docs/graphics/Configuration2.png)

- select the newly created PLC and click 'Deploy' to save the configuration and start the project

![Deploy](/docs/graphics/IIH_Deploy.png)

- back on the overview page 'Databus connectors', the status of the SLMP Connector should be shown as **connected**

![Connected](/docs/graphics/IIH_Connected.png)

Now data can be transferred via the SLMP connection. Please find more information in the  [Usage](/docs/Usage.md) documentation.
