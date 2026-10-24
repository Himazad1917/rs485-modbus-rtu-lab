# Industrial Gateway Connectivity — Field Checklist

A vendor-neutral checklist for planning a sensor-to-gateway connection. Exact steps depend on the sensor, gateway, protocol, firmware, and site network design.

## First identify the interface

| Interface | What must be confirmed |
|---|---|
| RS485 / Modbus RTU | A/B or D+/D− terminal naming in each manual, baud rate, parity, stop bits, slave address, register map, bus topology and termination |
| Ethernet / Modbus TCP | IP addressing, subnet/VLAN, TCP port approved by the site, unit identifier if required, register map, access controls |
| LoRaWAN | Regional frequency plan, device activation method, DevEUI/JoinEUI/AppKey handling, gateway coverage, network-server configuration |
| 4–20 mA | Loop wiring, loop supply, input resistance, channel mode, scaling, fault-current handling where supported |
| 0–10 V | Common/reference arrangement, input impedance, signal range, grounding and noise considerations |

## Bring-up sequence

1. Record exact model numbers, firmware versions, wiring diagrams, and required interfaces.
2. Verify power and wiring against manufacturer documentation before energising.
3. Configure one device at a time and record the exact serial/network settings.
4. Confirm raw data first, then validate scaling, units, timestamps, and quality flags.
5. Test communication loss and recovery in a controlled environment.
6. Check that credentials and keys are stored in approved secret storage; never commit them to a repository.
7. Document the known-good configuration without publishing passwords, AppKeys, private addresses, customer names, or other confidential data.

## RS485/Modbus RTU checks

- Confirm that the instrument actually supports Modbus RTU; RS485 is an electrical interface, not a protocol.
- Match baud rate, parity, and stop bits across the bus.
- Use the manufacturer's register map and correct data type/word order.
- Observe the recommended daisy-chain topology, termination, biasing, cable, and maximum loading for the devices used.
- Confirm device address uniqueness and avoid connecting/disconnecting live wiring unless the manual and site procedure explicitly permit it.

## Troubleshooting decision path

~~~mermaid
flowchart TD
  A[No data] --> B{Power and wiring verified?}
  B -- No --> C[Check approved wiring and supply]
  B -- Yes --> D{Physical interface matches?}
  D -- No --> E[Confirm fitted interface and converter]
  D -- Yes --> F{Settings and address match?}
  F -- No --> G[Use exact device manual]
  F -- Yes --> H[Check protocol, register map, and gateway logs]
~~~

## Acceptance record

Record: device model, gateway model, interface, firmware, configuration source, test date, test result, observed error messages, recovery test, and sign-off. Keep any secret values in the authorised system rather than in this record.

This checklist is educational and does not assert that any specific gateway or sensor has been tested.