# Taller 2 – Comunicaciones Industriales

Este repositorio contiene un resumen estructurado del **Taller 2**, enfocado en conceptos base de **ASCII** y **RS-232** (conectores DB9/DB25 y formato de trama). El contenido se organiza para consulta rápida y uso en laboratorio o estudio.

---

## Índice
- [1. Código ASCII: historia, funcionamiento y descripción](#1-código-ascii-historia-funcionamiento-y-descripción)
  - [1.1. ¿Qué es?](#11-qué-es)
  - [1.2. ¿Cómo funciona?](#12-cómo-funciona)
  - [1.3. Importancia](#13-importancia)
  - [1.4. Tabla parcial de referencia](#14-tabla-parcial-de-referencia)
- [2. RS-232: conectores DB9 y DB25](#2-rs232-conectores-db9-y-db25)
  - [2.1. Señales típicas en DB9](#21-señales-típicas-en-db9)
  - [2.2. Señales típicas en DB25](#22-señales-típicas-en-db25)
- [3. RS-232: formato de la trama](#3-rs232-formato-de-la-trama)
  - [3.1. Estructura](#31-estructura)
  - [3.2. Diagrama (ASCII)](#32-diagrama-ascii)
- [Cómo usar este README](#cómo-usar-este-readme)

---

## 1. Código ASCII: historia, funcionamiento y descripción

### 1.1. ¿Qué es?
**ASCII** (*American Standard Code for Information Interchange*) es un **sistema de codificación de caracteres** creado en **1963** por el comité **ANSI** para **unificar** la representación de letras, números y símbolos en computadoras.

### 1.2. ¿Cómo funciona?
ASCII **asigna un número entero** a cada carácter y se **representa en binario** (históricamente 7 bits; hoy suele almacenarse en 8 bits). Ejemplos:
- **A** → 65
- **espacio** → 32
- **0** (cero) → 48

### 1.3. Importancia
Fue la **base de la comunicación entre computadoras** y aún es clave en protocolos, archivos de texto, terminales y equipos industriales legados.

### 1.4. Tabla parcial de referencia
| Carácter | Decimal | Binario (8 bits) |
|---|---:|---|
| (espacio) | 32 | 0010 0000 |
| 0 | 48 | 0011 0000 |
| 1 | 49 | 0011 0001 |
| 2 | 50 | 0011 0010 |
| A | 65 | 0100 0001 |
| B | 66 | 0100 0010 |
| C | 67 | 0100 0011 |
| a | 97 | 0110 0001 |
| b | 98 | 0110 0010 |
| c | 99 | 0110 0011 |

> *La tabla completa incluye letras, dígitos, signos de puntuación y caracteres de control.*

---

## 2. RS-232: conectores DB9 y DB25

### 2.1. Señales típicas en DB9
El estándar RS-232 usa con frecuencia el conector **DB9**. Señales comunes (rol DTE típico):

| Pin | Señal | Descripción breve |
|---:|---|---|
| 1 | **DCD** | *Data Carrier Detect* |
| 2 | **RXD** | *Receive Data* |
| 3 | **TXD** | *Transmit Data* |
| 4 | **DTR** | *Data Terminal Ready* |
| 5 | **GND** | Tierra/señal |
| 6 | **DSR** | *Data Set Ready* |
| 7 | **RTS** | *Request To Send* |
| 8 | **CTS** | *Clear To Send* |
| 9 | **RI** | *Ring Indicator* |

> *Las señales listadas coinciden con las presentadas en el documento (DCD, RXD, TXD, DTR, GND, DSR, RTS, CTS, RI). La asignación de pines mostrada es la utilizada habitualmente para DTE.*

### 2.2. Señales típicas en DB25
Para **DB25**, el documento destaca principalmente: **GND, TXD, RXD, RTS, CTS, DSR, DCD, DTR, RI**. En aplicaciones RS-232 clásicas, estos son los más usados.

| Señal | Descripción breve |
|---|---|
| **GND** | Tierra/señal |
| **TXD** | Transmisión de datos |
| **RXD** | Recepción de datos |
| **RTS** | Solicitud para enviar |
| **CTS** | Listo para enviar |
| **DSR** | Equipo listo |
| **DCD** | Portadora detectada |
| **DTR** | Terminal listo |
| **RI** | Indicador de llamada |

> *El documento indica que el resto de pines pueden ser opcionales o reservados según dispositivo.*

---

## 3. RS-232: formato de la trama

### 3.1. Estructura
Una **trama RS-232** transmite un carácter por vez con la siguiente estructura general:
1. **Bit de inicio (Start)**: siempre **0**, marca el comienzo.
2. **Bits de datos**: típicamente **5–8 bits** (por ejemplo, el código ASCII).
3. **Bit de paridad (opcional)**: verificación simple de errores (**par** o **impar**, entre otras opciones).
4. **Bits de parada (Stop)**: **1** o más bits en **1** para indicar el final del carácter.

### 3.2. Diagrama (ASCII)
```
Línea:   ──────┐┌─────────────── Datos (5–8 bits) ────────────────┐┌──────
Nivel:        0 1 1 1 0 0 1 0 1 0 1 0  (ejemplo)                    1
            Start     D0 D1 D2 D3 D4 D5 D6 D7      Paridad?       Stop
```

---

## Cómo usar este README
- Copia este archivo como `README.md` en la raíz de tu repositorio de GitHub.
- Si vas a documentar prácticas de laboratorio, crea una carpeta `assets/` para diagramas, fotografías de cableado y capturas de terminal.
- Complementa con ejercicios: convertir texto a ASCII, configurar parámetros 8N1 (8 bits, sin paridad, 1 stop), y pruebas de loopback.
