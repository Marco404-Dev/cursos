
# CISCO NETWORKING BASICS
## MÓDULO 5 — CUESTIONARIO DE REFUERZO
### Protocolos, estándares y modelos OSI/TCP-IP

**Total:** 10 preguntas

**Instrucciones:** Responde primero todas las preguntas. En las preguntas 3, 8 y 10 debes seleccionar varias opciones.

---

## PREGUNTA 1 — Capa física

¿Cuál es el objetivo de la capa física de OSI?

- [ ] A. Transmitir bits por los medios locales.
- [ ] B. Intercambiar tramas entre nodos por medios físicos de red.
- [ ] C. Realizar pruebas de detección de errores en las tramas recibidas.
- [ ] D. Controlar el acceso a los medios.

---

## PREGUNTA 2 — Protocolos de red

¿Qué afirmación es correcta sobre los protocolos de red?

- [ ] A. Los protocolos de red definen el tipo de hardware que se utiliza y cómo se monta en los racks.
- [ ] B. Definen cómo se intercambian los mensajes entre el origen y el destino.
- [ ] C. Todos funcionan en la capa de acceso a la red de TCP/IP.
- [ ] D. Solo son necesarios para el intercambio de mensajes entre dispositivos en redes remotas.

---

## PREGUNTA 3 — Organizaciones de estandarización

¿Cuáles son los tres acrónimos o siglas que representan organismos de estandarización? (Elija tres opciones).

- [ ] A. IANA
- [ ] B. TCP/IP
- [ ] C. MAC
- [ ] D. OSI
- [ ] E. IEEE
- [ ] F. IETF

---

## PREGUNTA 4 — Reglas de comunicación

¿Qué término de red describe un conjunto particular de reglas en una capa que rigen la comunicación en esa capa?

- [ ] A. Verificación de errores.
- [ ] B. Encapsulación.
- [ ] C. Desajuste.
- [ ] D. Protocolo.

---

## PREGUNTA 5 — Capa de transporte

¿Qué capa del modelo OSI define los servicios para segmentar y rearmar los datos de comunicaciones individuales entre terminales?

- [ ] A. Sesión.
- [ ] B. Aplicación.
- [ ] C. Presentación.
- [ ] D. Transporte.
- [ ] E. Red.

---

## PREGUNTA 6 — Propósito de los protocolos

¿Cuál es el propósito de los protocolos en las comunicaciones de datos?

- [ ] A. Especificar el ancho de banda del canal o el medio para cada tipo de comunicación.
- [ ] B. Definir el contenido del mensaje que se envía durante la comunicación.
- [ ] C. Proporcionar las reglas requeridas para que se produzca un tipo específico de comunicación.
- [ ] D. Especificar los sistemas operativos de los dispositivos que permiten la comunicación.

---

## PREGUNTA 7 — Estándares de red

¿Qué término se refiere al conjunto de reglas que define cómo funciona una red?

- [ ] A. Modelo.
- [ ] B. Dominio.
- [ ] C. Estándar.
- [ ] D. Protocolo.

---

## PREGUNTA 8 — Capas OSI y TCP/IP

¿Cuáles son las tres capas del modelo OSI que conforman la capa de aplicación del modelo TCP/IP? (Elija tres opciones).

- [ ] A. Transporte.
- [ ] B. Presentación.
- [ ] C. Enlace de datos.
- [ ] D. De nube.
- [ ] E. Sesión.
- [ ] F. Red.

**Nota:** En la captura únicamente aparecen estas seis alternativas. Falta la alternativa "Aplicación", que debería estar incluida para que la pregunta tenga las tres respuestas correctas.

Para practicar la pregunta completa, agrega:

- [ ] G. Aplicación.

---

## PREGUNTA 9 — Documentos RFC

¿Qué organización emite y administra los documentos de Petición de Comentarios (Request for Comments, RFC)?

- [ ] A. IEEE.
- [ ] B. IETF.
- [ ] C. ISO.
- [ ] D. TIA/EIA.

---

## PREGUNTA 10 — Correspondencia OSI y TCP/IP

¿Cuáles son las dos capas del modelo OSI que tienen la misma funcionalidad que dos capas del modelo TCP/IP? (Escoge dos).

