# Home Energy Management System (HEMS)

## Project Overview

### Motivation

This project serves as a learning experience for myself as I've gained interest in energy management to minimize energy usage.

### Project Summary

This project contains the core logic to minimize energy usage and cost at home using energy data from different sensors.

Moreover, it contains a web-based application that allows users to monitor the energy flow in real-time and accepts users inputs for system control.

Furthermore, it contains the gateway's code source that acts like translators converting device-specific data payload into standard data package to send into the system.

### System Architecture

The system can be divided into **five** layers:

1. **User Interface**: Allows users to view and control the home's energy production and consumption.
2. **Core Logic**: Uses sensor data and user inputs to optimise energy usage.
3. **Database**: Records data flowing between the system.
4. **Gateway**: Translates the data from the devices to standardised formats and send them to the database and core logic.
5. **Devices**: Physical hardware or cloud APIs that produce data affecting the energy production and consumption of the home.

## Development Plan

### Standardise Messaging 

All messages flowing between the gateway and the core logic and database must be in a standardised format.

We can break down the messages into **three** different types:
- **Telemetry**: Data from the physical devices or cloud APIs and to be sent to the core logic and database, called *upstreaming*.
- **Command**: Data from the core logic to be sent to the devices, called *downstreaming*.
- **Event**: Alerts from the devices, requiring immediate feedback.

This project uses **JSON** as the messaging package, since it is relatively lightweight and easy to parse and debug. Furthermore, we use **JSON Schema** to validate the messages ensuring that the messages strictly follow a standard format.

### MQTT Topic Definition

The transfer of messages between the sub-system can be done over **MQTT**, which is the de-facto IoT messaging protocol due to its lightweight, publish-subscribe model allowing ease of integration and future expansions.

This project defines the general structure of the MQTT topic as:

```
<root>/<gateway_id>/<message_type>/<device_id>
```

Where:
- **root** is the house.
- **gateway_id** is the ID of the gateway the message passes through.
- **message_type** is one of three types of messages: telemetry, command, or event.
- **device_id** is the ID of the device that sent the data or is going to receive the command.

