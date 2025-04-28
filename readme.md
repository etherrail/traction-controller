# EtherRail Traction Controller TC1000PX22+D+EA
The WiFi based controller for locomotives and other rolling stock.
This device is a drop in replacement for any DCC boards.

Main Features
- WiFi enabled
- Plux2 Interface according to [NEM 658](./documentation/nem658.pdf)
- Inertia Sensor for speed control (instead of the common power control)
- Sound up to 96kHz
- 1A motor current (3.6A Peak)
- Track power probe
- Low production cost
- Tip over, stall and push detection

Product Code
- `TC` traction controller
- `1000` 1000mA nominal current
- `PX22` PluX22 plugging interface (NEM 658)
- `+D` debugging version (USB compatible, status LEDs)
- `+CA` external antenna

## To Do
- Test Boards (currently in production)
- Add GPIO pins

## Connectivity
The device connects with WiFi or Bluetooth.
An external antenna should be attached.

## Ineria Sensor
Usually, the trains are controlled by setting a motor power level, not a target speed. The IMU sensor integrates an accelerometer and a gyroscope, which can be used to estimate the actual speed of the train.

No more speed calibrations and motor ramps - the controller can automatically compensate for heavier trains or gradients. Stalling can be detect too, both total stalling and wheel-slip, which can then be counter acted with automatically induced power bursts. The controller can detect being pushed too, for example in a collision case. And even a tip over can be detected.

## Track Power Probe
The traction controller constantly measures the track voltage.
When an outage is detected (which usually happens every couple miliseconds, even with clean tracks), the controller goes into sleep mode to preserve energy on the on board capacitor bank.

This can be used to monitor the tracks quality and schedule maintenance before issues arise.

## Sound
The board contains a 3.2W@4Ohm sound chip.

To be tested.

## Function Outputs
600mA per channel.

Warning: The output are directly connected to the P-Channel mosfets, additional protected may be required for some output devices.

## Expandability
The processor used on this device (ESP32C3) is more than capable for this task.
We could add camera functionality with this chip!
DCC emulation is theoretically possible.

The board currently contains a full USB debugging interface (pads only, but a programmer is included on the ESP).