- [ ] A. Enlace de datos.
- [ ] B. Red.
- [ ] C. Sesión.
- [ ] D. Transporte.
- [ ] E. Física.

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

# SOLUCIONARIO EXPLICADO
## NO REVISAR ANTES DE TERMINAR

### PREGUNTA 1
**Respuesta: A. Transmitir bits por los medios locales.**

**¿Por qué?**

La capa física es la capa 1 del modelo OSI.

Su función consiste en transmitir bits mediante señales a través del medio físico.

Por ejemplo:

- Cable de cobre → señales eléctricas.
- Fibra óptica → señales luminosas.
- Medio inalámbrico → ondas electromagnéticas.

**¿Por qué no son las demás?**

Intercambiar tramas, controlar el acceso al medio y verificar errores de las tramas son funciones asociadas a la capa 2, Enlace de Datos.

**PARA RECORDAR:**

Capa 1 = Bits y señales físicas.

Capa 2 = Tramas y acceso al medio.

---

### PREGUNTA 2
**Respuesta: B. Definen cómo se intercambian los mensajes entre el origen y el destino.**

**¿Por qué?**

Los protocolos de red establecen reglas para que los dispositivos puedan comunicarse.

Estas reglas pueden definir:

- Formato del mensaje.
- Tamaño del mensaje.
- Sincronización.
- Codificación.
- Encapsulación.
- Patrones de comunicación.

**Ejemplo:**

Dos computadoras necesitan utilizar protocolos compatibles para intercambiar información correctamente.

**PARA RECORDAR:**

Protocolo = reglas que permiten intercambiar información.

---

### PREGUNTA 3
**Respuestas: A, E y F.**

- A. IANA.
- E. IEEE.
- F. IETF.

**¿Por qué?**

**IANA:** coordina recursos de numeración de Internet, como direcciones IP y números de protocolo.

**IEEE:** desarrolla estándares técnicos utilizados en redes, como IEEE 802.11.

**IETF:** desarrolla especificaciones y estándares de Internet mediante procesos documentados en RFC.

**¿Por qué no son las otras opciones?**

- TCP/IP = conjunto de protocolos.
- MAC = Control de Acceso al Medio.
- OSI = modelo de referencia.

**IMPORTANTE:**

En el contexto de Cisco, IANA se incluye entre las organizaciones relacionadas con la estandarización y administración de Internet, aunque su función principal es la coordinación de recursos de numeración.

---

### PREGUNTA 4
**Respuesta: D. Protocolo.**

**¿Por qué?**

Un protocolo es un conjunto de reglas que determina cómo debe producirse una comunicación.

En una pila de protocolos, cada capa cumple funciones específicas mediante protocolos adecuados.

**Ejemplo:**

TCP proporciona mecanismos de transporte confiable.

IP proporciona direccionamiento y encaminamiento.

**PARA RECORDAR:**

Protocolo = conjunto de reglas de comunicación.

---

### PREGUNTA 5
**Respuesta: D. Transporte.**

**¿Por qué?**

La capa 4 del modelo OSI es Transporte.

Proporciona servicios para transferir datos entre dispositivos finales.

Entre sus funciones se encuentran:

- Segmentación de datos.
- Transferencia de segmentos.
- Reensamblaje de datos.
- Servicios de comunicación entre procesos.

**Ejemplo:**

TCP permite segmentar y reensamblar datos para entregar información a una aplicación.

**PARA RECORDAR:**

Capa 4 = Transporte = Segmentación y reensamblaje.

---

### PREGUNTA 6
**Respuesta: C. Proporcionar las reglas requeridas para que se produzca un tipo específico de comunicación.**

**¿Por qué?**

Los protocolos especifican las reglas necesarias para establecer determinados tipos de comunicación.

No determinan obligatoriamente el sistema operativo del dispositivo ni el contenido específico que escribe el usuario.

**Ejemplo:**

HTTP establece reglas para intercambiar solicitudes y respuestas web.

**PARA RECORDAR:**

Los protocolos definen cómo se realiza la comunicación.

---

### PREGUNTA 7
**Respuesta: C. Estándar.**

**¿Por qué?**

Un estándar es un conjunto de reglas o especificaciones comunes que permiten que distintas tecnologías funcionen de manera compatible.

