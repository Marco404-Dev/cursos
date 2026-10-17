
# CISCO NETWORKING BASICS
## MÓDULO 5 — PRINCIPIOS DE COMUNICACIÓN

**Objetivo:** Comprender cómo se comunican los dispositivos mediante protocolos, por qué son necesarios los estándares y cómo funcionan los modelos TCP/IP y OSI.

---

# 5.1 — PROTOCOLOS DE COMUNICACIÓN

## 5.1.1 — Protocolos de comunicación

### ¿Qué es un protocolo?

Un **protocolo** es un conjunto de reglas que determina cómo se realiza una comunicación.

Al igual que las personas necesitan utilizar un idioma y establecer reglas para comunicarse, las computadoras necesitan protocolos para intercambiar información correctamente.

### ¿Qué reglas intervienen en una comunicación?

- **Emisor:** quien envía el mensaje.
- **Receptor:** quien recibe el mensaje.
- **Método:** medio utilizado para comunicarse.
- **Idioma:** lenguaje común entre los participantes.
- **Temporización:** momento y velocidad de la comunicación.
- **Confirmación:** mecanismo para verificar la recepción cuando sea necesario.

### Ejemplo cotidiano

Imagina que envías un mensaje de texto.

1. Escribes el mensaje.
2. Seleccionas al destinatario.
3. Utilizas una aplicación para enviarlo.
4. La aplicación transmite la información.
5. El destinatario recibe el mensaje.
6. Puede enviarse una confirmación de recepción.

**IDEA CLAVE:** los protocolos permiten que los dispositivos utilicen reglas comunes para intercambiar información.

---

## 5.1.2 — ¿Por qué importan los protocolos?

Los protocolos son necesarios para que las computadoras se comuniquen correctamente.

Si dos dispositivos no utilizan protocolos compatibles, podrían no interpretar correctamente los mensajes que intercambian.

### Características de los protocolos

**1. Formato del mensaje**

Define la estructura que debe tener un mensaje para ser interpretado correctamente.

**Ejemplo:** una solicitud web debe respetar el formato definido por el protocolo utilizado.

**2. Tamaño del mensaje**

Establece reglas relacionadas con el tamaño de los datos transmitidos.

Cuando un mensaje es demasiado grande, puede ser necesario dividirlo en partes más pequeñas.

**Ejemplo:** un archivo grande puede transmitirse mediante múltiples unidades de datos.

**3. Sincronización o temporización**

Determina aspectos relacionados con el momento y la velocidad de transmisión.

Permite coordinar el intercambio de información entre dispositivos.

**4. Codificación**

Consiste en representar la información de una forma adecuada para almacenarla o transmitirla.

**Ejemplo:**

Mensaje → Bits → Señales eléctricas, ópticas o inalámbricas.

El dispositivo receptor interpreta las señales para recuperar la información.

**5. Encapsulación**

Es el proceso mediante el cual se agrega información de control a los datos para permitir su transmisión.

Puede incluir información relacionada con:
- Direcciones de origen y destino.
- Identificación de protocolos.
- Entrega de información.
- Control de la comunicación.

**6. Patrón del mensaje**

Determina cómo se intercambian los mensajes entre dispositivos.

Por ejemplo:
- Solicitud y respuesta.
- Transmisión sin confirmación individual de recepción.

### Tabla de repaso

| Característica | Función |
|---|---|
| Formato | Define la estructura del mensaje. |
| Tamaño | Establece cómo manejar la cantidad de datos. |
| Sincronización | Coordina el momento y ritmo de transmisión. |
| Codificación | Representa la información en bits y señales. |
| Encapsulación | Agrega información de control. |
| Patrón | Define cómo se intercambian los mensajes. |

---

## ¿Cómo funciona la encapsulación?

Imagina que envías un mensaje desde una computadora a un servidor.

El mensaje necesita información adicional para poder viajar por la red.

### Ejemplo simplificado

**Datos originales:**

HOLA

