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
