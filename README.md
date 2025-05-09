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

## Explicación detallada de las Notas

| Nota escrita en la tabla | Explicación clara y sencilla |
|--------------------------|------------------------------|
| **Alimenta la placa desde fuente externa** | Conectas una fuente de alimentación (batería o fuente de 5V). Este pin (VIN) da energía a toda la placa si no usas USB. |
| **Masa (GND)** | Es el negativo del circuito. Todas las tierras de tu proyecto deben ir conectadas al GND del ESP32. |
| **Solo entrada** | Pines que solo reciben señales (ejemplo: sensores). No sirven para encender LEDs ni sacar señal. |
| **ADC (Analog to Digital Converter)** | Lee señales analógicas (0 a 3.3V) y las convierte en números digitales (0–4095). Útil para potenciómetros o sensores analógicos. |
| **Touch** | Sirve para crear botones táctiles (detecta toques sin contacto físico). Solo disponible en algunos pines. |
| **DAC (Digital to Analog Converter)** | Permite crear señales analógicas (0 a 3.3V). Solo en D25 y D26. Útil para audio o salidas de voltaje variable. |
| **HSPI CLK / CS** | Pines para comunicación SPI (con pantallas, memorias, etc.). Si no usas SPI, puedes usarlos como pines normales. |
| **(ojo en boot)** | Estos pines (D0, D12, D15) influyen en el arranque. Si se conectan mal (por ejemplo a GND), la placa no arranca. Hay que tener precaución. |
| **Interno (no usar)** | D9 y D10 están conectados a la memoria interna (flash). Si los tocas, dañas el funcionamiento de la placa. No se deben usar nunca. |
| **UART TX0 / RX0 (depuración)** | Son los pines que comunican con el ordenador (por USB). Sirven para enviar/recibir texto (monitor serial). Se usan para ver mensajes cuando programas. |
| **Reinicia el microcontrolador (EN)** | Pin que resetea la placa (igual que pulsar el botón reset). Si lo conectas a GND un instante, la placa reinicia. |
| **Salidas SPI MOSI, MISO, CLK** | Pines usados para comunicación SPI (rápida, con pantallas, memorias, etc.). Se pueden usar como pines normales si no usas SPI. |
| **I2C SDA, SCL** | Pines usados para comunicar con sensores/pantallas por I2C (lento pero fácil). Estos son los recomendados pero puedes usar otros. |

Pines a tener cuidado en arranque (boot):

Cuando un pin pone depuración → sirve para enviar mensajes al ordenador.
Cuando pone reservado flash → ni lo toques (te carga el sistema).
Cuando pone ojo en boot → cuidado cómo lo conectas al arrancar.

IO0 → LOW entra en modo flash

IO2 → Debe estar LOW o flotando

IO15 / IO12 → No conectarlos a GND en boot (afectan arranque)

## Explicación PULL-DOWN, PULL-UP resistencia en pulsador

Cuando tú conectas un pulsador a un pin del ESP32, ese pin necesita tener siempre un valor claro: o HIGH (1) o LOW (0). El problema es que cuando el pulsador no está pulsado y no hay resistencia, el pin queda “al aire” o flotante — no está conectado ni a 0V ni a 3.3V — y el ESP32 puede leer valores aleatorios, porque capta interferencias o ruido eléctrico.

Ahí es donde entra la resistencia pull-up o pull-down:

Resistencia pull-down (a GND): Conectas una resistencia de 10 kΩ entre el pin y GND. Así, cuando el pulsador está abierto, el pin se mantiene a LOW (0). Cuando pulsas, conectas el pin a 3.3V y el estado pasa a HIGH (1).

Resistencia pull-up (a Vcc): Conectas una resistencia entre el pin y 3.3V. Así, cuando el pulsador está abierto, el pin está en HIGH (1). Al pulsar, conectas el pin a GND y el estado pasa a LOW (0).