**Durante la encapsulación:**

[Información de control] + [Datos: HOLA]

Esta información adicional permite que las distintas capas de comunicación procesen y transporten los datos.

### Proceso general

1. La aplicación genera información.
2. Las capas inferiores agregan información de control.
3. Los datos se transmiten mediante la red.
4. El dispositivo receptor procesa la información de control.
5. Se recuperan los datos originales.

**IMPORTANTE:**

- **Encapsulación:** agregar información de control a los datos.
- **Desencapsulación:** procesar y retirar la información de control correspondiente al recibirlos.

---

# 5.2 — ESTÁNDARES DE COMUNICACIÓN

## 5.2.1 — ¿Qué es un estándar?

Un **estándar** es un conjunto de reglas o especificaciones que permite que distintos dispositivos y tecnologías funcionen de manera compatible.

### ¿Por qué son necesarios?

Porque existen dispositivos desarrollados por diferentes fabricantes.

**Ejemplo:**

Una persona utiliza una laptop para enviar un correo electrónico y otra utiliza un teléfono para recibirlo.

Esto es posible porque ambos dispositivos utilizan protocolos y estándares compatibles.

### Diferencia entre protocolo y estándar

| Protocolo | Estándar |
|---|---|
| Define reglas de comunicación. | Establece especificaciones comunes. |
| Describe cómo intercambiar información. | Favorece la compatibilidad entre sistemas. |
| Ejemplo: HTTP. | Ejemplo: IEEE 802.11. |

**IMPORTANTE:** un protocolo también puede estar definido mediante un estándar. Los conceptos están relacionados.

---

## 5.2.2 — Internet y estándares

Los estándares permiten que diferentes dispositivos se comuniquen independientemente de su fabricante o sistema operativo.

### Ejemplo

Una computadora con Windows puede comunicarse con un servidor que utiliza Linux.

Esto ocurre porque ambos sistemas pueden utilizar protocolos compatibles.

### Beneficios

- **Interoperabilidad:** equipos diferentes pueden comunicarse.
- **Compatibilidad:** tecnologías de distintos fabricantes pueden funcionar juntas.
- **Estandarización:** se utilizan reglas comunes.
- **Desarrollo tecnológico:** pueden implementarse nuevas tecnologías siguiendo especificaciones compartidas.

**IDEA CLAVE:** Internet necesita estándares comunes para permitir la comunicación entre dispositivos y redes diferentes.

---

## 5.2.3 — Organizaciones de estándares de red

Los estándares de Internet se desarrollan mediante procesos de discusión, revisión y pruebas.

### IETF

**IETF (Internet Engineering Task Force)** significa Grupo de Trabajo de Ingeniería de Internet.

Participa en el desarrollo y mantenimiento de estándares relacionados con Internet.

### RFC

**RFC (Request for Comments)** significa Solicitud de Comentarios.

Son documentos numerados que describen especificaciones, protocolos, propuestas y otros aspectos técnicos relacionados con Internet.

**IMPORTANTE:** no todos los documentos RFC son estándares oficiales de Internet.

### Otras organizaciones relacionadas

**IEEE**

Institute of Electrical and Electronics Engineers.

Desarrolla estándares técnicos utilizados en redes, como IEEE 802.11.

**ISO**

International Organization for Standardization.

Es una organización internacional de normalización relacionada con el desarrollo del modelo de referencia OSI.

### Para recordar

- **IETF:** desarrolla estándares relacionados con Internet.
- **RFC:** documentos técnicos numerados.
- **IEEE:** desarrolla estándares técnicos.
- **ISO:** organización internacional de normalización.

---

# 5.3 — MODELOS DE COMUNICACIÓN DE RED

## 5.3.1 — ¿Qué es una pila de protocolos?

Una **pila de protocolos** es una organización de protocolos en diferentes capas que trabajan conjuntamente para permitir la comunicación.

Cada capa cumple funciones específicas y utiliza servicios proporcionados por otras capas.

