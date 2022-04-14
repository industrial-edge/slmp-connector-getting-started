# SLMP Connector

Using the Industrial Edge applications SLMP Configurator and SLMP Connector.

* [SLMP Connector](#slmp-connector)
  * [Description](#description)
    * [Overview](#overview)
    * [General Task](#general-task)
  * [Requirements](#requirements)
    * [Prerequisites](#prerequisites)
    * [Used components](#used-components)
    * [PLC project](#plc-project)
  * [Installation](#installation)
  * [Usage](#usage)
  * [Documentation](#documentation)
  * [Contribution](#contribution)
  * [Licence and Legal Information](#licence-and-legal-information)

## Description

### Overview

This tutorial shows how to use the Industrial Edge applications SLMP Configurator and SLMP Connector to establish a connection to a Mitsubishi PLC. These PLC variants are supported:

* Mitsubishi iQR series
* Mitsubishi iQF series

With the connection between an Industrial Edge Device (SLMP client) and a Mitsubishi PLC (SLMP server) data can be transfered. On the Industrial Edge Device (IED), the data is published to the Databus. From there the data can be used within other Edge apps.

### General Task

Here we configure a connection to a Mitsubishi PLC FX5U (iQF), that supports the SLMP protocol. The FX5U acts as SLMP server and the IED acts as SLMP client. Data is read from the FX5U and published on the Databus. By using the application IE Flow Creator, the received data on the dedicated topic can be print out.

![overview](/docs/graphics/Overview.png)

## Requirements

### Prerequisites

* Access to an Industrial Edge Management (IEM) with onboarded Industrial Edge Device (IED)
* IEM: Installed system configurator for Databus
* IED: Installed system app Databus
* IED: Installed app SLMP Configurator
* IED: Installed app SLMP Connector
* IED: Installed app IE Flow Creator
* IED is connected to Mitsubishi PLC via Ethernet
* Google Chrome (Version ≥ 72)

### Used components

* Industrial Edge Management (IEM) V1.4.0-42 / V1.5.6
  * IE Databus Configurator V 1.6.19
* Industrial Edge Device (IED) V 1.3.0-57
  * IE Databus V 1.6.3
  * SLMP Configurator V1.0.0
  * SLMP Connector V1.0.0
  * IE Flow Creator V1.3.3
* PLC: Mitsubishi FX5U
* Google Chrome

### PLC project

The used project for the Mitsubishi PLC *PlcProject.zip* can be found in the [src folder](/src/).

## Installation

You can find the further information about the following steps in the [Installation](/docs/Installation.md) documentation:

* [Configure IE Databus](/docs/Installation.md#configure-ie-databus)
* [Install SLMP Configurator and Connector](/docs/Installation.md#install-slmp-configurator-and-connector)
* [Configure SLMP Connector](/docs/Installation.md#configure-slmp-connector)

## Usage

As soon as the SLMP Connector is configured to connect to the Mitsubishi PLC, data can be transfered.

You can find the further information about how to use the SLMP connector in the [Usage](/docs/Usage.md) documentation:

* [Read data](/docs/Usage.md#read-data)
* [Write data](/docs/Usage.md#write-data)

## Documentation

Add links to documentation. Either on external URL or in the doc folder. Please use always link to a file not to a directory (it doesn't work with static site generator engines).

Add these links:

You can find further documentation and help in the following links

* [Industrial Edge Hub](https://iehub.eu1.edge.siemens.cloud/#/documentation)
* [Industrial Edge Forum](https://www.siemens.com/industrial-edge-forum)
* [Industrial Edge landing page](https://new.siemens.com/global/en/products/automation/topic-areas/industrial-edge/simatic-edge.html)
* [Industrial Edge GitHub page](https://github.com/industrial-edge)

## Contribution

Thank you for your interest in contributing. Anybody is free to report bugs, unclear documentation, and other problems regarding this repository in the Issues section.
Additionally everybody is free to propose any changes to this repository using Pull Requests.

If you are interested in contributing via Pull Request, please check the [Contribution License Agreement](Siemens_CLA_1.1.pdf) and forward a signed copy to [industrialedge.industry@siemens.com](mailto:industrialedge.industry@siemens.com?subject=CLA%20Agreement%20Industrial-Edge).

## Licence and Legal Information

Please read the [Legal information](LICENSE.txt).
