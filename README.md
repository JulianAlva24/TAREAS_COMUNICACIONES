# Tarea 1 – Comunicaciones Industriales

Este repositorio contiene un resumen estructurado de los sensores disponibles en los laboratorios de la Santoto, con sus características principales, tipos de señal, rangos de medición (cuando aplican) y aplicaciones típicas. El contenido se basa en el documento **“Tarea 1 Comunicaciones Industriales”** suministrado por el usuario.

---

## Índice
- [Inventario de sensores](#inventario-de-sensores)
  - [Sensor magnético para cilindro neumático](#sensor-magnético-para-cilindro-neumático)
  - [Sensor de sonda de temperatura (Termopar)](#sensor-de-sonda-de-temperatura-termopar)
  - [Termómetro infrarrojo (Extech IR100)](#termómetro-infrarrojo-extech-ir100)
  - [Luxómetro digital](#luxómetro-digital)
  - [Sensor capacitivo](#sensor-capacitivo)
  - [Sensor inductivo](#sensor-inductivo)
  - [Sensor de temperatura Pt100 (RTD)](#sensor-de-temperatura-pt100-rtd)
  - [Sensor de presión de aire](#sensor-de-presión-de-aire)
  - [Sensor fotoeléctrico](#sensor-fotoeléctrico)
- [Resumen comparativo](#resumen-comparativo)
- [Referencias](#referencias)

---

## Inventario de sensores

### Sensor magnético para cilindro neumático
**Descripción.** Sensor de proximidad que detecta la posición del pistón dentro de un cilindro neumático gracias al imán incrustado en el pistón. Al pasar cerca, el campo magnético activa el sensor.  
**Tipo de señal.** Digital (ON/OFF). Puede ser de tipo *reed switch* (contacto magnético) o de efecto Hall (electrónico).  
**Aplicaciones.** Detección de posición en cilindros neumáticos, control de procesos automatizados y funciones de seguridad en sistemas de movimiento.

---

### Sensor de sonda de temperatura (Termopar)
**Descripción.** Conjunto de dos metales distintos unidos en un extremo; al variar la temperatura, se genera un voltaje proporcional. Es muy usado por su amplio rango y resistencia a altas temperaturas.  
**Tipo de señal.** Analógica (mV), requiere acondicionamiento o módulo de adquisición. Existen varios tipos (K, J, T, etc.); el **Tipo K** es común.  
**Rango típico (Tipo K).** −200 °C a 1350 °C.  
**Aplicaciones.** Control de procesos industriales, hornos y calderas, y laboratorios de pruebas térmicas.

---

### Termómetro infrarrojo (Extech IR100)
**Descripción.** Mide temperatura a distancia (sin contacto) detectando la radiación infrarroja de la superficie. Portátil y práctico para mediciones rápidas en superficies donde no es posible colocar sensores de contacto.  
**Rango de medición.** −34 °C a 230 °C (−29 °F a 446 °F).  
**Características.** Medición sin contacto, diseño compacto y cobertura de más del 90% de aplicaciones de superficie.  
**Aplicaciones.** Detección de puntos calientes en tableros eléctricos, monitoreo de procesos y control de temperatura de objetos en movimiento o de difícil acceso.

---

### Luxómetro digital
**Descripción.** Instrumento para medir iluminancia (lux) sobre una superficie, con fotodiodo/celda fotoeléctrica que convierte luz en señal eléctrica proporcional.  
**Rango típico.** Desde 0 lux (oscuridad total) hasta 200 000 lux o más (luz solar intensa).  
**Aplicaciones.** Verificación de niveles de iluminación en interiores/exteriores, cumplimiento de normas en espacios de trabajo, control en laboratorios, fotografía y horticultura.

---

### Sensor capacitivo
**Descripción.** Sensor de proximidad que detecta objetos **metálicos y no metálicos** (madera, vidrio, plástico, líquidos, etc.) por variación de capacitancia al acercarse a la superficie activa.  
**Tipo de señal.** Usualmente digital (ON/OFF); algunos modelos ofrecen salida analógica.  
**Rango típico.** Milímetros a varios centímetros (según modelo).  
**Aplicaciones.** Detección de nivel de líquidos y sólidos; sensado de objetos no metálicos; automatización industrial y control.

---

### Sensor inductivo
**Descripción.** Sensor de proximidad para detección **sin contacto** de objetos **metálicos** mediante un campo electromagnético generado por una bobina interna; al ingresar un metal, cambia la inductancia y se activa la salida.  
**Tipo de señal.** Generalmente digital (ON/OFF); algunos modelos avanzados ofrecen analógica.  
**Rango típico.** 1 mm a 60 mm (según tamaño y tipo de metal).  
**Aplicaciones.** Detección y conteo de piezas metálicas, posicionamiento, automatización y robótica.

---

### Sensor de temperatura Pt100 (RTD)
**Descripción.** Detector de temperatura por resistencia (RTD) de platino. Su resistencia varía con la temperatura; “100” indica 100 Ω a 0 °C.  
**Características.** Alta precisión y estabilidad a largo plazo; buena linealidad. Requiere acondicionamiento (p. ej., puente de Wheatstone o transmisor 4–20 mA).  
**Rango típico.** −200 °C a +850 °C.  
**Aplicaciones.** Control de procesos, medición en hornos/reactores/Sistemas HVAC, laboratorios y calibración.

---

### Sensor de presión de aire
**Descripción.** Mide presión relativa o absoluta en sistemas neumáticos, convirtiendo la fuerza ejercida por el aire en señal eléctrica proporcional.  
**Tipo de señal.** Analógica (0–5 V, 0–10 V o 4–20 mA); algunos modelos entregan salida digital (I²C, SPI).  
**Rango típico.** Desde pocos milibares hasta varios bares (según modelo).  
**Aplicaciones.** Monitoreo y control en neumática, manufactura, compresores, válvulas y líneas de aire.

---

### Sensor fotoeléctrico
**Descripción.** Detecta presencia/ausencia de objetos mediante un haz de luz (IR o láser). El emisor envía un rayo y el receptor lo recibe; la interrupción o reflexión del rayo permite detectar el objeto.  
**Tipos principales.**
- **Barreras (Through-beam):** emisor y receptor separados.  
- **Reflexión con espejo (Retro-reflective):** el haz rebota en un reflector.  
- **Reflexión difusa (Diffuse):** el objeto refleja la luz hacia el receptor.  
**Tipo de señal.** Usualmente digital (ON/OFF); algunos modelos con salida analógica.  
**Aplicaciones.** Detección y conteo en bandas transportadoras, automatización y sistemas de seguridad.

---

## Resumen comparativo

| Sensor | Naturaleza de la medición | Tipo de señal | Rango típico (cuando aplica) | Usos comunes |
|---|---|---|---|---|
| Magnético para cilindro | Proximidad/posición de pistón | Digital ON/OFF | — | Posición en cilindros, seguridad |
| Termopar (Tipo K) | Temperatura (contacto) | Analógica (mV) | −200 °C a 1350 °C | Hornos, procesos, laboratorio |
| IR Extech IR100 | Temperatura (sin contacto) | — | −34 °C a 230 °C | Tableros, objetos en movimiento |
| Luxómetro | Iluminancia (luz) | — | 0 a 200 000+ lux | Iluminación interior/exterior |
| Capacitivo | Proximidad (no metálicos y metálicos) | Digital / Analógica | mm a cm | Nivel de líquidos/sólidos, automatización |
| Inductivo | Proximidad (metales) | Digital / Analógica | 1 a 60 mm | Conteo, posicionamiento, robótica |
| Pt100 (RTD) | Temperatura (contacto) | Analógica (medición de resistencia) | −200 °C a +850 °C | Procesos, HVAC, calibración |
| Presión de aire | Presión neumática | Analógica / Digital | mbar a bar (según modelo) | Neumática, compresores, válvulas |
| Fotoeléctrico | Presencia/ausencia por luz | Digital / Analógica | — | Bandas, conteo, seguridad |

> **Nota.** Los rangos “típicos” pueden variar según fabricante/modelo.

---

## Referencias

1. Festo, *Sensores magnéticos para cilindros*. Disponible en: https://www.festo.com/entry/es-co/sensores-magneticos-para-cilindros-id_gb/  
2. Omega Engineering, *Principios de los termopares*. Disponible en: https://mx.omega.com/prodinfo/termopares.html  
3. Extech Instruments, *IR100: Pocket IR Thermometer*. Disponible en: https://www.extech.com/products/ir100  
4. Testo, *Medición de iluminación*. Disponible en: https://www.testo.com/es-ES/aplicaciones/medicion-de-iluminacion  
5. IFM Electronic, *Sensores capacitivos*. Disponible en: https://www.ifm.com/co/es/co/category/010/010_020/010_020_010  
6. IFM Electronic, *Sensores inductivos*. Disponible en: https://www.ifm.com/co/es/co/category/010/010_010/010_010_010  
7. Omega Engineering, *RTD Sensors (PT100)*. Disponible en: https://mx.omega.com/prodinfo/rtd.html  
8. Honeywell, *Pressure Sensors*. Disponible en: https://sps.honeywell.com/us/en/products/sensors-and-switches/pressure-sensors  
9. Omron Industrial Automation, *Photoelectric Sensors*. Disponible en: https://industrial.omron.mx/es/products/category/sensors/photoelectric-sensors

---

> **Cómo usar este README**  
> - Copia este archivo como `README.md` en la raíz de tu repositorio de GitHub.  
> - Si deseas añadir imágenes/esquemáticos específicos de cada sensor, crea una carpeta `assets/` y enlázalas desde cada sección con Markdown.

