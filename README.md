# SLMP Connector

This example shows how to use the Industrial Edge app SLMP Connector.

* [SLMP Connector](#slmp-connector)
  * [Description](#description)
    * [Overview](#overview)
    * [General task](#general-task)
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

The SLMP Connector is an application that runs on the individual Industrial Edge Device. Connections can be configured using the Common Configurator for Industrial Edge. The connector transfers the value series of selected data points from a PLC to the Databus. From there the data can be used within other Edge apps, e.g. the Flow Creator.

### General task

Here we configure a connection to a Mitsubishi PLC FX5U (iQF) using the SLMP Connector. The FX5U acts as SLMP server and the Industrial Edge Device acts as SLMP client. The data is published on the Databus. By using the application Flow Creator, we fetch the metadata of the SLMP Connector, write some data on the configured tags and read out the new data.

![overview](/docs/graphics/Slmparchi.png)

## Requirements

### Prerequisites

* Access to an Industrial Edge Management (IEM) with onboarded Industrial Edge Device (IED)
* IEM: Installed system configurator for Databus
* IED: Installed apps Databus, Flow Creator, common Configurator, Registry Service, SLMP Connector, IIH Essentials (optional)
* IED is connected to Mitsubishi PLC via Ethernet
* GX Works 3 project loaded on PLC
* Google Chrome (Version ≥ 72)

### Used components

* Industrial Edge Management (IEM) V1.16.11
* Industrial Edge Virtual Device (OS) V2.1.0-22-x86-64
  * Databus V2.3.2-5
  * Flow Creator V1.17.0-2
  * Common Configurator V1.9.0-4
  * Common Import Converter V2.1.0-2
  * Registry Service V1.10.0-0
  * SLMP Connector V2.1.0-0
  * IIH Essentials V1.10.2
* PLC: Mitsubishi FX5U
* GX Works 3 (Mitsubishi engineering software)

### PLC project

The used PLC project *Test.gx3* can be found in the [src folder](/src/).

## Configuration

You can find further information about the following steps in the [Configuration](/docs/Installation.md) documentation:

- [Overview](/docs/Installation.md#overview)
- [Install SLMP Connector](/docs/Installation.md#install-slmp-connector)
- [Configure Databus](/docs/Installation.md#configure-Databus)
- [Configure SLMP via Common Configurator](/docs/Installation.md#configure-slmp-via-Common-Configurator)

## Usage

As soon as the SLMP Connector is configured, data can be transfered.

You can find further information about how to handle the data via the Flow Creator in the [Usage](/docs/Usage.md) documentation:

* [Read metadata](/docs/Usage.md#read-metadata)
* [Write data](/docs/Usage.md#write-data)
* [Read data](/docs/Usage.md#read-data)
* [Use IIH Essentials](/docs/Usage.md#use-IIH-Essentials)

## Documentation

You can find further documentation and help in the following links

* [Industrial Edge Hub](https://iehub.eu1.edge.siemens.cloud/#/documentation)
* [Industrial Edge Forum](https://www.siemens.com/industrial-edge-forum)
* [Industrial Edge landing page](https://new.siemens.com/global/en/products/automation/topic-areas/industrial-edge/simatic-edge.html)
* [Industrial Edge GitHub page](https://github.com/industrial-edge)

## Contribution

Thank you for your interest in contributing. Anybody is free to report bugs, unclear documentation, and other problems regarding this repository in the Issues section. Additionally everybody is free to propose any changes to this repository using Pull Requests.

If you haven't previously signed the [Siemens Contributor License Agreement](https://cla-assistant.io/industrial-edge/) (CLA), the system will automatically prompt you to do so when you submit your Pull Request. This can be conveniently done through the CLA Assistant's online platform. Once the CLA is signed, your Pull Request will automatically be cleared and made ready for merging if all other test stages succeed.
 

## Licence and Legal Information

Please read the [Legal information](LICENSE.txt).


IMPORTANT - PLEASE READ CAREFULLY:

 

This documentation describes how you can download and set up containers which consist of or contain third-party software. By following this documentation you agree that using such third-party software is done at your own discretion and risk. No advice or information, whether oral or written, obtained by you from us or from this documentation shall create any warranty for the third-party software. Additionally, by following these descriptions or using the contents of this documentation, you agree that you are responsible for complying with all third party licenses applicable to such third-party software. All product names, logos, and brands are property of their respective owners. All third-party company, product and service names used in this documentation are for identification purposes only. Use of these names, logos, and brands does not imply endorsement.
