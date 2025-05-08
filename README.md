# ESP32-PINES
Características generales de tu placa:
Microcontrolador: Tensilica Xtensa LX6 dual-core (240 MHz)

WiFi: 802.11 b/g/n

Bluetooth: 4.2 (BLE + Classic)

Flash: 4 MB (normalmente)

SRAM: 520 KB

GPIOs: Hasta 30 pines configurables

ADC: 18 canales (12 bits)

DAC: 2 canales

Touch sensors: 10 pines

Interfaces: UART, SPI, I2C, PWM, etc.

## Mapa de pines — ESP32 DevKit v1 (ESP32-WROOM-32D)

## Mapa de pines — ESP32 DevKit v1 (ESP32-WROOM-32D)

### Lado izquierdo (VIN → D15)

| Pin   | GPIO  | Función principal   | Notas                                        |
|-------|-------|---------------------|----------------------------------------------|
| VIN   | -     | Entrada 5V          | Alimenta la placa desde fuente externa       |
| GND   | -     | GND                 | Masa                                         |
| D34   | 34    | Solo entrada        | ADC1_CH6, no salida                          |
| D35   | 35    | Solo entrada        | ADC1_CH7, no salida                          |
| D32   | 32    | GPIO, ADC, Touch    | ADC1_CH4, Touch9                             |
| D33   | 33    | GPIO, ADC, Touch    | ADC1_CH5, Touch8                             |
| D25   | 25    | GPIO, DAC           | DAC1                                         |
| D26   | 26    | GPIO, DAC           | DAC2                                         |
| D27   | 27    | GPIO, ADC, Touch    | ADC1_CH7, Touch7                             |
| D14   | 14    | GPIO, ADC, Touch    | ADC2_CH6, Touch6, HSPI CLK                   |
| D12   | 12    | GPIO, ADC, Touch    | ADC2_CH5, Touch5 **(ojo en boot)**           |
| GND   | -     | GND                 | Masa                                         |
| D13   | 13    | GPIO, ADC, Touch    | ADC2_CH4, Touch4                             |
| D9    | 9     | Interno (no usar)   | Reservado para flash                         |
| D10   | 10    | Interno (no usar)   | Reservado para flash                         |
| D15   | 15    | GPIO, ADC, Touch    | ADC2_CH3, Touch3 **(ojo en boot)**           |

---

### Lado derecho (3V3 → EN)

| Pin   | GPIO  | Función principal   | Notas                                        |
|-------|-------|---------------------|----------------------------------------------|
| 3V3   | -     | Salida 3.3V         | Alimenta circuitos externos                  |
| GND   | -     | GND                 | Masa                                         |
| D23   | 23    | GPIO                | SPI MOSI                                     |
| D22   | 22    | GPIO, I2C SCL       | Entrada/Salida                               |
| TX    | 1     | UART TX0            | Salida serial (depuración)                   |
| RX    | 3     | UART RX0            | Entrada serial (depuración)                  |
| D21   | 21    | GPIO, I2C SDA       | Entrada/Salida                               |
| D19   | 19    | GPIO                | SPI MISO                                     |
| D18   | 18    | GPIO                | SPI CLK                                      |
| D5    | 5     | GPIO                | HSPI CS                                      |
| D17   | 17    | GPIO                | Entrada/Salida                               |
| D16   | 16    | GPIO                | Entrada/Salida                               |
| D4    | 4     | GPIO, ADC, Touch    | ADC2_CH0, Touch0                             |
| D0    | 0     | GPIO, ADC, Touch    | ADC2_CH1, Touch1 **(Boot mode)**             |
| D2    | 2     | GPIO, ADC, Touch    | ADC2_CH2, Touch2                             |
| GND   | -     | GND                 | Masa                                         |
| EN    | -     | Reset               | Reinicia el microcontrolador                 |


Pines a tener cuidado en arranque (boot):
IO0 → LOW entra en modo flash

IO2 → Debe estar LOW o flotando

IO15 / IO12 → No conectarlos a GND en boot (afectan arranque)
