
# CISCO NETWORKING BASICS
## MÓDULO 6 — MEDIOS DE RED

**Objetivo:** Identificar los principales medios de transmisión utilizados en redes y comprender sus características, funcionamiento y aplicaciones.

---

# 6.1 — TIPOS DE MEDIOS DE RED

## 6.1.1 — ¿Qué es un medio de red?

Un **medio de red** es el canal por el cual viajan los datos desde un dispositivo de origen hasta un dispositivo de destino.

Los medios permiten transportar señales utilizadas para comunicar los dispositivos de una red.

**Ejemplo:**

PC → Cable Ethernet → Switch

En este ejemplo, el cable Ethernet es el medio de transmisión.

---

## 6.1.2 — TRES TIPOS DE MEDIOS

Cisco clasifica los medios de red en tres categorías principales.

### 1. Hilos metálicos dentro de cables

Los datos se transmiten mediante **impulsos eléctricos** que viajan por conductores metálicos.

**Ejemplos:**
- Cable de par trenzado.
- Cable coaxial.

### 2. Fibra óptica

Los datos se transmiten mediante **pulsos de luz** que viajan por fibras de vidrio o plástico.

**Ejemplo:** conexiones de fibra óptica utilizadas en redes troncales.

### 3. Transmisión inalámbrica

Los datos se transmiten mediante **ondas electromagnéticas** que se modulan para representar información.

**Ejemplo:** Wi-Fi.

### Comparación

| Medio | Señal utilizada | Ejemplo |
|---|---|---|
| Cobre | Impulsos eléctricos | Cable Ethernet |
| Fibra óptica | Pulsos de luz | Enlace de fibra |
| Inalámbrico | Ondas electromagnéticas | Wi-Fi |

**PARA RECORDAR:**

- Cobre → electricidad.
- Fibra óptica → luz.
- Inalámbrico → ondas electromagnéticas.

---

## ¿CÓMO ELEGIR UN MEDIO DE RED?

Cisco presenta cuatro criterios principales para seleccionar un medio.

### 1. Distancia

¿Cuál es la distancia máxima a la que el medio puede transportar una señal correctamente?

### 2. Entorno

¿Dónde se instalará el medio?

Se deben considerar las condiciones físicas y ambientales del lugar.

### 3. Cantidad de datos y velocidad

¿Cuántos datos se deben transmitir y qué velocidad necesita la comunicación?

### 4. Costo

¿Cuánto costará instalar el medio de transmisión?

**Ejemplo:**

Si una empresa necesita conectar edificios separados por una gran distancia y transmitir muchos datos, la fibra óptica puede ser una opción adecuada.

**IMPORTANTE:**

No se debe elegir un medio únicamente por su velocidad. También deben evaluarse la distancia, el entorno y el costo.

---

## 6.1.3 — CABLES DE RED COMUNES

Los tres cables de red más comunes presentados por Cisco son:

1. Cable de par trenzado.
2. Cable coaxial.
3. Cable de fibra óptica.

---

### 1. Cable de par trenzado

El **cable de par trenzado** es uno de los medios más utilizados en redes LAN Ethernet.

Está formado por conductores agrupados en pares que se encuentran trenzados.

### ¿Por qué están trenzados?

Los conductores se trenzan para ayudar a reducir las interferencias eléctricas.

Los hilos tienen colores que permiten identificar correctamente cada conductor en los extremos del cable.

Generalmente, cada par tiene:
- Un hilo de color sólido.
- Un hilo blanco con una franja del mismo color.

### ¿Dónde se utiliza?

Principalmente en:
- Redes LAN.
- Conexiones de computadoras.
- Conexiones entre dispositivos Ethernet.

**Ejemplo:**

Computadora → Cable de par trenzado → Switch

**IMPORTANTE:**

Ethernet utiliza frecuentemente cable de par trenzado para comunicar dispositivos dentro de una red local.

---

### 2. Cable coaxial

El **cable coaxial** es un medio de transmisión formado por un conductor central rodeado por material aislante y blindaje conductor.

### Estructura

1. Núcleo conductor de cobre.
2. Capa aislante.
3. Blindaje metálico.
4. Cubierta protectora exterior.

### ¿Cómo funciona?

Los datos se transmiten mediante señales eléctricas a través del cable.

Su estructura permite transportar señales de alta frecuencia.

### ¿Dónde se utiliza?

- Redes de televisión por cable.
- Conexiones de Internet por cable.
- Sistemas de comunicación satelital.

