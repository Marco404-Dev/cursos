
# Módulo 5: La Capa de Red

**Curso:** Cisco Networking Academy — Dispositivos de Red y Configuración Inicial

## 1. ¿Qué es la capa de red?

La capa de red corresponde a la **capa 3 del modelo OSI**.

Su función principal es permitir la comunicación entre dispositivos ubicados en diferentes redes.

### Protocolos importantes

| Protocolo | Función |
|---|---|
| IPv4 | Direccionamiento y transporte de paquetes mediante direcciones de 32 bits. |
| IPv6 | Direccionamiento y transporte de paquetes mediante direcciones de 128 bits. |
| ICMP | Enviar mensajes de control, diagnóstico y errores. |
| OSPF | Permitir que los routers intercambien información de enrutamiento. |

## 2. Funciones principales de la capa de red

La capa de red realiza cuatro operaciones:

| Operación | Descripción |
|---|---|
| Direccionamiento | Identifica dispositivos mediante direcciones IP. |
| Encapsulación | Agrega un encabezado IP a los datos recibidos de la capa superior. |
| Enrutamiento | Determina por dónde enviar los paquetes hacia otras redes. |
| Desencapsulación | Retira el encabezado IP cuando el paquete llega al dispositivo de destino. |

### Ejemplo

PC-A quiere comunicarse con un servidor ubicado en otra red.

1. PC-A crea un paquete con IP de origen y destino.
2. Envía la trama hacia su gateway predeterminado.
3. El router consulta su tabla de enrutamiento.
4. El paquete puede atravesar varios routers.
5. El servidor recibe el paquete y procesa la información.

**Importante:** Cada router atravesado representa un salto (hop).

## 3. Encapsulación IP

La encapsulación consiste en agregar información de control a los datos recibidos de una capa superior.

### Ejemplo con TCP

Capa 4:

`Segmento TCP`

Capa 3:

`Encabezado IP + Segmento TCP = Paquete IP`

Capa 2:

`Encabezado Ethernet + Paquete IP + FCS = Trama`

### Direcciones durante el recorrido

Supongamos:

- PC-A: `192.168.1.10`
- Servidor: `10.10.10.20`

El paquete contiene:

- IP origen: `192.168.1.10`
- IP destino: `10.10.10.20`

Normalmente, estas direcciones permanecen iguales durante el recorrido.

**Excepción:** Si existe NAT, alguna dirección IP puede modificarse.

Las direcciones MAC, en cambio, pueden cambiar en cada enlace cuando el paquete atraviesa routers.

## 4. Características del protocolo IP

IP tiene tres características fundamentales.

| Característica | Significado |
|---|---|
| Sin conexión | No necesita establecer una conexión antes de enviar paquetes. |
| Mejor esfuerzo | No garantiza que los paquetes lleguen al destino. |
| Independiente del medio | Funciona sobre diferentes tecnologías de transmisión. |

### 4.1. Sin conexión (Connectionless)

IP no establece previamente una conexión dedicada entre origen y destino.

**Ejemplo:** Es parecido a enviar una carta sin comprobar primero si el destinatario está disponible.

### 4.2. Mejor esfuerzo (Best Effort)

IP intenta entregar los paquetes, pero no garantiza:

- Que lleguen al destino.
- Que lleguen en orden.
- Que lleguen sin pérdidas.

IP tampoco retransmite automáticamente los paquetes perdidos.

**Importante:** TCP puede proporcionar mecanismos de confiabilidad y retransmisión desde la capa de transporte.

### 4.3. Independiente del medio

Los paquetes IP pueden viajar por:

- Cables de cobre.
- Fibra óptica.
- Redes inalámbricas.

IP no depende de una tecnología física específica.

## 5. MTU y fragmentación

### MTU (Maximum Transmission Unit)

Es el tamaño máximo de paquete de capa de red que puede transportar un enlace sin fragmentarlo.

**Ejemplo:** En una red Ethernet convencional, la MTU IP suele ser de 1500 bytes.

