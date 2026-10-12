
# CISCO NETWORKING BASICS
## MÓDULO 7 — LA CAPA DE ACCESO

**Objetivo:** Comprender cómo se encapsulan los mensajes, cómo funcionan las tramas Ethernet y cómo los switches permiten la comunicación entre dispositivos dentro de una red local.

---

# 7.1 — ENCAPSULACIÓN Y TRAMAS ETHERNET

## 7.1.2 — Encapsulación

### ¿Qué es la encapsulación?

La **encapsulación (Encapsulation)** es el proceso de colocar los datos dentro de una estructura que incluye información adicional necesaria para transmitirlos.

Esta información permite identificar aspectos de la comunicación, como el origen y el destino.

### Ejemplo: enviar una carta

Imagina que deseas enviar una carta a otra persona.

1. Escribes el mensaje.
2. Colocas la carta dentro de un sobre.
3. Escribes las direcciones del remitente y del destinatario.
4. Envías el sobre.
5. El destinatario recibe el sobre y extrae la carta.

En una red ocurre algo similar: los datos se encapsulan para poder transmitirse correctamente.

### ¿Qué es la desencapsulación?

La **desencapsulación (Decapsulation)** es el proceso inverso.

El dispositivo receptor procesa la información adicional que acompaña al mensaje para recuperar los datos correspondientes.

**PARA RECORDAR:**
- Encapsulación = agregar información de control.
- Desencapsulación = procesar y retirar esa información al recibir los datos.

---

## ¿Qué es una trama?

Una **trama (Frame)** es una unidad de datos utilizada en la capa de enlace de datos.

Las tramas Ethernet permiten transportar información entre dispositivos a través de una red Ethernet.

### ¿Qué información contiene una trama Ethernet?

Entre sus campos importantes se encuentran:

- **Preámbulo:** ayuda a sincronizar la recepción.
- **Delimitador de inicio:** indica dónde comienza la trama.
- **Dirección MAC de destino:** identifica al destinatario en el enlace Ethernet.
- **Dirección MAC de origen:** identifica al dispositivo emisor.
- **Longitud o tipo:** identifica la longitud o el protocolo correspondiente, según el formato.
- **Datos:** contiene la información transportada.
- **FCS:** secuencia de verificación utilizada para detectar errores.

### ¿Qué es una dirección MAC?

**MAC (Media Access Control)** es una dirección utilizada en la capa de enlace de datos para identificar interfaces de red.

En Ethernet, las direcciones MAC de origen y destino aparecen dentro de la trama.

**Ejemplo de dirección MAC:**

00:1A:2B:3C:4D:5E

### ¿Cómo funciona?

1. Una computadora prepara información para enviarla.
2. Se agrega la información necesaria para formar la trama.
3. La trama incluye las direcciones MAC de origen y destino.
4. La trama se transmite por Ethernet.
5. El dispositivo receptor procesa la trama.

**IMPORTANTE:**

La trama Ethernet utiliza direcciones MAC para la entrega en el enlace.

El protocolo IP utiliza direcciones IP para permitir la comunicación entre redes.

---

## Encapsulación de paquetes IP

Cisco también presenta el protocolo IP como ejemplo de encapsulación.

**IP (Internet Protocol)** permite direccionar paquetes desde un origen hacia un destino a través de una o varias redes.

### Encabezado IPv6

En la figura del curso se presenta un encabezado IPv6 de **40 bytes**.

Los campos mostrados son:

- Versión.
- Clase de tráfico.
- Etiqueta de flujo.
- Longitud de carga útil.
- Siguiente encabezado.
- Límite de saltos.
- Dirección IPv6 de origen.
- Dirección IPv6 de destino.

**IMPORTANTE:** estos campos se estudiarán con mayor detalle en los módulos de direccionamiento IP.

---

# 7.2 — LA CAPA DE ACCESO

## ¿Qué es la capa de acceso?

La **capa de acceso** es la parte de la infraestructura de red que permite conectar los dispositivos finales a la red local.

Es el primer punto de conexión de computadoras, impresoras y otros hosts con la infraestructura Ethernet.

### Ejemplo

Computadora → Switch → Impresora de red

La computadora y la impresora pueden conectarse a un switch para intercambiar información.

