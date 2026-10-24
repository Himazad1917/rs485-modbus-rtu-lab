# RS485 & Modbus RTU Lab

An educational reference for serial communication used by some industrial instruments. Examples are conceptual and do not assert testing with physical devices.

## RS485 vs Modbus RTU
- **RS485** defines electrical signalling characteristics for a differential serial bus.
- **Modbus RTU** defines message framing and application-level function codes commonly carried over serial links.
- RS485 does not by itself mean a device supports Modbus; verify the device manual.

## Conceptual bus layout

~~~mermaid
flowchart LR
  M[Master / gateway] --- B[RS485 bus]
  B --- D1[Device 1]
  B --- D2[Device 2]
  B --- D3[Device 3]
~~~

The physical topology, termination, biasing, cable, loading, and grounding must follow the specific devices' documentation and applicable installation rules.

## Request/response concept

~~~mermaid
sequenceDiagram
  participant M as Client / master
  participant S as Instrument / server
  M->>S: Address + function + data + CRC
  S-->>M: Address + function + response data + CRC
~~~

## Configuration checklist

- Confirm the protocol supported by the exact instrument model.
- Match baud rate, parity, stop bits, and device address.
- Use the manufacturer's register map, including data type, signedness, scaling, and word order.
- Confirm wiring labels from both manuals; terminal naming conventions can differ.
- Avoid duplicate addresses and follow the recommended bus topology.

## Guides

- [Gateway Connectivity Checklist](guides/gateway-connectivity-checklist.md) — RS485, analogue, Ethernet and LoRaWAN bring-up considerations

## Illustrative scaling example

A hypothetical register might encode a temperature in tenths of a degree. If a documented raw value were 246 and the manufacturer's map specified a scale of 0.1, the interpreted value would be 24.6 °C. This is only an arithmetic example; it is not a real device register or a recommended register address.

## Troubleshooting

| Symptom | Checks |
|---|---|
| No response | Power, polarity/terminal labels, converter, serial settings, address and protocol |
| CRC errors | Noise, wiring, settings mismatch, bus layout and termination |
| Wrong value | Register map, units, scaling, signedness and word order |
| Intermittent response | Address conflict, cabling, grounding, bus loading and timeout settings |

## References

- [Modbus specifications](https://www.modbus.org/specs.php)

This repository is a learning reference, not evidence of physical device testing or a validated commissioning procedure.