### ¿Por qué se utilizan capas?

- Facilitan comprender el funcionamiento de una red.
- Organizan las funciones de los protocolos.
- Favorecen la interoperabilidad.
- Permiten desarrollar y modificar tecnologías sin cambiar necesariamente todo el sistema.
- Facilitan identificar problemas de comunicación.

### Ejemplo

Cuando visitas una página web, intervienen diferentes protocolos.

- **HTTP:** permite intercambiar información web.
- **TCP:** proporciona servicios de transporte.
- **IP:** permite direccionar y encaminar paquetes.
- **Ethernet:** puede transportar información dentro de una LAN cableada.

**IMPORTANTE:** estos protocolos no realizan exactamente la misma función. Cada uno participa en una parte distinta de la comunicación.

---

## 5.3.3 — MODELO TCP/IP

### ¿Qué es TCP/IP?

El **modelo TCP/IP** organiza las funciones de comunicación utilizadas por los protocolos de Internet.

Tiene **4 capas principales**.

### Las cuatro capas TCP/IP

| Número | Capa | Función |
|---|---|---|
| 4 | Aplicación | Proporciona funciones de comunicación para aplicaciones y representación de datos. |
| 3 | Transporte | Permite la comunicación entre procesos de diferentes dispositivos. |
| 2 | Internet | Permite el direccionamiento y encaminamiento entre redes. |
| 1 | Acceso a la red | Se relaciona con el hardware y los medios utilizados para transmitir información. |

### 1. Capa de Aplicación

Proporciona servicios de comunicación utilizados por las aplicaciones.

**Ejemplo:** un navegador que utiliza HTTP para comunicarse con un servidor web.

### 2. Capa de Transporte

Permite transportar información entre procesos de dispositivos diferentes.

**Ejemplo:** TCP permite establecer una comunicación con mecanismos de entrega confiable.

### 3. Capa de Internet

Se encarga del direccionamiento y del encaminamiento entre redes.

**Ejemplo:** IP permite que los paquetes sean enviados hacia una dirección de destino.

### 4. Capa de Acceso a la Red

Comprende las funciones relacionadas con los medios físicos y el acceso a ellos.

**Ejemplo:** Ethernet permite intercambiar información dentro de una red cableada.

### Ejemplo de comunicación

Supongamos que abres una página web.

1. **Aplicación:** el navegador solicita información.
2. **Transporte:** se utilizan servicios de transporte para comunicar los procesos.
3. **Internet:** los paquetes se direccionan hacia el destino.
4. **Acceso a la red:** los datos se transmiten mediante la tecnología de red utilizada.

**PARA RECORDAR:**

TCP/IP tiene 4 capas:

1. Aplicación.
2. Transporte.
3. Internet.
4. Acceso a la red.

---

## 5.3.4 — MODELO DE REFERENCIA OSI

### ¿Qué es OSI?

**OSI (Open Systems Interconnection)** significa Interconexión de Sistemas Abiertos.

Es un modelo de referencia que describe las funciones necesarias para la comunicación de redes.

Fue desarrollado en el ámbito de normalización de ISO.

### ¿Cuántas capas tiene?

El modelo OSI tiene **7 capas**.

### Tabla del modelo OSI

| Capa | Nombre | Función |
|---|---|---|
| 7 | Aplicación | Proporciona servicios de comunicación a los procesos de aplicación. |
| 6 | Presentación | Proporciona una representación común de los datos. |
| 5 | Sesión | Organiza y administra el diálogo entre aplicaciones. |
| 4 | Transporte | Segmenta, transfiere y reensambla datos entre dispositivos finales. |
| 3 | Red | Permite intercambiar datos entre dispositivos ubicados en diferentes redes. |
| 2 | Enlace de datos | Permite intercambiar tramas mediante un medio común. |
| 1 | Física | Define cómo se transmiten los bits mediante señales físicas. |

---

### CAPA 7 — APLICACIÓN

Es la capa relacionada con los servicios de comunicación utilizados por las aplicaciones.