En redes Ethernet cableadas, los dispositivos finales suelen conectarse mediante cables Ethernet.

---

## Concentrador Ethernet (Hub)

### ¿Qué es un hub?

Un **hub o concentrador Ethernet** es un dispositivo que permite conectar varios hosts dentro de una red.

Tiene múltiples puertos Ethernet.

### ¿Cómo funciona?

1. Una computadora transmite una señal.
2. El hub repite la señal hacia los demás puertos.
3. Los dispositivos conectados reciben la señal.
4. Si varios dispositivos transmiten al mismo tiempo, pueden producirse colisiones.

### ¿Qué es una colisión?

Una **colisión** ocurre cuando dos o más dispositivos transmiten simultáneamente sobre un medio Ethernet compartido y sus señales interfieren.

Las colisiones pueden provocar retransmisiones y disminuir el rendimiento.

### Desventajas del hub

- Comparte el medio de comunicación entre los dispositivos.
- Puede presentar colisiones.
- Las retransmisiones reducen el rendimiento.
- Es una tecnología antigua, reemplazada ampliamente por switches.

**PARA RECORDAR:**

Hub = repite señales hacia otros puertos y comparte el dominio de colisión.

---

## Switch Ethernet

### ¿Qué es un switch?

Un **switch (conmutador)** es un dispositivo de red que permite conectar hosts dentro de una LAN.

Un switch Ethernet tradicional trabaja principalmente en la **capa 2 del modelo OSI: Enlace de Datos**.

### ¿Cómo funciona?

1. Una computadora envía una trama Ethernet.
2. El switch recibe la trama.
3. Examina la dirección MAC de destino.
4. Consulta su tabla de direcciones MAC.
5. Si conoce el puerto de destino, reenvía la trama hacia ese puerto.
6. Si no conoce la dirección MAC de destino, normalmente realiza una inundación de la trama por los puertos correspondientes, excepto el de entrada.

### ¿Qué es la tabla MAC?

La **tabla de direcciones MAC** es una tabla que mantiene el switch para relacionar direcciones MAC con los puertos donde se encuentran los dispositivos.

### ¿Cómo aprende el switch las direcciones MAC?

1. El switch recibe una trama Ethernet.
2. Examina la dirección MAC de origen.
3. Identifica el puerto por el que recibió la trama.
4. Registra la asociación entre la dirección MAC y el puerto.
5. Utiliza esa información para futuras comunicaciones.

### Ejemplo de tabla MAC

| Dirección MAC | Puerto |
|---|---|
| AA:AA:AA:AA:AA:01 | Fa0/1 |
| BB:BB:BB:BB:BB:02 | Fa0/2 |
| CC:CC:CC:CC:CC:03 | Fa0/3 |

**Ejemplo:**

Si el switch recibe una trama destinada a la dirección MAC que conoce en Fa0/2, puede reenviarla directamente por ese puerto.

**IMPORTANTE:** el switch aprende las direcciones MAC observando las direcciones de origen de las tramas recibidas.

---

## Comunicación full-duplex

### ¿Qué significa full-duplex?

**Full-duplex** permite enviar y recibir información simultáneamente en una conexión.

En enlaces Ethernet conmutados que utilizan full-duplex, no se producen las colisiones propias de Ethernet compartido.

### ¿Qué significa half-duplex?

**Half-duplex** permite transmitir en ambas direcciones, pero no simultáneamente.

**PARA RECORDAR:**

- Half-duplex = transmitir o recibir, pero no ambos simultáneamente.
- Full-duplex = transmitir y recibir simultáneamente.

---

# DIFERENCIAS ENTRE HUB Y SWITCH

| Característica | Hub | Switch |
|---|---|---|
| Función | Repite señales | Reenvía tramas |
| Capa OSI | Física (1) | Enlace de datos (2) |
| Direcciones MAC | No utiliza tabla MAC | Utiliza tabla MAC |
| Colisiones | Pueden ocurrir | No ocurren en enlaces full-duplex |
| Rendimiento | Menor en redes compartidas | Generalmente mejor |
| Uso actual | Obsoleto | Común en redes LAN |

**IDEA CLAVE:**

El hub repite señales entre sus puertos.