**Ejemplo:**

IEEE 802.11 establece especificaciones técnicas utilizadas por las redes WLAN.

**Diferencia importante:**

- Protocolo: define reglas para intercambiar mensajes.
- Estándar: establece especificaciones comunes para garantizar interoperabilidad.

Ambos conceptos se relacionan, pero Cisco utiliza aquí "estándar" por la referencia general a cómo funciona una red.

---

### PREGUNTA 8
**Respuestas: B, E y G.**

- B. Presentación.
- E. Sesión.
- G. Aplicación.

**¿Por qué?**

La capa de Aplicación del modelo TCP/IP reúne las funciones de tres capas del modelo OSI:

- Capa 7: Aplicación.
- Capa 6: Presentación.
- Capa 5: Sesión.

**PARA RECORDAR:**

Aplicación TCP/IP = Aplicación + Presentación + Sesión de OSI.

**Nota:** La tercera alternativa correcta no aparece en la captura visible. Se añadió al cuestionario para completarlo correctamente.

---

### PREGUNTA 9
**Respuesta: B. IETF.**

**¿Por qué?**

IETF significa Internet Engineering Task Force.

Participa en el desarrollo y publicación de especificaciones técnicas relacionadas con Internet mediante documentos conocidos como RFC.

**RFC significa:**

Request for Comments.

Traducción: Solicitud o Petición de Comentarios.

**PARA RECORDAR:**

- IETF → RFC.
- IEEE → Estándares como IEEE 802.11.
- ISO → Modelo de referencia OSI.

---

### PREGUNTA 10
**Respuestas: B y D.**

- B. Red.
- D. Transporte.

**¿Por qué?**

En la comparación de modelos presentada por Cisco:

- La capa de Red de OSI corresponde funcionalmente a la capa de Internet de TCP/IP.
- La capa de Transporte de OSI corresponde a la capa de Transporte de TCP/IP.

Las capas Física y Enlace de Datos de OSI se agrupan dentro de la única capa de Acceso a la Red de TCP/IP.

**IMPORTANTE:**

Esta pregunta es diferente de aquella que solicita las dos capas OSI que forman la capa de Acceso a la Red.

En ese otro caso las respuestas serían:

- Física.
- Enlace de Datos.

---

# TABLA DE REPASO — OSI Y TCP/IP

| Modelo OSI | Modelo TCP/IP |
|---|---|
| 7. Aplicación | Aplicación |
| 6. Presentación | Aplicación |
| 5. Sesión | Aplicación |
| 4. Transporte | Transporte |
| 3. Red | Internet |
| 2. Enlace de datos | Acceso a la red |
| 1. Física | Acceso a la red |

---

# CONCEPTOS CLAVE PARA EL EXAMEN

| Pista en la pregunta | Concepto |
|---|---|
| Transmitir bits | Capa física |
| Intercambiar tramas | Enlace de datos |
| Direccionamiento IP | Capa de red |
| Segmentar y reensamblar | Transporte |
| Organizar diálogos | Sesión |
| Representación de datos | Presentación |
| Servicios de aplicaciones | Aplicación |
| Reglas de comunicación | Protocolo |
| Especificaciones comunes | Estándar |
| Documentos RFC | IETF |
| Estándares IEEE 802.11 | IEEE |
| Direcciones IP y recursos numéricos | IANA |

---

# REPASO FINAL

**Modelo OSI: 7 capas.**

1. Física.
2. Enlace de datos.
3. Red.
4. Transporte.
5. Sesión.
6. Presentación.
7. Aplicación.

**Modelo TCP/IP: 4 capas.**

1. Acceso a la red.
2. Internet.
3. Transporte.
4. Aplicación.

**Correspondencias importantes:**

- OSI 1 + 2 = Acceso a la red TCP/IP.
- OSI 3 = Internet TCP/IP.
- OSI 4 = Transporte TCP/IP.
- OSI 5 + 6 + 7 = Aplicación TCP/IP.

---

**PUNTAJE FINAL: ____ / 10**




# CISCO NETWORKING BASICS
## MÓDULO 6 — CUESTIONARIO DE REFUERZO
### Medios de red y tipos de cableado

