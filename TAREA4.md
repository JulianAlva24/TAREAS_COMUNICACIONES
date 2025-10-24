# Tarea 4 — Comunicaciones Industriales

**Autores:** Daniel Felipe Pinilla Daza · Julian Sebastian Alvarado Monroy  
**Asignatura:** Comunicaciones Industriales 

---

## Descripción general

Este repositorio documenta, de forma sintética y estructurada, la **Tarea 4 de Comunicaciones Industriales**, cuyo objetivo es revisar protocolos y tecnologías de automatización usados en la industria (MODBUS, AS‑Interface, PROFIBUS/PROFINET, Ethernet/RS‑485), y presentar una **comparación técnica entre IPv4 e IPv6** con énfasis en ventajas, mecanismos de transición e ideas de implementación.

> **Alcance**: resumen técnico de los temas tratados, puntos clave para estudio, y referencias principales. Para el desarrollo completo (figuras y descripciones ampliadas), ver el PDF base.

---

## Contenido

- [1. Vigilancia tecnológica de protocolos industriales](#1-vigilancia-tecnológica-de-protocolos-industriales)  
  - [1.1 MODBUS](#11-modbus)  
  - [1.2 AS‑Interface (AS‑i)](#12-as-interface-as-i)  
  - [1.3 Ethernet industrial (EtherNet/IP, EtherCAT, POWERLINK, TSN)](#13-ethernet-industrial-ethernetip-ethercat-powerlink-tsn)
- [2. Dispositivos y protocolos en la universidad](#2-dispositivos-y-protocolos-en-la-universidad)  
  - [2.1 MODBUS](#21-modbus) · [2.2 AS‑i](#22-as-i) · [2.3 PROFIBUS](#23-profibus) · [2.4 PROFINET](#24-profinet) · [2.5 Ethernet](#25-ethernet) · [2.6 RS‑485](#26-rs-485)
- [3. IPv4 e IPv6: características y diferencias](#3-ipv4-e-ipv6-características-y-diferencias)  
  - [3.1 IPv4](#31-ipv4) · [3.2 IPv6](#32-ipv6) · [3.3 Comparación](#33-comparación-ipv4-vs-ipv6) · [3.4 Ventajas de IPv6](#34-ventajas-de-ipv6) · [3.5 Mecanismos de transición](#35-mecanismos-de-transición) · [3.6 Implementación](#36-implementación)
- [4. Referencias bibliográficas](#4-referencias-bibliográficas)

---

## 1. Vigilancia tecnológica de protocolos industriales

### 1.1 MODBUS
- **Modelo maestro–esclavo** (1979, Modicon/Schneider); variantes: **RTU** (binario), **ASCII** y **Modbus TCP** (puerto 502).
- Uso extendido en **PLCs, SCADA, medidores de energía, variadores** y dispositivos de automatización.
- Tendencias: integración en **IoT industrial**, evolución a **Modbus Secure** (mejoras de ciberseguridad), aplicaciones en **energías renovables, edificios inteligentes** y **mantenimiento predictivo**.

### 1.2 AS‑Interface (AS‑i)
- **Bus de 2 hilos** (24 V DC + datos), orientado a **sensores/actuadores simples**.
- **AS‑i 3.0**: hasta **62 esclavos/segmento**, **167 kbps**, **tiempo de ciclo ≈ 5 ms**, distancias típicas **100–300 m**.
- **AS‑i Safety at Work** (SIL 3, IEC 61508) integra funciones de seguridad en el mismo bus.
- Tendencias: **sensores inteligentes** de bajo costo, **reducción de cableado**, compatibilidad con **Industria 4.0** y líneas flexibles.

### 1.3 Ethernet industrial (EtherNet/IP, EtherCAT, POWERLINK, TSN)
- **EtherNet/IP (CIP sobre TCP/IP)**: adopción amplia; perfiles para **tiempo real** y sincronización precisa.
- **EtherCAT**: procesamiento *on‑the‑fly* con **latencias del orden de decenas de µs**; muy usado en **motion** y **robótica**.
- **POWERLINK**: abierto, **determinismo estricto**, aplicado en **maquinaria de alta precisión**.
- **TSN (IEEE 802.1)**: Ethernet determinista con **sincronización** y **convergencia OT/IT**; clave para **Industria 4.0** y **5G industrial**.

---

## 2. Dispositivos y protocolos en la universidad

### 2.1 MODBUS
- **Hasta 247 esclavos** (en serial), **9600–115200 bps**; funciones de lectura/escritura de *coils* y registros; verificación **CRC‑16** (RTU) / **LRC** (ASCII).
- Dispositivos típicos: **PLCs (Allen‑Bradley, Siemens, Schneider), medidores, VFDs, SCADA**.

### 2.2 AS‑i
- Cable **2 hilos**, **62 esclavos**, **167 kbps**, **5 ms** de ciclo; **SIL 3** con Safety at Work.
- Dispositivos típicos: **sensores discretos, fotocélulas, pulsadores, electroválvulas, balizas**.

### 2.3 PROFIBUS
- Estándar **DIN 19245** (años 80). Arquitectura **multi‑maestro con *token***.
- Variantes: **DP** (fabricación, RS‑485, **9.6 kbps–12 Mbps**) y **PA** (procesos, **MBP‑IS**).
- Hasta **126 nodos/segmento**; terminaciones y reglas de bus RS‑485.

### 2.4 PROFINET
- Evolución Ethernet (IEC 61158/61784). Clases: **TCP/IP**, **RT**, **IRT**.
- **100 Mbps/1 Gbps**, **topología flexible con switches**, **MRP** (redundancia), **PROFISAFE** (seguridad).
- Ecosistema: **Siemens S7‑1200/1500, HMIs, drives Sinamics, robots, switches SCALANCE**.

### 2.5 Ethernet
- IEEE **802.3**; **10/100/1000/10G** (y superiores), **full‑duplex**, cobre **UTP** o **fibra**.
- Backbone común para **celdas de manufactura, DCS y cámaras IP**.

### 2.6 RS‑485
- Capa física diferencial **TIA/EIA‑485** (1983). **Bus lineal** con terminaciones **120 Ω**.
- **Hasta 32 nodos** (extensible), **hasta 10 Mbps** (cortas), **≈1200 m** a **100 kbps**. **Alta inmunidad al ruido**.

---

## 3. IPv4 e IPv6: características y diferencias

### 3.1 IPv4
- **32 bits** (notación decimal, p. ej. 192.168.1.1); clases A/B/C y rangos privados **RFC 1918**.
- Fragmentación en **hosts y routers**; **checksum** en encabezado; **IPSec opcional**.
- Direcciones especiales: **loopback 127.0.0.1**, **broadcast 255.255.255.255**.

### 3.2 IPv6
- **128 bits** (notación hexadecimal, p. ej. 2001:db8::1); encabezado **fijo (40 B)**.
- Tipos: **Global Unicast, Link‑Local (fe80::/10), ULA (fc00::/7), Multicast (ff00::/8), Anycast**.
- **SLAAC/DHCPv6**, **sin checksum**, **fragmentación solo en el host origen**, **NDP** en lugar de ARP, **IPSec en la especificación**.

### 3.3 Comparación IPv4 vs IPv6

| Característica      | IPv4                           | IPv6                              |
|---------------------|--------------------------------|-----------------------------------|
| Longitud dirección  | 32 bits                        | 128 bits                          |
| Encabezado          | Variable (20–60 B)             | Fijo (40 B)                       |
| Broadcast           | Sí                              | No (usa Multicast)                |
| Autoconfiguración   | DHCP/manual                     | SLAAC/DHCPv6/manual               |
| Fragmentación       | Routers y hosts                 | Solo host origen                  |
| Checksum            | Sí                              | No                                |
| Seguridad (IPSec)   | Opcional                        | Incluida en la especificación     |
| NAT                 | Común                           | En principio innecesario          |
| Resolución de capa 2| ARP                             | NDP (ICMPv6)                      |
| MTU mínimo          | 576 B                           | 1280 B                            |

### 3.4 Ventajas de IPv6
- **Espacio masivo** para IoT; **elimina NAT** y facilita **conectividad extremo‑a‑extremo**.
- **Autoconfiguración** (SLAAC), **mejoras de rendimiento** por encabezado fijo y **multicast eficiente**.
- **Seguridad y movilidad** contempladas desde el diseño (MIPv6).

### 3.5 Mecanismos de transición
- **Dual‑Stack**: coexistencia IPv4/IPv6 (máxima compatibilidad).  
- **Túneles (Tunneling)**: 6in4 (manual), 6to4 (automático, 2002::/16), **Teredo** (UDP a través de NAT).  
- **Traducción**: **NAT64/DNS64** (clientes IPv6 → servidores IPv4), **464XLAT** (apps IPv4 en redes IPv6).

### 3.6 Implementación
- **Planificación**: obtención de prefijos (/48, /56), **subred /64** por segmento.  
- **Infraestructura**: compatibilidad de equipos, firmware actualizado, **dual‑stack** donde sea viable.  
- **Seguridad**: *hardening* de firewalls, filtrado ICMPv6, mitigación de ataques específicos.  
- **Adopción**: crecimiento sostenido; se proyecta dominio de IPv6 en los próximos años.

---

## 4. Referencias bibliográficas

- AS‑International Association (2023). *AS‑Interface: The Automation Solution.*  
- Bolton, W. (2015). *Programmable Logic Controllers (6th ed.).* Newnes.  
- Deering, S., & Hinden, R. (1998/2017). **RFC 2460 / RFC 8200** – *Internet Protocol, Version 6 Specification.*  
- Felser, M. (2010). *Real‑Time Ethernet Industry Prospective.* Proceedings of the IEEE, 93(6).  
- IEEE Standards Association (2018). **IEEE 802.3 Ethernet Standard.**  
- MODBUS Organization (2012). *MODBUS Application Protocol Specification V1.1b3.*  
- Postel, J. (1981). **RFC 791** – *Internet Protocol.*  
- PROFIBUS & PROFINET International (2020/2021). *PROFIBUS Technology and Application / PROFINET System Description.*  
- RFC 1918 (1996). *Address Allocation for Private Internets.*  
- RFC 3056 (2001). *Connection of IPv6 Domains via IPv4 Clouds.*  
- RFC 4380 (2006). *Teredo: Tunneling IPv6 over UDP through NATs.*  
- Tanenbaum, A., & Wetherall, D. (2011). *Computer Networks (5th ed.).* Pearson.  
- Zurawski, R. (2014). *Industrial Communication Technology Handbook (2nd ed.).* CRC Press.