**Ejemplo:** protocolos que permiten intercambiar información web.

**PARA RECORDAR:** servicios de comunicación de aplicaciones.

---

### CAPA 6 — PRESENTACIÓN

Se encarga de proporcionar una representación común de los datos intercambiados.

Puede relacionarse con:
- Formato de datos.
- Conversión de representaciones.
- Codificación de información.

**Ejemplo:** representar información de manera que pueda ser interpretada por el sistema receptor.

**PARA RECORDAR:** representación de datos.

---

### CAPA 5 — SESIÓN

Proporciona servicios para organizar y administrar el diálogo entre aplicaciones.

**Ejemplo:** funciones que permiten coordinar el intercambio de información entre procesos.

**PARA RECORDAR:** administración del diálogo.

---

### CAPA 4 — TRANSPORTE

Define servicios para transferir datos entre dispositivos finales.

Puede incluir:
- Segmentación.
- Transferencia.
- Reensamblaje.
- Control de la comunicación.

**Ejemplo:** TCP.

**PARA RECORDAR:** comunicación extremo a extremo entre procesos.

---

### CAPA 3 — RED

Permite intercambiar información entre dispositivos ubicados en diferentes redes.

Incluye funciones de direccionamiento y encaminamiento.

**Ejemplo:** IP.

**PARA RECORDAR:** direccionamiento y rutas.

---

### CAPA 2 — ENLACE DE DATOS

Define procedimientos para intercambiar tramas entre dispositivos mediante un medio común.

**Ejemplo:** funciones de Ethernet relacionadas con el intercambio de tramas.

**PARA RECORDAR:** tramas y comunicación mediante el enlace.

---

### CAPA 1 — FÍSICA

Describe las características físicas necesarias para transmitir bits.

Incluye aspectos:
- Mecánicos.
- Eléctricos.
- Ópticos.
- Funcionales.
- De transmisión de señales.

**Ejemplo:** transmitir bits mediante señales eléctricas en un cable de cobre.

**PARA RECORDAR:** bits y señales físicas.

---

## Cómo memorizar las siete capas OSI

**De arriba hacia abajo:**

7. Aplicación.
6. Presentación.
5. Sesión.
4. Transporte.
3. Red.
2. Enlace de datos.
1. Física.

**De abajo hacia arriba:**

1. Física.
2. Enlace de datos.
3. Red.
4. Transporte.
5. Sesión.
6. Presentación.
7. Aplicación.

### Regla de estudio

- Capa 7 → Aplicaciones.
- Capa 6 → Representación.
- Capa 5 → Diálogo.
- Capa 4 → Transporte.
- Capa 3 → Direccionamiento.
- Capa 2 → Tramas.
- Capa 1 → Bits.

---

## 5.3.5 — COMPARACIÓN OSI Y TCP/IP

### ¿Por qué existen dos modelos?

El modelo TCP/IP describe las funciones relacionadas con la suite de protocolos utilizada para las comunicaciones de Internet.

El modelo OSI es un modelo de referencia que permite estudiar las funciones de comunicación con mayor separación entre capas.

### Comparación de capas

| Modelo OSI | Modelo TCP/IP |
|---|---|
| 7. Aplicación | Aplicación |
| 6. Presentación | Aplicación |
| 5. Sesión | Aplicación |
| 4. Transporte | Transporte |
| 3. Red | Internet |
| 2. Enlace de datos | Acceso a la red |
| 1. Física | Acceso a la red |

### Diferencias principales

**Modelo OSI**
- Tiene 7 capas.
- Es un modelo de referencia.
- Se utiliza para estudiar las funciones de las redes.
- Facilita la descripción y resolución de problemas.

**Modelo TCP/IP**
- Tiene 4 capas en la representación estudiada en Cisco.
- Está relacionado con los protocolos utilizados en Internet.
- Organiza las funciones de la suite de protocolos TCP/IP.

### Correspondencias importantes

