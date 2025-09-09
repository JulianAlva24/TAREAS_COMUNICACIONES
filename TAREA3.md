# Guía completa del **MAX232** (Transceptor RS-232 de doble canal)

> **Objetivo de la tarea**
>
> - Revisar el *datasheet* del MAX232 y documentar: **esquema eléctrico**, **funcionamiento**, **variantes** y **prestaciones típicas**.  
> - Indicar si **se sigue usando hoy**, aplicaciones, **ventajas / desventajas** y **versiones** relacionadas.  
> - Entregar una **guía informativa lista para GitHub** (README) con estilo, tablas y diagramas.

---

## Índice
- [Resumen rápido](#resumen-rápido)
- [1. ¿Qué es el MAX232?](#1-qué-es-el-max232)
- [2. Esquema eléctrico típico](#2-esquema-eléctrico-típico)
  - [2.1. Diagrama (Mermaid)](#21-diagrama-mermaid)
  - [2.2. Conexiones esenciales y valores de capacitores](#22-conexiones-esenciales-y-valores-de-capacitores)
- [3. Funcionamiento interno](#3-funcionamiento-interno)
- [4. Pinout (16 pines)](#4-pinout-16-pines)
- [5. Prestaciones típicas](#5-prestaciones-típicas)
- [6. Variantes y versiones relacionadas](#6-variantes-y-versiones-relacionadas)
- [7. ¿Se sigue usando hoy? Aplicaciones reales](#7-se-sigue-usando-hoy-aplicaciones-reales)
- [8. Ventajas y desventajas](#8-ventajas-y-desventajas)
- [9. Buenas prácticas de diseño](#9-buenas-prácticas-de-diseño)
- [10. Ejemplo de uso rápido](#10-ejemplo-de-uso-rápido)
- [11. Referencias](#11-referencias)

---

## Resumen rápido

- **Transceptor RS-232 de doble canal**: *2 drivers (TX) + 2 receptores (RX)*.  
- **Alimentación**: +5 V (MAX232). Internamente **genera ≈ ±8.5 V** con *charge pump* y **4 capacitores externos**.  
- **Velocidad**: hasta **120 kbit/s** (MAX232); versiones **E/A/3232** alcanzan **200–250 kbit/s**.  
- **Compatibilidad**: cumple **TIA/EIA-232-F** e **ITU V.28**; entradas RS-232 toleran **±30 V**.  
- **Uso actual**: Muy vigente en **industria**, consolas de **equipos de red**, **instrumentación**, **retro-computación** y **mantenimiento**.

---

## 1. ¿Qué es el MAX232?

El **MAX232** es un CI que adapta niveles **TTL/CMOS (5 V)** a **RS-232 (≈ ±6…±10 V)** y viceversa, usando un **doblador e inversor de tensión por bomba de carga** (*charge pump*) a partir de una sola fuente **+5 V**. Integra **dos transmisores** (TTL→RS-232) y **dos receptores** (RS-232→TTL).

---

## 2. Esquema eléctrico típico

> El circuito típico usa **cuatro capacitores externos** para la bomba de carga (**C1–C4**) y un **bypass** en VCC. Para MAX232, los capacitores recomendados son **1 µF** y la tasa típica es **hasta 120 kbps**.

### 2.1. Diagrama (Mermaid)


```mermaid
flowchart LR
  VCC["+5V"] -->|C_BYPASS| MAX232
  subgraph MAX232[ MAX232 ]
    direction TB
    CP[ "Charge pump\n(C1,C2,C3,C4)" ]
    TX1[ "Driver T1: T1IN → T1OUT" ]
    RX1[ "Receiver R1: R1IN → R1OUT" ]
    TX2[ "Driver T2: T2IN → T2OUT" ]
    RX2[ "Receiver R2: R2IN → R2OUT" ]
    CP --> VPOS["V+ (≈ +8.5V)"]
    CP --> VNEG["V- (≈ -8.5V)"]
  end

  UART[ "MCU/UART TTL (5V)" ]
  RS232[ "Conector RS-232 (DB9/DB25)" ]

  UART -->|T1IN/T2IN| MAX232
  MAX232 -->|R1OUT/R2OUT| UART
  MAX232 -->|T1OUT| RS232
  RS232 -->|R1IN| MAX232
  MAX232 -->|T2OUT| RS232
  RS232 -->|R2IN| MAX232
```

### 2.2. Conexiones esenciales y valores de capacitores

- **C1** entre **C1+ (pin 1)** y **C1− (pin 3)** → *“volador” para doblado de tensión*  
- **C2** entre **C2+ (pin 4)** y **C2− (pin 5)** → *“volador” para inversión*  
- **C3** entre **V+ / VS+ (pin 2)** y **GND**  
- **C4** entre **V− / VS− (pin 6)** y **GND**  
- **C_BYPASS** entre **VCC (pin 16)** y **GND (pin 15)**  
- **Valores recomendados (MAX232)**: **1 µF** en C1–C4; bypass de **0.1–1 µF** en VCC.  
- **Notas**: con **MAX232A / MAX202** se permiten **0.1 µF**; en **MAX3232** también se usan **0.1 µF** (ver variantes).

---

## 3. Funcionamiento interno

1. **Bomba de carga** que **duplica** e **invierte** la tensión de +5 V para generar **V+** y **V−**.  
2. **Drivers**: convierten **TTL→RS-232** e **invierten** la lógica usando V+/V−.  
3. **Receptores**: convierten **RS-232→TTL**, con **umbral ~1.3 V** e **histeresis ~0.5 V** para robustez ante ruido.  
4. **Lógica RS-232** invertida: “mark” (1) ≈ tensión **negativa**; “space” (0) ≈ **positiva**.

---

## 4. Pinout (16 pines)

| # | Nombre | Tipo | Descripción breve |
|---:|---|---|---|
| 1 | **C1+** | — | Terminal + del capacitor C1 |
| 2 | **VS+ / V+** | **O** | Salida positiva de la bomba (almacenamiento) |
| 3 | **C1−** | — | Terminal − del capacitor C1 |
| 4 | **C2+** | — | Terminal + del capacitor C2 |
| 5 | **C2−** | — | Terminal − del capacitor C2 |
| 6 | **VS− / V−** | **O** | Salida negativa de la bomba (almacenamiento) |
| 7 | **T2OUT** | **O** | Salida RS-232 (hacia conector) |
| 8 | **R2IN** | **I** | Entrada RS-232 (desde conector) |
| 9 | **R2OUT** | **O** | Salida TTL/CMOS hacia UART |
| 10 | **T2IN** | **I** | Entrada TTL/CMOS desde UART |
| 11 | **T1IN** | **I** | Entrada TTL/CMOS desde UART |
| 12 | **R1OUT** | **O** | Salida TTL/CMOS hacia UART |
| 13 | **R1IN** | **I** | Entrada RS-232 (desde conector) |
| 14 | **T1OUT** | **O** | Salida RS-232 (hacia conector) |
| 15 | **GND** | — | Tierra |
| 16 | **VCC** | — | +5 V |

---

## 5. Prestaciones típicas

- **Normas**: **TIA/EIA-232-F** e **ITU V.28**.  
- **VCC**: **+5 V** (4.5–5.5 V).  
- **Tasa de datos**: **hasta 120 kbit/s** (MAX232); versiones E/A/3232 **hasta 200–250 kbit/s**.  
- **Consumo**: **≈ 8 mA típico** (MAX232).  
- **Entradas RS-232**: toleran **±30 V**.  
- **ESD**: **~2 kV HBM** (MAX232); **±15 kV HBM** y **IEC 61000-4-2** en versiones **E**.

---

## 6. Variantes y versiones relacionadas

| Dispositivo | VCC | Caps bomba | Tasa máx. | ESD (HBM) | Comentarios |
|---|---:|---:|---:|---:|---|
| **MAX232** | 5 V | **1 µF** | **120 kbit/s** | **≈ 2 kV** | Base, 2TX+2RX. |
| **MAX232A / MAX202** | 5 V | **0.1 µF** | **~200 kbit/s** | — | Misma función; menores capacitores, mayor bitrate. |
| **MAX232E** | 5 V | **1 µF** | **hasta 250 kbit/s** | **±15 kV** | Protección ESD para entornos severos. |
| **MAX3232** | **3.0–5.5 V** | **0.1 µF** | **hasta 250 kbit/s** | **±15 kV** | Alternativa para **MCUs a 3.3 V**; pin-compatible con MAX232. |

> **Nota**: los nombres pueden variar según fabricante (TI/ADI). Revise siempre el datasheet específico.

---

## 7. ¿Se sigue usando hoy? Aplicaciones reales

**Sí.** Aunque USB y Ethernet dominan el usuario final, **RS-232** sigue presente en:
- **Consolas de servicio** (routers/switches, equipos de telecom).  
- **Instrumentación y laboratorio**, **PLC/CNC** legados, HMI antiguas.  
- **Embebidos industriales**, POS y **retro-computación**.  
Para MCUs a **3.3 V**, se prefiere **MAX3232** (misma topología, VCC 3.0–5.5 V).

---

## 8. Ventajas y desventajas

**Ventajas**
- Una sola fuente **+5 V** (o **3.3–5.5 V** en MAX3232) gracias a la **bomba de carga**.  
- **Robusto**: entradas **±30 V**, buenas opciones de **ESD** (versiones E).  
- **Sencillo y económico**: solo **4 capacitores** externos.

**Desventajas**
- **Velocidad** moderada frente a interfaces modernas (**120–250 kbps**).  
- La **bomba de carga** puede introducir **rizado/EMI** si se eligen mal los capacitores o el ruteo.  
- Conectores **DB9/DB25** grandes; RS-485/422 es preferible para largas distancias.

---

## 9. Buenas prácticas de diseño

- Colocar **C1–C4** **muy cerca** de sus pines y con **retornos cortos** a GND.  
- **Bypass** en VCC: **0.1 µF** + **granel** (1–10 µF).  
- **MAX232**: **1 µF** en C1–C4; **MAX232A/MAX202**: **0.1 µF**; **MAX3232**: **0.1 µF**.  
- Usar cerámicos **X7R**; verificar tolerancias si hay sensibilidad a rizado/EMI.

---

## 10. Ejemplo de uso rápido

**Objetivo**: conectar un **MCU (UART TTL 5 V)** a un **puerto RS-232 DB9**.

1) **VCC=5 V** al pin **16** y **GND** al pin **15**.  
2) **C1–C4 = 1 µF** entre (1–3), (4–5), (2–GND) y (6–GND). Bypass **0.1 µF** en **VCC–GND**.  
3) **UART→RS-232**: **T1IN (11)** → UART TX; **T1OUT (14)** → DB9 *TX*.  
4) **RS-232→UART**: **R1IN (13)** ← DB9 *RX*; **R1OUT (12)** → UART RX.  
5) Configurar UART (p.ej. **9600 8N1**) y probar **loopback** uniendo **T1OUT↔R1IN**.

---

## 11. Referencias

- **Texas Instruments – MAX232 (datasheet)**: https://www.ti.com/lit/gpn/MAX232  
- **Texas Instruments – MAX232E (datasheet)**: https://www.ti.com/lit/gpn/MAX232E  
- **Texas Instruments – MAX3232 (datasheet)**: https://www.ti.com/lit/gpn/MAX3232  
- **Analog Devices (Maxim) – MAX232**: https://www.analog.com/en/products/max232.html  
- **Analog Devices (Maxim) – MAX3232 (familia)**: https://www.analog.com/media/en/technical-documentation/data-sheets/max3222-max3241.pdf