El switch utiliza las direcciones MAC para decidir por dónde reenviar las tramas.

---

# EJEMPLO PRÁCTICO — COMUNICACIÓN ENTRE DOS PC

Imagina una red formada por:

- PC1.
- PC2.
- Switch Ethernet.

### Funcionamiento simplificado

1. PC1 necesita enviar información a PC2.
2. PC1 crea una trama Ethernet con una MAC de origen y una MAC de destino.
3. La trama llega al switch.
4. El switch aprende la MAC de PC1 mediante el puerto de entrada.
5. El switch consulta la dirección MAC de PC2.
6. Si conoce su puerto, reenvía la trama directamente.
7. PC2 recibe la trama.

Si el switch aún no conoce el puerto correspondiente a PC2, puede inundar la trama para intentar entregarla.

**PARA RECORDAR:**

El switch utiliza principalmente las direcciones MAC para reenviar tramas dentro de la LAN.

---

# GLOSARIO — MÓDULO 7

| Término | Significado |
|---|---|
| Encapsulación | Agregar información de control a los datos. |
| Desencapsulación | Procesar y retirar la información de control correspondiente. |
| Trama | Unidad de datos de la capa de enlace. |
| Ethernet | Tecnología de comunicación de redes LAN. |
| MAC | Media Access Control. |
| Dirección MAC | Dirección utilizada para identificar interfaces en el enlace. |
| Hub | Concentrador que repite señales. |
| Switch | Dispositivo que reenvía tramas utilizando direcciones MAC. |
| Tabla MAC | Asociación de direcciones MAC con puertos del switch. |
| Colisión | Interferencia entre transmisiones simultáneas sobre un medio compartido. |
| Full-duplex | Transmisión y recepción simultáneas. |
| Half-duplex | Transmisión en ambas direcciones, no simultánea. |
| FCS | Frame Check Sequence, utilizada para detectar errores. |
| IPv6 | Versión 6 del Protocolo de Internet. |

---

# RESUMEN GENERAL — MÓDULO 7

1. La encapsulación agrega información de control a los datos para transmitirlos.
2. La desencapsulación es el proceso inverso realizado durante la recepción.
3. Una trama Ethernet incluye direcciones MAC de origen y destino.
4. Ethernet establece reglas relacionadas con el formato y transmisión de tramas.
5. El encabezado IPv6 contiene campos de direccionamiento y control.
6. La capa de acceso conecta los hosts con la infraestructura de red.
7. Un hub repite señales entre sus puertos.
8. En redes compartidas mediante hubs pueden ocurrir colisiones.
9. Un switch Ethernet tradicional trabaja principalmente en la capa 2 del modelo OSI.
10. El switch consulta la dirección MAC de destino para reenviar tramas.
11. La tabla MAC relaciona direcciones MAC con puertos.
12. El switch aprende direcciones MAC examinando la dirección de origen de las tramas.
13. Full-duplex permite transmitir y recibir simultáneamente.
14. Los switches modernos mejoran el rendimiento y eliminan las colisiones en enlaces full-duplex.

**IDEA FINAL:**

Las tramas Ethernet permiten transportar información dentro de una red local. Los switches utilizan direcciones MAC para aprender dónde están conectados los dispositivos y reenviar los mensajes hacia sus destinos.

---

# CUESTIONARIO — MÓDULO 7

**Total:** 10 preguntas
**Puntaje máximo:** 10 puntos

**Instrucciones:** Selecciona la respuesta correcta. En las preguntas indicadas, elige varias opciones.

## PREGUNTA 1

¿Qué término describe el proceso de agregar información de control a los datos antes de transmitirlos?

- [ ] A. Desencapsulación
- [ ] B. Encapsulación
- [ ] C. Fragmentación
- [ ] D. Sincronización

## PREGUNTA 2

¿Cuáles son campos o elementos presentes en una trama Ethernet? (Selecciona tres).

- [ ] A. Dirección MAC de origen
- [ ] B. Dirección MAC de destino
- [ ] C. Secuencia de verificación de trama (FCS)
- [ ] D. Contraseña del usuario

## PREGUNTA 3

¿Qué capa del modelo OSI utiliza las tramas Ethernet?

- [ ] A. Capa física
- [ ] B. Capa de enlace de datos
- [ ] C. Capa de transporte
- [ ] D. Capa de aplicación