- OSI 7, 6 y 5 → Aplicación TCP/IP.
- OSI 4 → Transporte TCP/IP.
- OSI 3 → Internet TCP/IP.
- OSI 2 y 1 → Acceso a la red TCP/IP.

**IMPORTANTE:**

En ambos modelos, las funciones de transporte son comparables.

La capa de Internet del modelo TCP/IP corresponde a la capa de Red del modelo OSI.

---

# EJEMPLO GENERAL — COMUNICACIÓN ENTRE COMPUTADORAS

Imagina que utilizas una laptop para consultar una página web.

### Proceso simplificado

1. El navegador genera una solicitud.
2. La información es procesada por las funciones de las capas superiores.
3. La capa de transporte prepara la comunicación entre procesos.
4. La capa de Internet proporciona el direccionamiento.
5. La capa de acceso a la red transmite la información mediante el medio disponible.
6. Los equipos intermedios permiten que la información avance hacia el destino.
7. El servidor recibe y procesa la solicitud.
8. El servidor genera una respuesta.
9. La información regresa al dispositivo cliente.
10. El navegador muestra el contenido recibido.

**IDEA CLAVE:**

Los protocolos trabajan conjuntamente. Cada capa cumple una función específica dentro del proceso completo de comunicación.

---

# GLOSARIO — MÓDULO 5

| Término | Significado |
|---|---|
| Protocolo | Conjunto de reglas de comunicación. |
| Estándar | Especificación común para garantizar compatibilidad. |
| Encapsulación | Proceso de agregar información de control a los datos. |
| Desencapsulación | Procesamiento de esa información al recibir los datos. |
| Codificación | Representación de información mediante códigos o señales. |
| Sincronización | Coordinación temporal de la comunicación. |
| HTTP | Protocolo de comunicación web. |
| TCP | Protocolo de transporte. |
| IP | Protocolo de Internet. |
| Ethernet | Tecnología de comunicación de red. |
| IETF | Internet Engineering Task Force. |
| RFC | Request for Comments. |
| IEEE | Institute of Electrical and Electronics Engineers. |
| ISO | International Organization for Standardization. |
| OSI | Open Systems Interconnection. |
| TCP/IP | Suite de protocolos utilizada en Internet. |
| Pila de protocolos | Organización de protocolos en capas. |
| Trama | Unidad de datos utilizada en la capa de enlace. |
| Paquete | Unidad de datos utilizada en la capa de red. |
| Segmentación | División de datos en unidades más pequeñas. |

---

# RESUMEN GENERAL — MÓDULO 5

1. Los protocolos establecen reglas para que los dispositivos intercambien información.
2. Las características de los protocolos incluyen formato, tamaño, sincronización, codificación, encapsulación y patrones de mensajes.
3. La encapsulación agrega información de control a los datos.
4. Los estándares permiten la interoperabilidad entre dispositivos de diferentes fabricantes.
5. La IETF participa en el desarrollo de estándares relacionados con Internet.
6. Los RFC son documentos técnicos utilizados para registrar especificaciones y propuestas.
7. Las pilas de protocolos organizan funciones de comunicación en capas.
8. El modelo TCP/IP tiene cuatro capas en el esquema estudiado por Cisco.
9. El modelo OSI tiene siete capas.
10. El modelo OSI permite estudiar las funciones de comunicación de manera más detallada.
11. La capa de Red de OSI corresponde a la capa de Internet de TCP/IP.
12. La capa de Transporte tiene funciones comparables en ambos modelos.
13. Las capas Física y Enlace de Datos de OSI corresponden a Acceso a la Red de TCP/IP.
14. Las capas Aplicación, Presentación y Sesión de OSI corresponden a Aplicación de TCP/IP.

**IDEA FINAL:**

Las comunicaciones de red necesitan protocolos comunes y funciones organizadas. Los modelos OSI y TCP/IP permiten comprender cómo trabajan conjuntamente esas funciones para transmitir información entre dispositivos.