**Ejemplo:**

Proveedor de Internet → Cable coaxial → Cable módem

**PARA RECORDAR:**

El coaxial posee un conductor central y un blindaje que ayuda a proteger la señal.

---

### 3. Cable de fibra óptica

La **fibra óptica** es un medio que transmite información mediante pulsos de luz.

Puede estar fabricada con vidrio o plástico.

Las fibras son muy delgadas, con diámetros comparables al de un cabello humano.

### ¿Cómo funciona?

1. Un transmisor genera señales luminosas.
2. Los pulsos de luz viajan por la fibra.
3. Un receptor detecta las señales luminosas.
4. La información se recupera para su procesamiento.

### Ventajas

- Gran capacidad de transmisión.
- Permite enviar datos a grandes distancias.
- No se ve afectada por interferencias electromagnéticas.
- Puede transportar grandes cantidades de información.

### ¿Dónde se utiliza?

- Redes troncales.
- Grandes empresas.
- Centros de datos.
- Redes de telecomunicaciones.
- Conexiones de larga distancia.

También se utiliza en aplicaciones médicas e inspecciones industriales.

**Ejemplo:**

Centro de datos A → Fibra óptica → Centro de datos B

**IMPORTANTE:**

La fibra óptica utiliza luz en lugar de señales eléctricas para transportar información a través de la fibra.

---

# COMPARACIÓN DE LOS TRES CABLES

| Característica | Par trenzado | Coaxial | Fibra óptica |
|---|---|---|---|
| Señal | Eléctrica | Eléctrica | Luz |
| Material principal | Conductores metálicos | Conductor central y blindaje | Vidrio o plástico |
| Uso común | Redes LAN Ethernet | TV e Internet por cable | Redes troncales |
| Interferencias eléctricas | Pueden afectarlo | El blindaje ayuda a reducirlas | No afectan la señal óptica |
| Distancia | Depende de la tecnología | Depende de la tecnología | Adecuada para grandes distancias |

---

# GLOSARIO — MÓDULO 6

| Término | Significado |
|---|---|
| Medio de red | Canal utilizado para transmitir señales. |
| Par trenzado | Cable formado por pares de conductores trenzados. |
| Coaxial | Cable con conductor central y blindaje. |
| Fibra óptica | Medio de transmisión basado en pulsos de luz. |
| Ethernet | Tecnología utilizada en redes LAN. |
| Interferencia | Alteración que puede afectar la transmisión de señales. |
| Señal eléctrica | Variación eléctrica utilizada para transportar información. |
| Señal óptica | Luz utilizada para transportar información. |
| Señal inalámbrica | Onda electromagnética utilizada para transmitir información. |
| Red troncal | Infraestructura de alta capacidad que conecta redes importantes. |

---

# RESUMEN GENERAL — MÓDULO 6

1. Los medios de red transportan información entre dispositivos.
2. Existen tres categorías principales: cobre, fibra óptica e inalámbrico.
3. Los cables metálicos utilizan señales eléctricas.
4. La fibra óptica utiliza pulsos de luz.
5. Las conexiones inalámbricas utilizan ondas electromagnéticas.
6. La elección del medio depende de la distancia, el entorno, la velocidad requerida y el costo.
7. Los cables más comunes son par trenzado, coaxial y fibra óptica.
8. El par trenzado se utiliza frecuentemente en redes LAN Ethernet.
9. El trenzado de los conductores ayuda a reducir las interferencias.
10. El coaxial contiene un conductor central, material aislante y blindaje.
11. La fibra óptica permite transportar grandes cantidades de información a largas distancias.
12. Las interferencias electromagnéticas no afectan la señal óptica dentro de la fibra.

**IDEA CLAVE:**

El medio de red se selecciona considerando las necesidades de comunicación, el entorno, la distancia, la capacidad de transmisión y el costo.

---

# CUESTIONARIO — MÓDULO 6

**Total:** 10 preguntas
**Puntaje máximo:** 10 puntos

**Instrucciones:** Marca la respuesta correcta. Algunas preguntas tienen varias respuestas válidas.

## PREGUNTA 1

¿Qué medio de red transmite información mediante pulsos de luz?

- [ ] A. Cable coaxial.
- [ ] B. Cable de par trenzado.
- [ ] C. Fibra óptica.
- [ ] D. Transmisión por radio.

## PREGUNTA 2

¿Cuáles son las tres categorías principales de medios de red? (Selecciona tres).