**Total:** 11 preguntas

**Instrucciones:** Selecciona las alternativas correctas. Algunas preguntas requieren dos o tres respuestas.

---

## PREGUNTA 1 — Conexión entre edificios

Un técnico en redes extiende la red desde el edificio principal de oficinas a varios cientos de metros hasta una nueva estación de seguridad.

La estación necesita una conexión de alta velocidad para admitir la videovigilancia del edificio principal.

¿Qué tipo de cable es el más adecuado?

- [ ] A. Coaxial
- [ ] B. Fibra óptica
- [ ] C. Par trenzado sin blindaje
- [ ] D. Par trenzado blindado

---

## PREGUNTA 2 — Medios de red

¿Cuáles son dos medios comunes que se utilizan en las redes? (Elija dos opciones).

- [ ] A. Cobre
- [ ] B. Nailon
- [ ] C. Madera
- [ ] D. Agua
- [ ] E. Fibra

---

## PREGUNTA 3 — Cableado de oficina

¿Qué tipo de cable de red se utiliza comúnmente para conectar computadoras de oficina a la red local?

- [ ] A. Cable coaxial
- [ ] B. Cable de fibra óptica de vidrio
- [ ] C. Cable de fibra óptica de plástico
- [ ] D. Cable de par trenzado

---

## PREGUNTA 4 — Selección de medios

¿Cuáles son los tres factores que se deben considerar al elegir los medios de red apropiados? (Elija tres opciones).

- [ ] A. La cantidad de datos y la tasa de transferencia de datos deseada
- [ ] B. Los sistemas operativos utilizados en los dispositivos de red presentes en la red
- [ ] C. El entorno en el que se instalan los medios
- [ ] D. La velocidad de la CPU y la cantidad de memoria en los servidores
- [ ] E. El requisito de seguridad de datos y tolerancia a fallas
- [ ] F. La distancia entre los hosts que conectarán los medios

---

## PREGUNTA 5 — Identificación visual de cableado

En la imagen de Cisco se observan cables con conectores metálicos circulares y una fibra delgada que sobresale por el centro.

¿Qué tipo de cableado se muestra?

- [ ] A. Fibra
- [ ] B. UTP
- [ ] C. Coaxial
- [ ] D. STP

---

## PREGUNTA 6 — Ventajas de la fibra óptica

¿Qué hace que la fibra sea preferible al cableado de cobre para la interconexión de edificios? (Elija tres opciones).

- [ ] A. Mayores distancias por cable
- [ ] B. Susceptibilidad limitada a EMI/RFI
- [ ] C. Conexiones duraderas
- [ ] D. Fácil de terminar
- [ ] E. Mayor potencial de ancho de banda
- [ ] F. Menor costo de instalación

---

## PREGUNTA 7 — Impulsos eléctricos

¿Qué tipo de medios de red transporta datos codificados en impulsos eléctricos?

- [ ] A. Medios inalámbricos
- [ ] B. Cable de cobre
- [ ] C. Comunicaciones de datos móviles
- [ ] D. Cable de fibra óptica

---

## PREGUNTA 8 — Tipos de medios eléctricos

¿Qué dos tipos de medios de red transportan datos codificados en impulsos eléctricos? (Elija dos opciones).

- [ ] A. Cable de fibra óptica de vidrio
- [ ] B. Cable de fibra óptica de plástico
- [ ] C. Cable coaxial
- [ ] D. Cable de par trenzado
- [ ] E. Medios inalámbricos

---

## PREGUNTA 9 — Impulsos de luz

¿Qué tipo de medios de red transporta datos codificados en impulsos de luz?

- [ ] A. Cable de par trenzado
- [ ] B. Cable de fibra óptica
- [ ] C. Medios inalámbricos
- [ ] D. Cable coaxial

---

## PREGUNTA 10 — Actualización de una LAN

Un administrador de red en una oficina pequeña está actualizando la red local dentro del edificio.

Se necesitan nuevos cables de red para conectar computadoras de oficina y dispositivos de red.

¿Qué medio de red debe utilizar el administrador?

- [ ] A. Cable de par trenzado
- [ ] B. Cable de fibra óptica
- [ ] C. Solución inalámbrica
- [ ] D. Cable coaxial