---

# CUESTIONARIO — MÓDULO 5

**Total:** 10 preguntas  
**Puntaje máximo:** 10 puntos

**Instrucciones:** Marca las alternativas correctas. En las preguntas indicadas debes seleccionar varias opciones.

## PREGUNTA 1

¿Qué término describe el conjunto de reglas utilizado por los dispositivos para comunicarse correctamente a través de una red?

- [ ] A. Topología.
- [ ] B. Protocolo.
- [ ] C. Medio físico.
- [ ] D. Dirección IP.

## PREGUNTA 2

¿Cuáles de las siguientes características pueden ser definidas por los protocolos de red? (Selecciona tres).

- [ ] A. Formato del mensaje.
- [ ] B. Tamaño del mensaje.
- [ ] C. Encapsulación.
- [ ] D. Color físico de los dispositivos.

## PREGUNTA 3

¿Qué proceso agrega información de control a los datos antes de transmitirlos por una red?

- [ ] A. Desencapsulación.
- [ ] B. Compresión.
- [ ] C. Encapsulación.
- [ ] D. Traducción.

## PREGUNTA 4

¿Qué organización participa en el desarrollo de estándares de Internet mediante documentos RFC?

- [ ] A. IETF.
- [ ] B. IEEE.
- [ ] C. ISO.
- [ ] D. Wi-Fi Alliance.

## PREGUNTA 5

¿Cuántas capas tiene el modelo TCP/IP presentado en Cisco Networking Basics?

- [ ] A. 3 capas.
- [ ] B. 4 capas.
- [ ] C. 5 capas.
- [ ] D. 7 capas.

## PREGUNTA 6

¿Qué capa del modelo TCP/IP determina las rutas para transmitir información entre redes?

- [ ] A. Aplicación.
- [ ] B. Transporte.
- [ ] C. Internet.
- [ ] D. Acceso a la red.

## PREGUNTA 7

¿Qué capa del modelo OSI se encarga de intercambiar tramas mediante un medio común?

- [ ] A. Física.
- [ ] B. Enlace de datos.
- [ ] C. Red.
- [ ] D. Transporte.

## PREGUNTA 8

¿Cuáles de las siguientes capas del modelo OSI corresponden a la capa de Aplicación del modelo TCP/IP? (Selecciona tres).

- [ ] A. Aplicación.
- [ ] B. Presentación.
- [ ] C. Sesión.
- [ ] D. Red.

## PREGUNTA 9

La capa de Red del modelo OSI corresponde a la capa de Internet del modelo TCP/IP.

- [ ] A. Verdadero.
- [ ] B. Falso.

## PREGUNTA 10

El modelo OSI está formado por cuatro capas, mientras que TCP/IP está formado por siete.

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
**Respuesta: B. Protocolo.**

Un protocolo es un conjunto de reglas que permite establecer comunicaciones entre dispositivos.

### PREGUNTA 2
**Respuesta: A, B y C.**

Los protocolos pueden definir el formato, tamaño y encapsulación de los mensajes.

### PREGUNTA 3
**Respuesta: C. Encapsulación.**

La encapsulación agrega información de control necesaria para transportar los datos.

### PREGUNTA 4
**Respuesta: A. IETF.**

La IETF desarrolla y mantiene estándares relacionados con Internet mediante procesos documentados, incluidos los RFC.

### PREGUNTA 5
**Respuesta: B. 4 capas.**

El modelo TCP/IP presentado por Cisco contiene Aplicación, Transporte, Internet y Acceso a la Red.

### PREGUNTA 6
**Respuesta: C. Internet.**

La capa de Internet se relaciona con el direccionamiento y encaminamiento de paquetes entre redes.

### PREGUNTA 7
**Respuesta: B. Enlace de datos.**

La capa de Enlace de Datos utiliza tramas para intercambiar información mediante un medio común.

### PREGUNTA 8
**Respuesta: A, B y C.**