- [ ] A. Hilos metálicos dentro de cables.
- [ ] B. Fibras de vidrio o plástico.
- [ ] C. Transmisión inalámbrica.
- [ ] D. Servidores y routers.

## PREGUNTA 3

¿Por qué los conductores del cable de par trenzado están agrupados en pares trenzados?

- [ ] A. Para aumentar el peso del cable.
- [ ] B. Para reducir las interferencias eléctricas.
- [ ] C. Para transmitir pulsos de luz.
- [ ] D. Para reemplazar los dispositivos de red.

## PREGUNTA 4

¿Qué tipo de cable contiene un conductor central rodeado por material aislante y blindaje metálico?

- [ ] A. Fibra óptica.
- [ ] B. Cable coaxial.
- [ ] C. Cable de par trenzado.
- [ ] D. Cable de fibra plástica.

## PREGUNTA 5

¿Qué medio de transmisión se utiliza comúnmente en las redes LAN Ethernet?

- [ ] A. Cable de par trenzado.
- [ ] B. Cable de fibra óptica exclusivamente.
- [ ] C. Enlaces satelitales.
- [ ] D. Ondas infrarrojas exclusivamente.

## PREGUNTA 6

¿Cuáles son criterios utilizados para seleccionar un medio de red? (Selecciona tres).

- [ ] A. Distancia máxima de transmisión.
- [ ] B. Entorno de instalación.
- [ ] C. Cantidad de datos y velocidad requerida.
- [ ] D. Color del gabinete del router.

## PREGUNTA 7

Una empresa necesita transmitir grandes cantidades de datos a largas distancias y evitar interferencias eléctricas. ¿Qué medio sería el más adecuado?

- [ ] A. Cable coaxial.
- [ ] B. Cable de par trenzado.
- [ ] C. Fibra óptica.
- [ ] D. Cable telefónico convencional.

## PREGUNTA 8

¿Qué tecnología permite transmitir datos utilizando ondas electromagnéticas a través del aire?

- [ ] A. Fibra óptica.
- [ ] B. Cable coaxial.
- [ ] C. Par trenzado.
- [ ] D. Transmisión inalámbrica.

## PREGUNTA 9

La fibra óptica utiliza electricidad como señal principal para transportar datos por el interior de la fibra.

- [ ] A. Verdadero.
- [ ] B. Falso.

## PREGUNTA 10

El cable coaxial puede utilizarse para transmitir señales de televisión y datos de Internet.

- [ ] A. Verdadero.
- [ ] B. Falso.

---

# HOJA DE RESPUESTAS

| Pregunta | Mi respuesta |
|---|---|
| 1 | |
| 2 | |
| 3 | |
| 4 | |
| 5 | |
| 6 | |
| 7 | |
| 8 | |
| 9 | |
| 10 | |

---

# SOLUCIONARIO — NO REVISAR ANTES DE TERMINAR

### PREGUNTA 1
**Respuesta: C. Fibra óptica.**

La fibra óptica transmite información mediante pulsos de luz.

### PREGUNTA 2
**Respuesta: A, B y C.**

Los medios principales son conductores metálicos, fibra óptica y transmisión inalámbrica.

### PREGUNTA 3
**Respuesta: B. Reducir las interferencias eléctricas.**

El trenzado de los conductores ayuda a reducir las interferencias que pueden afectar las señales.

### PREGUNTA 4
**Respuesta: B. Cable coaxial.**

El cable coaxial tiene un conductor central rodeado por material aislante y blindaje metálico.

### PREGUNTA 5
**Respuesta: A. Cable de par trenzado.**

Ethernet utiliza frecuentemente par trenzado para conectar dispositivos en redes LAN.

### PREGUNTA 6
**Respuesta: A, B y C.**

La distancia, el entorno y la cantidad de datos o velocidad requerida son criterios fundamentales.

El costo de instalación también es un criterio importante.

### PREGUNTA 7
**Respuesta: C. Fibra óptica.**

Permite transportar grandes cantidades de datos a largas distancias y no sufre interferencias electromagnéticas en la señal óptica.

### PREGUNTA 8
**Respuesta: D. Transmisión inalámbrica.**

Utiliza ondas electromagnéticas para transportar información sin cables entre los dispositivos.

### PREGUNTA 9
**Respuesta: B. Falso.**

La fibra óptica transporta información mediante luz, no mediante señales eléctricas por el interior de la fibra.

### PREGUNTA 10
**Respuesta: A. Verdadero.**

