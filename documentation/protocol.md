# Traction Controller Client Protocol (TCCP)
This document describes the TCP-socket based protocol used to interface with etherrail traction controllers. This protocol may be used by any other Wifi-based traction controller, but modifications should be posed as issues on here to create a common standard.

The traction controller does not store **any** settings. Every setting has to be reapplied on startup.

## Sent by traction controller
Listed are the packages sent by the traction controller.
A orchestrator has to handle all the messages sent by traction controllers.

### `0x00` Keep Alive
The traction controller will send this package every **250ms**. The traction controller should be flagged as dead when no package (not just keep alive) was received for over **1000ms**.

### `0x21 [Quality]` Power Quality
The traction controller may periodically send this package to report the current track quality. We are sending it every 25mm in testing, but this may be decreased and only reported when the quality is poor. 

The quality parameter ranges from 0 (0V track voltage) to 255 (20V track voltage).

## Sent by orchestrator
The orchestrator sends commands to the traction controller. All commands are listed here.

### `0x00` Keep Alive
This package should be sent every **250ms**. The orchestrator has to send any package every **1000ms** or the traction controller will automatically perform an emergency stop. 

### `0x01` Emergency Stop
The traction controller will perform and emergency stop.

### `0x91 [Speed]` Set Speed
The traction controller will apply the speed as a voltage to the motor. 

Speed 0 will stop the motor, while 255 will apply the maximum voltage set by [Maximum Motor Voltage](#0xa1-max-voltage-maximum-motor-voltage).

### `0xa1 [Max Voltage]` Maximum Motor Voltage
This setting prevents motor damage. Any speed operations will automatically be scaled by the maximum voltage. Max voltage parameter ranges from 0 = 0V to 255 = 20V. 

Example: `0xa1 0x7f 0x91 0xff` will apply 10V to the motor, while a following `0x91 0x7f` will apply 5V. 