### Fragmentación IPv4

Ocurre cuando un paquete IPv4 necesita atravesar un enlace con una MTU menor que su tamaño.

Un router IPv4 puede dividir el paquete en fragmentos más pequeños si está permitido.

**Ejemplo:**

Un paquete IPv4 de 2000 bytes necesita atravesar un enlace con MTU de 1500 bytes.

Puede ser necesario fragmentarlo antes de transmitirlo.

**Importante:**

- La fragmentación puede generar sobrecarga y afectar el rendimiento.
- Si el indicador DF (Don't Fragment) está activado, el router no puede fragmentar ese paquete IPv4.
- Los routers IPv6 no fragmentan paquetes. La fragmentación IPv6, cuando se necesita, la realiza el dispositivo de origen.

## 6. Encabezado IPv4

El encabezado IPv4 contiene información necesaria para transportar paquetes entre redes.

Su tamaño es:

- Mínimo: 20 bytes.
- Máximo: 60 bytes.

### Campos principales

| Campo | Función |
|---|---|
| Versión | Identifica IPv4 mediante el valor binario `0100`. |
| IHL | Indica la longitud del encabezado. |
| DS (DiffServ) | Permite clasificar el tráfico para QoS e indicar congestión mediante ECN. |
| Longitud total | Indica el tamaño completo del paquete IPv4. |
| Identificación | Ayuda a identificar fragmentos de un paquete. |
| Indicadores | Controlan aspectos de la fragmentación. |
| Desplazamiento | Indica la posición de un fragmento. |
| TTL | Limita cuántos saltos puede realizar el paquete. |
| Protocolo | Identifica el protocolo transportado. |
| Checksum | Detecta errores en el encabezado IPv4. |
| IP origen | Dirección IPv4 del emisor. |
| IP destino | Dirección IPv4 del destinatario. |

## 7. TTL (Time to Live)

TTL es un campo de 8 bits del encabezado IPv4.

Su función es evitar que los paquetes circulen indefinidamente por una red.

### ¿Cómo funciona?

Cada router que reenvía el paquete reduce el TTL en 1.

**Ejemplo:**

| Dispositivo | TTL |
|---|---|
| PC origen | 64 |
| Router R1 | 63 |
| Router R2 | 62 |
| Router R3 | 61 |

Si el TTL llega a 0, el router descarta el paquete.

Normalmente, envía un mensaje **ICMP Time Exceeded** al origen.

**Importante:** El comando `tracert` o `traceroute` aprovecha este comportamiento para descubrir los routers que atraviesa un paquete.

## 8. Campo Protocolo en IPv4

Permite identificar qué protocolo contiene el paquete IPv4.

### Valores importantes

| Valor decimal | Protocolo |
|---|---|
| 1 | ICMP |
| 6 | TCP |
| 17 | UDP |

**Ejemplo:**

Si el campo Protocolo contiene `6`, el paquete transporta TCP.

Si contiene `17`, transporta UDP.

## 9. Limitaciones de IPv4

IPv4 presenta tres limitaciones principales.

### 9.1. Agotamiento de direcciones

IPv4 tiene 32 bits.

Cantidad teórica de direcciones:

`2^32 = 4,294,967,296`

No todas están disponibles como direcciones públicas utilizables.

El crecimiento de Internet ha provocado el agotamiento de los bloques IPv4 disponibles para nuevas asignaciones generales.

### 9.2. Falta de conectividad directa extremo a extremo

En IPv4 se utiliza NAT para permitir que varios dispositivos privados compartan una dirección pública.

**Ejemplo:**

Varios dispositivos de una casa utilizan una misma IPv4 pública para acceder a Internet.

NAT puede complicar las conexiones directas entrantes entre dispositivos.

### 9.3. Mayor complejidad

El uso de NAT y otros mecanismos adicionales puede dificultar la configuración y solución de problemas de red.

## 10. IPv6

IPv6 se desarrolló para superar varias limitaciones de IPv4.

### Ventajas

- Direcciones de 128 bits.
- Espacio de direccionamiento mucho mayor.
- Encabezado básico simplificado.
- Facilita la conectividad extremo a extremo sin necesitar NAT para conservar direcciones.
- Mejoras en el procesamiento de paquetes.

### Comparación IPv4 vs. IPv6

| Característica | IPv4 | IPv6 |
|---|---|---|
| Longitud | 32 bits | 128 bits |
| Representación | Decimal | Hexadecimal |
| Encabezado | 20-60 bytes | 40 bytes fijos |
| Campo de saltos | TTL | Hop Limit |
| Checksum de encabezado | Sí | No |
| Fragmentación por routers | Posible | No |
| NAT para conservar direcciones | Frecuente | Generalmente innecesario |

### Ejemplo de IPv6

`2001:DB8::1`

El espacio IPv6 contiene:

`2^128`

posibles direcciones.

Es una cantidad enormemente superior a IPv4.

## 11. Encabezado IPv6

El encabezado básico IPv6 tiene un tamaño fijo de **40 bytes**.

### Campos principales

| Campo | Tamaño | Función |
|---|---|---|
| Versión | 4 bits | Identifica IPv6 mediante `0110`. |
| Clase de tráfico | 8 bits | Permite clasificar y priorizar tráfico. |
| Etiqueta de flujo | 20 bits | Identifica paquetes pertenecientes a un mismo flujo. |
| Longitud de carga útil | 16 bits | Indica la longitud de la carga útil, sin incluir el encabezado básico. |
| Siguiente encabezado | 8 bits | Identifica otro encabezado o protocolo superior. |
| Límite de saltos | 8 bits | Limita la cantidad de routers que puede atravesar. |
| IPv6 origen | 128 bits | Dirección del emisor. |
| IPv6 destino | 128 bits | Dirección del destinatario. |

### Diferencias importantes

**IPv4 utiliza TTL.**

**IPv6 utiliza Hop Limit.**

Ambos evitan que los paquetes circulen indefinidamente.

IPv6 no incluye checksum en su encabezado básico, por lo que los routers no necesitan recalcularlo al disminuir el límite de saltos.

## 12. Encabezados de extensión IPv6

IPv6 puede incorporar encabezados de extensión (Extension Headers o EH).

Se colocan después del encabezado IPv6 básico y antes de los datos de las capas superiores.

Pueden utilizarse para:

- Fragmentación realizada por el origen.
- Funciones de seguridad.
- Opciones adicionales.
- Determinadas funciones de movilidad.

**Importante:** Los encabezados de extensión son opcionales y no cambian el tamaño fijo de 40 bytes del encabezado básico IPv6.

---

# 10 preguntas de repaso — Módulo 5

### 1. ¿Cuál es la función principal de la capa de red?

A) Administrar los puertos TCP y UDP.  
B) Permitir la comunicación entre dispositivos a través de diferentes redes.  
C) Convertir señales eléctricas en bits.  
D) Identificar dispositivos únicamente mediante direcciones MAC.