El cable coaxial se utiliza en redes de televisión por cable y servicios de Internet por cable.

---

**PUNTAJE FINAL: ____ / 10**

# CONCEPTOS QUE DEBES DOMINAR ANTES DEL MÓDULO 7

- Los tres tipos principales de medios de red.
- Señales eléctricas, ópticas e inalámbricas.
- Los cuatro criterios para seleccionar un medio.
- Características del cable de par trenzado.
- Función del trenzado para reducir interferencias.
- Estructura y aplicaciones del cable coaxial.
- Funcionamiento y ventajas de la fibra óptica.
- Diferencias entre cobre, fibra óptica y medios inalámbricos.





# CISCO NETWORKING BASICS
## MÓDULO 5 — CUESTIONARIO DE REFUERZO
### Protocolos y estándares de comunicación

**Total:** 2 preguntas

**Instrucciones:** Responde primero las preguntas y consulta el solucionario al terminar.

---

## PREGUNTA 1 — Protocolos de red

Las reglas que rigen las comunicaciones de red, incluidos el formato, el tamaño, la temporización y el encapsulamiento, se denominan:

- [ ] A. Señalización
- [ ] B. Codificación
- [ ] C. Protocolos
- [ ] D. Mensajería

---

## PREGUNTA 2 — Estándares de Internet

El IETF (Internet Engineering Task Force) registra y publica los estándares de Internet en documentos conocidos como:

- [ ] A. Estándares de Protocolo de Internet (IPS)
- [ ] B. Documentos de Estándares IETF (ISD)
- [ ] C. Estándares de Especificación de Internet (ISS)
- [ ] D. Petición de Comentarios (RFC)

---

# HOJA DE RESPUESTAS

| Pregunta | Mi respuesta |
|---|---|
| 1 | |
| 2 | |

---

# SOLUCIONARIO EXPLICADO
## NO REVISAR ANTES DE TERMINAR

### PREGUNTA 1
**Respuesta correcta: C. Protocolos**

**¿Por qué?**

Los **protocolos de red** son conjuntos de reglas que permiten que los dispositivos se comuniquen correctamente.

Estas reglas establecen aspectos como:

- Formato del mensaje.
- Tamaño del mensaje.
- Temporización.
- Codificación.
- Encapsulación.
- Patrones de mensajes.

**¿Por qué no son las otras opciones?**

- **Señalización:** se relaciona con la transmisión y representación de señales.
- **Codificación:** es una característica relacionada con representar información mediante códigos o señales.
- **Mensajería:** se relaciona con el intercambio de mensajes, pero no es el término general para las reglas de comunicación.

**Ejemplo:**

Cuando una computadora se comunica con otra, ambas deben utilizar protocolos compatibles para interpretar los mensajes.

**PARA RECORDAR:**

Protocolos = reglas de comunicación.

---

### PREGUNTA 2
**Respuesta correcta: D. Petición de Comentarios (RFC)**

**¿Por qué?**

La **IETF (Internet Engineering Task Force)** desarrolla y publica especificaciones técnicas relacionadas con Internet mediante documentos conocidos como RFC.

**RFC (Request for Comments)** significa Solicitud de Comentarios o Petición de Comentarios.

Estos documentos permiten registrar especificaciones, protocolos y propuestas técnicas.

**¿Por qué no son las otras opciones?**

- **IPS:** no corresponde al nombre de los documentos solicitados.
- **ISD:** no corresponde a la denominación utilizada en el material de Cisco.
- **ISS:** tampoco es el nombre de los documentos RFC.

**IMPORTANTE:**

No todos los documentos RFC son estándares oficiales de Internet; también existen RFC informativos y experimentales.

**PARA RECORDAR:**

- IETF = organización que desarrolla estándares relacionados con Internet.
- RFC = documentos técnicos donde se publican especificaciones.
- IEEE = organización que desarrolla estándares como IEEE 802.11.
- ISO = organización internacional relacionada con el modelo OSI.

---

# RESUMEN PARA EL EXAMEN

| Pista en la pregunta | Respuesta |
|---|---|
| Reglas que rigen la comunicación | Protocolos |
| Formato, tamaño y temporización | Características de protocolos |
| Documentos publicados por IETF | RFC |
| Request for Comments | RFC |
| Estándar de redes inalámbricas | IEEE 802.11 |
| Modelo de siete capas | OSI |

---

**PUNTAJE FINAL: ____ / 2**