Las capas Aplicación, Presentación y Sesión del modelo OSI corresponden a la capa de Aplicación de TCP/IP.

### PREGUNTA 9
**Respuesta: A. Verdadero.**

La capa de Red del modelo OSI corresponde funcionalmente a la capa de Internet del modelo TCP/IP.

### PREGUNTA 10
**Respuesta: B. Falso.**

El modelo OSI tiene siete capas y el modelo TCP/IP estudiado tiene cuatro.

---

**PUNTAJE FINAL: ____ / 10**

# CONCEPTOS QUE DEBES DOMINAR ANTES DEL MÓDULO 6

- Definición y funciones de los protocolos.
- Formato, tamaño y sincronización de mensajes.
- Codificación y encapsulación.
- Diferencia entre protocolos y estándares.
- Función de la IETF y documentos RFC.
- Significado de pila de protocolos.
- Las cuatro capas TCP/IP.
- Las siete capas OSI.
- Correspondencia entre OSI y TCP/IP.
- Funciones de las capas Física, Enlace, Red y Transporte.




# CISCO NETWORKING BASICS
## MÓDULO 5 — CUESTIONARIO DE REFUERZO
### Protocolos y características de comunicación

**Total:** 3 preguntas

**Instrucciones:** Responde primero las preguntas. Consulta el solucionario únicamente después de terminar.

---

## PREGUNTA 1 — Protocolos de comunicación

Bianka, un viajero polaco en Hanói, Vietnam, se detiene y le pregunta a Nguyệt cómo llegar al Ngoc Son Temple.

Se comunican verbalmente y determinan que ambos hablan inglés. Después de recibir instrucciones en inglés para el templo, Bianka se las repite a Nguyệt. Nguyệt dice: "Sí, eso es correcto".

Seleccione el orden de los protocolos de comunicación utilizados en este escenario.

- [ ] A. Confirmación, método, idioma.
- [ ] B. Método, confirmación, idioma.
- [ ] C. Método, idioma, confirmación.
- [ ] D. Idioma, método, confirmación.

---

## PREGUNTA 2 — Trama Ethernet

Rory está estudiando los campos dentro de una trama de Ethernet para una prueba próxima y advierte que la dirección de control de acceso al medio (MAC) de destino aparece primero antes de la dirección MAC de origen.

¿Cuál de las siguientes características del protocolo investiga Rory?

- [ ] A. Codificación.
- [ ] B. Sincronización.
- [ ] C. Patrón del mensaje.
- [ ] D. Sincronización del mensaje.
- [ ] E. Encapsulación.

---

## PREGUNTA 3 — Características de Ethernet

A medida que Rory continúa estudiando Ethernet, descubre que una trama suele tener de 64 a 1518 bytes de información que se convierte en una serie de bits antes de enviarse a la red.

¿Qué dos características de protocolo aprendió Rory para Ethernet? (Elija dos opciones).

- [ ] A. Tamaño del mensaje.
- [ ] B. Codificación.
- [ ] C. Encapsulación.
- [ ] D. Sincronización.
- [ ] E. Patrón del mensaje.

---

# HOJA DE RESPUESTAS

| Pregunta | Mi respuesta |
|---|---|
| 1 | |
| 2 | |
| 3 | |

---

# SOLUCIONARIO EXPLICADO
## NO REVISAR ANTES DE TERMINAR

### PREGUNTA 1
**Respuesta correcta: C. Método, idioma, confirmación.**

**¿Por qué?**

El escenario presenta tres momentos:

1. **Método:** Bianka y Nguyệt se comunican verbalmente.
2. **Idioma:** comprueban que ambos hablan inglés.
3. **Confirmación:** Bianka repite las indicaciones y Nguyệt confirma que son correctas.

**Ejemplo en redes:**

Los dispositivos necesitan utilizar reglas comunes para comunicarse y, cuando el protocolo lo requiere, confirmar la recepción de información.

**PARA RECORDAR:**