---

## PREGUNTA 11 — Pares trenzados

¿Cuál es el propósito de utilizar pares de cables trenzados en un cable Ethernet?

- [ ] A. Para proporcionar mayor ancho de banda
- [ ] B. Para garantizar que la transmisión de señales eléctricas se extienda a una distancia mayor
- [ ] C. Para identificar rutas de flujo de datos
- [ ] D. Para reducir la interferencia

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
| 11 | |

---

# SOLUCIONARIO EXPLICADO
## NO REVISAR ANTES DE TERMINAR

### PREGUNTA 1
**Respuesta correcta: B. Fibra óptica**

**¿Por qué?**

La estación de seguridad se encuentra a varios cientos de metros y necesita transmitir video a alta velocidad.

La fibra óptica es apropiada porque:

- Permite conexiones de grandes distancias.
- Tiene un alto potencial de ancho de banda.
- No sufre interferencias electromagnéticas en la señal óptica.

**Ejemplo:**

Edificio principal → Fibra óptica → Estación de seguridad

**PARA RECORDAR:**

Largas distancias + alta velocidad = fibra óptica.

---

### PREGUNTA 2
**Respuestas correctas: A y E.**

- A. Cobre.
- E. Fibra.

**¿Por qué?**

El cobre y la fibra óptica son dos medios físicos utilizados para transmitir datos.

**Cobre:**
Transmite información mediante impulsos eléctricos.

**Fibra óptica:**
Transmite información mediante pulsos de luz.

El nailon, la madera y el agua no corresponden a los medios de transmisión comunes presentados en este módulo de Cisco.

---

### PREGUNTA 3
**Respuesta correcta: D. Cable de par trenzado**

**¿Por qué?**

El cable de par trenzado es el tipo más común para conectar computadoras a switches dentro de una LAN Ethernet.

**Ejemplo:**

PC → Cable de par trenzado → Switch

**PARA RECORDAR:**

Computadoras de oficina + LAN Ethernet = par trenzado.

---

### PREGUNTA 4
**Respuestas correctas: A, C y F.**

- A. Cantidad de datos y velocidad requerida.
- C. Entorno de instalación.
- F. Distancia entre los hosts.

**¿Por qué?**

Cisco presenta cuatro criterios principales para seleccionar medios de red:

1. Distancia máxima.
2. Entorno de instalación.
3. Cantidad de datos y velocidad requerida.
4. Costo de instalación.

En esta pregunta aparecen tres de ellos.

**¿Por qué no las demás?**

El sistema operativo y las características de CPU o RAM de los servidores no determinan directamente qué medio físico debe instalarse.

La seguridad y la tolerancia a fallas pueden influir en el diseño de una red, pero no son una de las tres respuestas que solicita esta pregunta según los criterios presentados.

---

### PREGUNTA 5
**Respuesta correcta: A. Fibra**

**¿Por qué?**

La imagen muestra conectores de fibra óptica de tipo ST, caracterizados por su cuerpo metálico circular y mecanismo de acoplamiento.

Se distingue una férula que contiene la fibra óptica.

**PARA RECORDAR:**

- Fibra óptica = transporta pulsos de luz.
- UTP = pares de cobre sin blindaje.
- STP = pares de cobre con blindaje.
- Coaxial = conductor central rodeado de aislamiento y blindaje.

---

### PREGUNTA 6
**Respuestas correctas: A, B y E.**

- A. Mayores distancias por cable.
- B. Susceptibilidad limitada a EMI/RFI.
- E. Mayor potencial de ancho de banda.

**¿Por qué?**

La fibra óptica ofrece ventajas importantes para conectar edificios.

**1. Mayor distancia**

Puede transportar datos a mayores distancias que muchas implementaciones de Ethernet sobre cobre.

**2. Resistencia a interferencias**

La fibra utiliza luz, por lo que las interferencias electromagnéticas y de radiofrecuencia no afectan directamente la señal óptica.

**3. Gran ancho de banda**

Permite transportar cantidades elevadas de información.

**¿Por qué no las demás?**

- Conexiones duraderas: no es la ventaja diferenciadora principal.
- Fácil de terminar: normalmente requiere herramientas y procedimientos especializados.
- Menor costo: la instalación puede resultar más costosa según el entorno.

