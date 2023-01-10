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
  * [Configuration](#configuration)
  * [Usage](#usage)
  * [Documentation](#documentation)
  * [Contribution](#contribution)
  * [Licence and Legal Information](#licence-and-legal-information)

## Description

### Overview

This tutorial shows how to use the Industrial Edge application SLMP Connector to establish a connection between an Industrial Edge Device (IED) and a 3rd party PLC that supports SLMP (Seamless Messaging Protocol), which is a client/server protocol for point to point communication between standard TCP/IP Ethernet devices and CC-Link IE networks.

These PLC variants are supported:

* Mitsubishi iQR series
* Mitsubishi iQF series

The SLMP Connector is an application that runs on the individual IED. Connections can be configured using the Common Configurator for Industrial Edge. The connector transfers the value series of selected data points from a PLC to the Databus. From there the data can be used within other Edge apps, e.g. the Flow Creator.

### General Task

Here we configure a connection to a Mitsubishi PLC FX5U (iQF) using the SLMP Connector. The FX5U acts as SLMP server and the IED acts as SLMP client. The data is published on the IE Databus. By using the application IE Flow Creator, we fetch the metadata of the SLMP Connector, write some data on the configured tags and read out the new data.

![overview](/docs/graphics/Overview.png)

## Requirements

### Prerequisites

* Access to an Industrial Edge Management (IEM) with onboarded Industrial Edge Device (IED)
* IEM: Installed system configurator for Databus
* IED: Installed system app Databus
* IED: Installed app SLMP Connector
* IED: Installed app IE Flow Creator
* IED is connected to Mitsubishi PLC via Ethernet
* GX Works 3 project loaded on PLC
* Google Chrome (Version ≥ 72)

### Used components

* Industrial Edge Management (IEM) V1.5.1-4 / V1.8.6
  * IE Databus Configurator V1.7.8
* Industrial Edge Device (OS) V1.8.0-6
  * IE Databus V1.7.1
  * IIH Configurator V1.5.0
  * Registry Service V1.5.0
  * SLMP Connector V2.0.0-2
  * IE Flow Creator V1.10.0-3
  * Data Service V1.5.0
* PLC: Mitsubishi FX5U
* GX Works 3 (Mitsubishi engineering software)

### PLC project

The used PLC project *Test.gx3* can be found in the [src folder](/src/).

## Configuration

You can find further information about the following steps in the [Configuration](/docs/Installation.md) documentation:

- [Overview](/docs/Installation.md#overview)
- [Install SLMP Connector](/docs/Installation.md#install-slmp-connector)
- [Configure IE Databus](/docs/Installation.md#configure-ie-databus)
- [Configure SLMP via IIH Configurator](/docs/Installation.md#configure-slmp-via-iih-configurator)

## Usage

As soon as the SLMP Connector is configured, data can be transfered.

You can find further information about how to handle the data via the IE Flow Creator in the [Usage](/docs/Usage.md) documentation:

* [Read metadata](/docs/Usage.md#read-metadata)
* [Write data](/docs/Usage.md#write-data)
* [Read data](/docs/Usage.md#read-data)
* [Use Data Service](/docs/Usage.md#use-data-service)

## Documentation

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
