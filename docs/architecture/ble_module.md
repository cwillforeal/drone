# BLE Module Architecture
This document describes the BLE module architecture. It goes over requirements of the BLE module and functionality.
## Requirements
| ID     | Description                                                    |
| ------ | ---------------------------------------------------------------|
| BLE-001| The BLE module shall advertise for a connection                |
| BLE-002| The BLE module shall connectable as a peripheral device        |
| BLE-003| The BLE module shall have a configurable amount services/characteristics|
| BLE-004| The BLE module shall send and receive data over BLE            |

## Architecture
The BLE module is responsible for handling the sending and receiving of data over the BLE interface. At compile time other modules can configure services and characteristics for the BLE module to handle. The modules responsibility is to forward data or send data through the functions provided at compile time.
### Flow Charts

### Functions
- ble_init
Sets up the ble interface for use
- ble_start
Starts the ble advertising 