## PREGUNTA 4

¿Cuál es una característica de un concentrador Ethernet (hub)?

- [ ] A. Utiliza una tabla de direcciones MAC.
- [ ] B. Encaminan paquetes mediante IP.
- [ ] C. Repite las señales hacia otros puertos.
- [ ] D. Asigna direcciones IP automáticamente.

## PREGUNTA 5

¿Qué dispositivo Ethernet utiliza una tabla de direcciones MAC para reenviar tramas?

- [ ] A. Hub
- [ ] B. Switch
- [ ] C. Cable UTP
- [ ] D. Módem telefónico

## PREGUNTA 6

¿Qué dirección examina un switch para aprender en qué puerto está conectado un dispositivo?

- [ ] A. Dirección IP de destino
- [ ] B. Dirección MAC de origen
- [ ] C. Dirección DNS
- [ ] D. Dirección del gateway

## PREGUNTA 7

¿Qué hace normalmente un switch cuando recibe una trama unicast y conoce el puerto asociado con la MAC de destino?

- [ ] A. Reenvía la trama por el puerto correspondiente.
- [ ] B. Repite la trama por todos los puertos.
- [ ] C. Apaga los puertos de la LAN.
- [ ] D. Elimina todas las direcciones MAC.

## PREGUNTA 8

¿Qué característica describe una conexión Ethernet full-duplex?

- [ ] A. Solo permite transmitir.
- [ ] B. Solo permite recibir.
- [ ] C. Permite transmitir y recibir simultáneamente.
- [ ] D. Necesita colisiones para funcionar.

## PREGUNTA 9

Un switch Ethernet aprende direcciones MAC observando la MAC de origen de las tramas recibidas.

- [ ] A. Verdadero
- [ ] B. Falso

## PREGUNTA 10

Los hubs y los switches utilizan exactamente el mismo mecanismo para determinar dónde enviar las tramas Ethernet.

- [ ] A. Verdadero
- [ ] B. Falso

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
**Respuesta: B. Encapsulación.**

La encapsulación agrega información de control a los datos para permitir su transmisión.

### PREGUNTA 2
**Respuesta: A, B y C.**

Las tramas Ethernet incluyen direcciones MAC de origen y destino y un campo FCS utilizado para detectar errores.

### PREGUNTA 3
**Respuesta: B. Capa de enlace de datos.**

Las tramas corresponden a la capa 2 del modelo OSI.

### PREGUNTA 4
**Respuesta: C. Repite las señales hacia otros puertos.**

Un hub repite señales y no utiliza una tabla MAC para decidir el puerto de destino.

### PREGUNTA 5
**Respuesta: B. Switch.**

El switch examina direcciones MAC y utiliza su tabla para reenviar tramas.

### PREGUNTA 6
**Respuesta: B. Dirección MAC de origen.**

El switch aprende qué direcciones MAC están asociadas con sus puertos observando las tramas recibidas.

### PREGUNTA 7
**Respuesta: A. Reenvía la trama por el puerto correspondiente.**

Cuando el switch conoce la ubicación de la MAC de destino, puede enviar la trama directamente hacia ese puerto.

### PREGUNTA 8
**Respuesta: C. Permite transmitir y recibir simultáneamente.**

Full-duplex permite comunicación simultánea en ambas direcciones.

### PREGUNTA 9
**Respuesta: A. Verdadero.**

Los switches aprenden direcciones MAC examinando la dirección de origen de las tramas.

### PREGUNTA 10
**Respuesta: B. Falso.**

El hub repite señales, mientras que el switch utiliza direcciones MAC para decidir cómo reenviar las tramas.

---

**PUNTAJE FINAL: ____ / 10**

# CONCEPTOS QUE DEBES DOMINAR ANTES DEL MÓDULO 8

- Encapsulación y desencapsulación.
- Función de una trama Ethernet.
- Direcciones MAC de origen y destino.
- Función del campo FCS.
- Diferencia entre hub y switch.
- Funcionamiento de la tabla MAC.
- Aprendizaje de direcciones MAC.
- Colisiones Ethernet.
- Diferencia entre half-duplex y full-duplex.
- Función de la capa de acceso.