<details>
<summary>Ver respuesta</summary>

✅ **B) Permitir la comunicación entre dispositivos a través de diferentes redes.**

La capa 3 utiliza direccionamiento IP y enrutamiento para transportar paquetes entre redes.

</details>

### 2. ¿Cuáles son las cuatro operaciones principales de la capa de red?

A) Cifrado, compresión, autenticación y sincronización.  
B) Difusión, conmutación, filtrado y aprendizaje.  
C) Direccionamiento, encapsulación, enrutamiento y desencapsulación.  
D) Segmentación, confirmación, retransmisión y control de flujo.

<details>
<summary>Ver respuesta</summary>

✅ **C) Direccionamiento, encapsulación, enrutamiento y desencapsulación.**

Son las cuatro operaciones fundamentales de la capa de red.

</details>

### 3. ¿Qué significa que IP sea un protocolo de mejor esfuerzo?

A) Que no garantiza la entrega de los paquetes.  
B) Que establece una conexión antes de transmitir.  
C) Que retransmite automáticamente los paquetes perdidos.  
D) Que todos los paquetes llegan siempre en orden.

<details>
<summary>Ver respuesta</summary>

✅ **A) Que no garantiza la entrega de los paquetes.**

IP intenta entregar los paquetes, pero no garantiza su recepción.

