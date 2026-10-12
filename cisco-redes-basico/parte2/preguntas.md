
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
