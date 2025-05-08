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

Mapa de pines (lado por lado de tu placa)
Lado izquierdo (de arriba a abajo, donde pone VIN → IO15 en la placa)
Pin	Función principal	Notas
VIN	Entrada 5V	Alimenta la placa desde fuente externa
GND	GND	Masa
IO34	Entrada	Solo entrada (ADC, touch NO)
IO35	Entrada	Solo entrada (ADC, touch NO)
IO32	GPIO, ADC, Touch	Entrada/Salida, ADC1_CH4, Touch9
IO33	GPIO, ADC, Touch	Entrada/Salida, ADC1_CH5, Touch8
IO25	GPIO, DAC	Salida DAC1
IO26	GPIO, DAC	Salida DAC2
IO27	GPIO, ADC, Touch	Entrada/Salida, ADC1_CH7, Touch7
IO14	GPIO, ADC, Touch	Entrada/Salida, ADC2_CH6, Touch6, HSPI CLK
IO12	GPIO, ADC, Touch	Entrada/Salida, ADC2_CH5, Touch5 (ojo en boot)
GND	GND	Masa
IO13	GPIO, ADC, Touch	Entrada/Salida, ADC2_CH4, Touch4
IO9	(normalmente no disponible)	Interno flash
IO10	(normalmente no disponible)	Interno flash
IO15	GPIO, ADC, Touch	Entrada/Salida, ADC2_CH3, Touch3 (ojo en boot)

Lado derecho (de arriba a abajo, donde pone 3V3 → EN en la placa)
Pin	Función principal	Notas
3V3	3.3V salida	Alimenta circuitos externos
GND	GND	Masa
IO23	GPIO	Salida SPI MOSI
IO22	GPIO, I2C SCL	Entrada/Salida
IO1	UART TX0	Salida serial (depuración)
IO3	UART RX0	Entrada serial (depuración)
IO21	GPIO, I2C SDA	Entrada/Salida
IO19	GPIO	SPI MISO
IO18	GPIO	SPI CLK
IO5	GPIO	Entrada/Salida, HSPI CS
IO17	GPIO	Entrada/Salida
IO16	GPIO	Entrada/Salida
IO4	GPIO, ADC, Touch	Entrada/Salida, ADC2_CH0, Touch0
IO0	GPIO, ADC, Touch	Boot mode, ADC2_CH1, Touch1 (ojo en boot)
IO2	GPIO, ADC, Touch	Entrada/Salida, ADC2_CH2, Touch2
GND	GND	Masa
EN	Reset	Reinicia el micro

Pines a tener cuidado en arranque (boot):
IO0 → LOW entra en modo flash

IO2 → Debe estar LOW o flotando

IO15 / IO12 → No conectarlos a GND en boot (afectan arranque)