TCP puede ofrecer mecanismos de confiabilidad cuando se necesitan.

</details>

### 4. ¿Qué ocurre cuando el TTL de un paquete IPv4 llega a cero durante el enrutamiento?

A) El paquete regresa automáticamente al origen.  
B) El router aumenta el TTL nuevamente.  
C) El paquete se convierte en una trama broadcast.  
D) El router descarta el paquete y normalmente envía ICMP Time Exceeded.

<details>
<summary>Ver respuesta</summary>

✅ **D) El router descarta el paquete y normalmente envía ICMP Time Exceeded.**

TTL evita que los paquetes circulen indefinidamente en caso de bucles de enrutamiento.

</details>

### 5. ¿Qué valor en el campo Protocolo IPv4 identifica TCP?

A) 1.  
B) 6.  
C) 17.  
D) 80.

<details>
<summary>Ver respuesta</summary>

✅ **B) 6.**

Valores importantes:

- ICMP = 1.
- TCP = 6.
- UDP = 17.

</details>

### 6. ¿Qué significa MTU?

A) Maximum Transfer User.  
B) Media Transmission Utility.  
C) Maximum Transmission Unit.  
D) Multiple Transport Unit.

<details>
<summary>Ver respuesta</summary>

✅ **C) Maximum Transmission Unit.**

Indica el tamaño máximo que puede transportar un enlace para la unidad de datos correspondiente sin fragmentación.

</details>

### 7. ¿Cuál es una diferencia importante entre IPv4 e IPv6 respecto a la fragmentación?

A) Los routers IPv4 pueden fragmentar paquetes en determinadas condiciones, pero los routers IPv6 no lo hacen.  
B) IPv6 siempre fragmenta todos sus paquetes.  
C) Los routers IPv6 fragmentan paquetes automáticamente.  
D) Ninguna versión de IP permite fragmentación.

<details>
<summary>Ver respuesta</summary>

✅ **A) Los routers IPv4 pueden fragmentar paquetes en determinadas condiciones, pero los routers IPv6 no lo hacen.**

En IPv6, la fragmentación debe realizarla el dispositivo de origen cuando es necesaria.

</details>

### 8. ¿Cuál de las siguientes es una limitación importante de IPv4?

A) Tiene direcciones de 128 bits.  
B) No permite utilizar routers.  
C) No admite redes Ethernet.  
D) Posee un espacio limitado de direcciones públicas.

<details>
<summary>Ver respuesta</summary>

✅ **D) Posee un espacio limitado de direcciones públicas.**

IPv4 utiliza 32 bits y tiene aproximadamente 4.290 millones de direcciones teóricas.

</details>

### 9. ¿Qué campo de IPv6 reemplaza funcionalmente al TTL de IPv4?

A) Flow Label.  
B) Hop Limit.  
C) Next Header.  
D) Payload Length.

<details>
<summary>Ver respuesta</summary>

✅ **B) Hop Limit.**

Hop Limit se reduce en uno por cada router que reenvía el paquete.

Si llega a cero, el paquete se descarta.

</details>

### 10. ¿Cuál es el tamaño del encabezado básico de IPv6?

A) 20 bytes variables.  
B) 60 bytes fijos.  
C) 40 bytes fijos.  
D) 128 bytes fijos.

<details>
<summary>Ver respuesta</summary>

✅ **C) 40 bytes fijos.**

IPv6 utiliza un encabezado básico simplificado de 40 bytes.

Los encabezados de extensión son opcionales y se agregan por separado.

</details>

---

**Fin del Módulo 5 — La Capa de Red**
