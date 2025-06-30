# JL 2.4G Bluetooth Low-Latency Audio Headset Solution: Chip Selection, Latency, Hardware Design

![Dongle Diagram](https://github.com/blevoice/pic/blob/16e49ad372de95307cbbf40a83848b93e3f134a6/063000.png)

This document introduces JL's low-latency audio headset solution using 2.4G/Bluetooth technology.

## 1. Chip Selection
- **USB Dongle Side**:
  - JL7016M or JL7086E
  - Capable of 48KHz/16bit stereo output
  - Supports UAC (USB Audio Class) - plug-and-play, no driver required
- **Headset Side**:
  - TWS: JL7083G
  - Stereo headphones: JL7083F

## 2. Audio Transmission Process
### Uplink (microphone to host):
1. Audio sampled via USB (~2.5ms)
2. Encoded (~1ms)
3. Transmitted over 2.4G/Bluetooth using LC3 codec at 48KHz/16bit mono

### Downlink (host to headset):
1. Audio LC3 encoded at 48KHz/16bit stereo
2. Transmitted wirelessly to headset
3. Decoded (~2ms)
4. Playback via DAC (~7ms)

## 3. Latency Performance
- **TWS headphones**: ~20ms total latency
- **Over-ear/headband-style headphones**: ~17ms total latency

These values are excellent for gaming and multimedia scenarios where low latency is crucial.

![Solution Overview](https://github.com/blevoice/pic/blob/16e49ad372de95307cbbf40a83848b93e3f134a6/063011.png)

## 4. JL 2.4G Bluetooth Low-Latency Headset Solution Overview

### (1) Chipset & Basic Capabilities
- JL7016M or JL7086E for USB Dongle (receiver/transmitter)
- Outputs 48KHz/16bit stereo
- Supports UAC (plug-and-play with no driver required)

### (2) Encoding - Transmission - Decoding Flow
**Uplink (mic to host device)**:
1. Mic collects sound
2. USB sampling (~2.5ms)
3. LC3 encoding (~1ms)
4. Transmitted via 2.4G/Bluetooth to host (PC/phone)

**Downlink (host to headset)**:
1. Host audio encoded into LC3 (48KHz/16bit stereo)
2. Transmitted wirelessly to headset
3. Decoded (~2ms)
4. DAC playback (~7ms)

### (3) Latency Performance
- TWS headphones total latency: ~20ms
- Over-ear headphones total latency: ~17ms
- Excellent for low-latency needs in gaming/video applications

## 5. Chip Solution Comparison

| Solution Type | Dongle Chip      | Headset Chip | Protocol | Notes            |
|---------------|------------------|--------------|----------|------------------|
| Old           | JL7016M-QFN32    | JL7018F      | EDR      | Legacy solution  |
| New #1        | JL7016M-QFN32    | JL7083F      | LC3      | Stereo           |
| New #2        | JL7086E-QFN32    | JL7083F      | LC3      | Stereo           |
| New #3        | JL7086E-QFN32    | JL7083G      | LC3      | TWS              |

- **Headband-style gaming headset**: JL7086E + JL7083F
- **TWS-style earbuds**: JL7086E + JL7083G

![Power Consumption](https://github.com/blevoice/pic/blob/16e49ad372de95307cbbf40a83848b93e3f134a6/063013.png)

## 6. Power Consumption Note
2.4G wireless inherently consumes more power. The typical power consumption is around 20-30mA, and currently, this is a design limitation that cannot be significantly reduced.

## 7. Hardware Block Diagrams

### Dongle Side
![Dongle Block Diagram](https://github.com/blevoice/pic/blob/16e49ad372de95307cbbf40a83848b93e3f134a6/063014.jpeg)
*(Typically includes USB interface, JL7016M/7086E chip, 2.4G RF module, and antenna)*

### Headset Side
![Headset Block Diagram](https://github.com/blevoice/pic/blob/16e49ad372de95307cbbf40a83848b93e3f134a6/063015.jpeg)
*(Typically includes microphone, JL7083F/G chip, speaker/DAC output, battery/power management, and antenna)*