**PARA RECORDAR:**

Fibra = distancia + resistencia a interferencias + ancho de banda.

---

### PREGUNTA 7
**Respuesta correcta: B. Cable de cobre**

**¿Por qué?**

Los medios de cobre transportan datos mediante señales eléctricas.

**Ejemplo:**

PC → Cable Ethernet de cobre → Switch

**PARA RECORDAR:**

- Cobre = electricidad.
- Fibra = luz.
- Inalámbrico = ondas electromagnéticas.

---

### PREGUNTA 8
**Respuestas correctas: C y D.**

- C. Cable coaxial.
- D. Cable de par trenzado.

**¿Por qué?**

Ambos utilizan conductores metálicos y transmiten información mediante señales eléctricas.

**Cable coaxial:**
Utilizado frecuentemente en televisión por cable y servicios de Internet por cable.

**Cable de par trenzado:**
Utilizado frecuentemente en LAN Ethernet.

La fibra óptica transporta pulsos de luz.

Los medios inalámbricos transportan información mediante ondas electromagnéticas propagadas por el aire.

---

### PREGUNTA 9
**Respuesta correcta: B. Cable de fibra óptica**

**¿Por qué?**

La fibra óptica utiliza pulsos luminosos para transportar datos.

Las señales viajan a través de fibras de vidrio o plástico.

**Ejemplo:**

Router → Enlace de fibra óptica → Switch remoto

**PARA RECORDAR:**

Pulsos de luz = fibra óptica.

---

### PREGUNTA 10
**Respuesta correcta: A. Cable de par trenzado**

**¿Por qué?**

La pregunta describe una oficina pequeña que necesita conectar computadoras y equipos de red dentro de una LAN.

El cable de par trenzado es la opción habitual para estas conexiones.

**Ventajas:**

- Uso extendido en Ethernet.
- Instalación relativamente sencilla.
- Costo generalmente accesible.
- Adecuado para conexiones locales compatibles con sus límites de distancia.

**Ejemplo:**

Computadora → Cable UTP → Switch

---

### PREGUNTA 11
**Respuesta correcta: D. Para reducir la interferencia**

**¿Por qué?**

Los pares de conductores se trenzan para ayudar a reducir interferencias electromagnéticas y diafonía.

La diafonía ocurre cuando las señales de un par pueden interferir con las señales de otro.

El trenzado ayuda a mejorar la calidad de la transmisión eléctrica.

**IMPORTANTE:**

El propósito principal del trenzado no es identificar rutas, sino reducir interferencias.

**PARA RECORDAR:**

Pares trenzados = reducción de interferencias.

---

# TABLA FINAL PARA EL EXAMEN CISCO

| Pista de la pregunta | Respuesta |
|---|---|
| Largas distancias entre edificios | Fibra óptica |
| Alta capacidad y resistencia a EMI | Fibra óptica |
| Computadoras conectadas a una LAN | Par trenzado |
| Televisión por cable | Coaxial |
| Impulsos eléctricos | Cobre |
| Pulsos de luz | Fibra óptica |
| Ondas de radio | Inalámbrico |
| Reducir interferencia en cobre | Pares trenzados |
| Conectores metálicos ST con férula | Fibra óptica |

---

# RESUMEN DE LOS CONCEPTOS IMPORTANTES

**1. CABLE DE PAR TRENZADO**

- Transmite señales eléctricas.
- Es común en redes LAN Ethernet.
- Utiliza conductores trenzados.
- El trenzado ayuda a reducir interferencias.

**2. CABLE COAXIAL**

- Transmite señales eléctricas.
- Posee un conductor central.
- Utiliza aislamiento y blindaje metálico.
- Se emplea en sistemas de televisión y cable módem.

**3. FIBRA ÓPTICA**

- Transmite pulsos de luz.
- Permite conexiones de grandes distancias.
- Ofrece alto potencial de ancho de banda.
- No es afectada directamente por interferencias electromagnéticas.

**4. CRITERIOS PARA ELEGIR MEDIOS**

- Distancia.
- Entorno.
- Cantidad de datos y velocidad.
- Costo.

---

**PUNTAJE FINAL: ____ / 11**