- Método = cómo nos comunicamos.
- Idioma = lenguaje común.
- Confirmación = verificar que el mensaje fue recibido o comprendido correctamente.

---

### PREGUNTA 2
**Respuesta correcta: E. Encapsulación.**

**¿Por qué?**

Rory está estudiando cómo se organiza una trama Ethernet.

La encapsulación implica agregar información de control a los datos mediante una estructura definida por el protocolo.

En una trama Ethernet, las direcciones MAC aparecen en un orden específico:

1. Dirección MAC de destino.
2. Dirección MAC de origen.
3. Otros campos de la trama.

**Ejemplo:**

Una computadora necesita enviar información a otra.

La trama Ethernet contiene las direcciones MAC correspondientes para permitir que se transporte por la red local.

**¿Por qué no es codificación?**

Porque la codificación trata sobre la representación de la información mediante bits o señales.

En esta pregunta, Rory analiza la estructura de los campos de la trama, no cómo se representan las señales.

**PARA RECORDAR:**

- Encapsulación = agregar y organizar información de control.
- Codificación = representar información mediante bits o señales.
- Sincronización = coordinar el momento o ritmo de comunicación.
- Patrón del mensaje = forma en que se intercambian mensajes, por ejemplo, solicitud y respuesta.

**NOTA:** La característica más específica sería "formato del mensaje", porque Rory observa el orden de los campos. Sin embargo, esa opción no aparece entre las alternativas. De las opciones disponibles, encapsulación es la que mejor se relaciona con la estructura de la trama.

---

### PREGUNTA 3
**Respuestas correctas: A y B.**

- A. Tamaño del mensaje.
- B. Codificación.

**¿Por qué?**

La pregunta proporciona dos características diferentes.

**Primera característica: tamaño del mensaje.**

El enunciado señala que la trama Ethernet suele tener entre 64 y 1518 bytes.

Esto corresponde al tamaño del mensaje, porque establece la cantidad de información que puede contener una trama según el formato estudiado.

**Segunda característica: codificación.**

El enunciado indica que la información se convierte en una serie de bits antes de enviarse por la red.

Esto se relaciona con la codificación, porque los datos deben representarse de una manera adecuada para su transmisión.

**Ejemplo:**

Una computadora necesita transmitir una trama Ethernet.

1. La trama debe respetar un tamaño permitido.
2. La información se representa mediante bits.
3. Los bits se transmiten utilizando las señales correspondientes al medio.

**¿Por qué no es encapsulación?**

Porque el enunciado no se centra en agregar encabezados u otros campos de control, sino en el tamaño de la trama y la representación de la información.

**PARA RECORDAR:**

- 64 a 1518 bytes → Tamaño del mensaje.
- Convertir información en bits → Codificación.
- Agregar encabezados → Encapsulación.
- Coordinar velocidades y tiempos → Sincronización.
- Solicitud y respuesta → Patrón del mensaje.

---

# REPASO GENERAL PARA CISCO

| Pista en la pregunta | Concepto |
|---|---|
| Cómo se comunican las personas | Método |
| Idioma compartido | Lenguaje común |
| Verificar si el mensaje fue recibido | Confirmación |
| Tamaño en bytes | Tamaño del mensaje |
| Convertir información en bits o señales | Codificación |
| Agregar encabezados y campos de control | Encapsulación |
| Velocidad o momento de transmisión | Sincronización |
| Solicitud y respuesta | Patrón del mensaje |

---

# TRUCO PARA IDENTIFICAR RESPUESTAS

Cuando Cisco presente una pregunta sobre características de protocolos, identifica primero qué información está describiendo:

1. ¿Habla de cantidad de bytes? → Tamaño.
2. ¿Habla de bits o señales? → Codificación.
3. ¿Habla de encabezados o direcciones agregadas? → Encapsulación.
4. ¿Habla del momento o velocidad? → Sincronización.
5. ¿Habla de solicitudes y respuestas? → Patrón del mensaje.

---

**PUNTAJE FINAL: ____ / 3**

