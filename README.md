# DHT22 Driver for STM32F446RE

A  **bare-metal DHT22 driver** for the **STM32F446RE** that communicates with the sensor using a single GPIO pin and provides temperature and humidity measurements with checksum verification.

## Features

- Bare-metal implementation 
- Single-wire DHT22 protocol support
- Temperature and humidity measurement
- Checksum validation for reliable data
- Simple API
- Compatible with STM32F446RE
- UART-friendly output formatting

---

## Hardware Connections

### DHT22 ↔ STM32F446RE

| DHT22 Pin | STM32F446RE |
|------------|-------------|
| VCC | 5V |
| DATA | PA10 |
| GND | GND |

---

## Sensor Data Structure

```c
typedef struct
{
    uint16_t temperature;
    uint16_t humidity;
} DHT_DATA;
```

---

## Example Output

```
Temperature = 27.4 C
Humidity = 61.8 %
```

---

## Timing Sequence

1. MCU pulls DATA line LOW for start signal.
2. DHT22 responds with acknowledgment pulses.
3. Sensor transmits 40 bits:
   - 16 bits humidity
   - 16 bits temperature
   - 8 bits checksum
4. Driver verifies checksum and returns data.

---

## Requirements

- STM32F446RE
- DHT22 sensor
- UART (optional, for debugging)

---

## Tested On

- **Board:** STM32F446RE Nucleo
- **Compiler:** arm-none-eabi-gcc
- **Environment:** STM32CubeIDE
- **Clock:** 16 MHz

---

### Author

**Mudit Goyal**
