# EtherRail Traction Controller TC800N652+D+CA+2B
The WiFi based controller for locomotives and other rolling stock.
This device is a drop in replacement for any DCC boards.

Main Features
- WiFi enabled
- Complies with [NEM 652](./documentation/nem652.pdf)
- Up to 800mA current (1500mA peak)
- Track power probe
- Adaptive motor voltage capping
- 3€ production cost

Product Code
- `TC` traction controller
- `800` 800mA nominal current
- `N652` plugging interface
- `+D` debugging version (includes USB header)
- `+CA` on-board chip antenna
- `+2B` 2000uF bridgeing capacitor

## To Do
- Validate Design (We are currently testing this device)
- Add support for lights
- Add versions for PlugX16S, PlugX22, ...

## Track Power Probe
The traction controller constantly measures the track voltage. 
This can be used to monitor the tracks quality and schedule maintenance before issues arise.

## Expandability
The processor used on this device (ESP32C3) is more than capable for this task.
We could easily add sound or even camera functionality with this chip!

The board currently contains a full USB debugging interface (headers only, but a programmer is included on the ESP). 
No parts are currently on the back side of the board, thus it can be expanded very easily!
