
# CISCO NETWORKING BASICS
## MÓDULO 11 — DIRECCIONAMIENTO DINÁMICO CON DHCP

**Objetivo:** Comprender cómo se asignan las direcciones IPv4 de manera estática y dinámica, cómo funciona DHCP y cómo los dispositivos obtienen automáticamente su configuración de red.

---

# 11.1 — DIRECCIONAMIENTO ESTÁTICO Y DINÁMICO

## 11.1.1 — ASIGNACIÓN DE DIRECCIONES IPv4 ESTÁTICAS

### ¿Qué es una dirección IP estática?

Una **dirección IPv4 estática** es una dirección que el administrador configura manualmente en la interfaz de red de un dispositivo.

Esta configuración permanece estable hasta que se modifica.

### ¿Qué información se configura?

Como mínimo:

1. **Dirección IPv4:** identifica la interfaz del dispositivo dentro de la red.
2. **Máscara de subred:** identifica la porción de red y la porción de host.
3. **Puerta de enlace predeterminada (Default Gateway):** permite enviar paquetes hacia otras redes.

También puede configurarse información de DNS.

### Ejemplo

Una computadora utiliza:

- IP: 192.168.1.10
- Máscara: 255.255.255.0
- Gateway: 192.168.1.1
- DNS: 8.8.8.8

El administrador introduce estos valores manualmente.

### ¿Cuándo se recomienda utilizar IP estática?

Es útil en dispositivos que necesitan mantener una dirección conocida.

**Ejemplos:**

- Servidores.
- Impresoras de red.
- Interfaces de administración.
- Otros equipos que requieren una dirección estable.

### Ventajas

- Mayor control sobre el direccionamiento.
- Dirección conocida y estable.
- Facilita el acceso a servicios que dependen de una dirección determinada.

### Desventajas

- Se requiere configuración manual.
- Puede tomar mucho tiempo configurar numerosos hosts.
- Existe riesgo de errores de configuración.
- Es necesario mantener un registro de direcciones asignadas.

**IMPORTANTE:**

Cuando se utilizan direcciones IPv4 estáticas, el administrador debe evitar asignar la misma dirección a dos dispositivos dentro de la misma red.

---

## 11.1.2 — ASIGNACIÓN DINÁMICA DE DIRECCIONES IPv4

### ¿Qué es una dirección IP dinámica?

Una **dirección IPv4 dinámica** es una dirección que un dispositivo puede obtener automáticamente mediante un servidor DHCP.

### ¿Qué es DHCP?

**DHCP (Dynamic Host Configuration Protocol)** significa Protocolo de Configuración Dinámica de Host.

Permite asignar automáticamente información de red a los dispositivos clientes.

### ¿Qué información puede proporcionar DHCP?

- Dirección IPv4.
- Máscara de subred.
- Puerta de enlace predeterminada.
- Servidores DNS.
- Tiempo de arrendamiento de la dirección.

### ¿Cómo funciona?

1. Un dispositivo se conecta a la red.
2. El cliente DHCP busca un servidor DHCP.
3. El servidor ofrece una configuración IP.
4. El cliente solicita utilizar esa configuración.
5. El servidor confirma la asignación.
6. El dispositivo puede comunicarse mediante su configuración IP.

### Ejemplo

Un estudiante conecta su laptop al Wi-Fi de una universidad.

La laptop puede recibir automáticamente:

- IP: 192.168.10.25
- Máscara: 255.255.255.0
- Gateway: 192.168.10.1
- DNS: dirección proporcionada por la red

No es necesario que el estudiante configure manualmente estos datos.

### Ventajas de DHCP

- Automatiza la asignación de direcciones.
- Reduce el trabajo administrativo.
- Disminuye errores de configuración manual.
- Facilita la conexión de nuevos dispositivos.
- Permite administrar direcciones mediante arrendamientos.

**IMPORTANTE:**

DHCP es especialmente útil en redes donde los dispositivos se conectan y desconectan frecuentemente.

---

# ¿QUÉ ES UN POOL DHCP?

Un **pool DHCP** es un conjunto o rango de direcciones IP que el servidor puede asignar a sus clientes.

### Ejemplo

Red: 192.168.1.0/24

Router: 192.168.1.1

Pool DHCP:

192.168.1.100 hasta 192.168.1.200

Los dispositivos clientes pueden recibir direcciones disponibles dentro de ese rango.

### Ejemplo de asignación

| Dispositivo | Dirección asignada |
|---|---|
| Laptop 1 | 192.168.1.100 |
| Celular 1 | 192.168.1.101 |
| Laptop 2 | 192.168.1.102 |
| Celular 2 | 192.168.1.103 |

**IMPORTANTE:**

El servidor DHCP administra la asignación de direcciones para evitar conflictos dentro del rango que controla.

---

# ¿QUÉ ES EL ARRENDAMIENTO DHCP?

**Lease (arrendamiento)** es el período durante el cual un cliente tiene asignada una dirección IPv4 mediante DHCP.

### ¿Cómo funciona?

1. El servidor asigna una dirección IP.
2. La dirección tiene un tiempo de arrendamiento.
3. El cliente normalmente intenta renovar el arrendamiento antes de que expire.
4. Si el arrendamiento termina sin renovarse, la dirección puede volver a estar disponible.

### Ejemplo

Una laptop recibe:

IP: 192.168.1.105

Arrendamiento: 24 horas.

La laptop puede solicitar la renovación antes de que termine ese período.

**PARA RECORDAR:**

- IP estática = configuración manual.
- IP dinámica = configuración automática.
- Pool DHCP = conjunto de direcciones disponibles.
- Lease = tiempo de arrendamiento.

---

## 11.1.3 — SERVIDORES DHCP

### ¿Qué es un servidor DHCP?

Un **servidor DHCP** es un dispositivo o servicio que proporciona automáticamente parámetros de configuración IP a los clientes.

### ¿Qué dispositivos pueden funcionar como servidor DHCP?

- Servidores dedicados.
- Routers domésticos.
- Routers empresariales compatibles.

### DHCP en una red doméstica

En muchos hogares, el router inalámbrico cumple dos funciones:

**1. Cliente DHCP**

Solicita una configuración IP al ISP mediante su interfaz WAN, cuando el proveedor utiliza DHCP.

**2. Servidor DHCP**

Proporciona direcciones IPv4 privadas a los dispositivos de la LAN.

### Ejemplo

ISP
 |
 | Configuración IPv4 para WAN
 |
Router doméstico
 |
 | DHCP para la LAN
 |
 +-- PC: 192.168.1.100
 +-- Laptop: 192.168.1.101
 +-- Celular: 192.168.1.102

### ¿Qué ocurre cuando conectas tu celular al Wi-Fi?

1. El celular se conecta a la WLAN.
2. Solicita configuración mediante DHCP, si está configurado para usarlo.
3. El router responde como servidor DHCP.
4. El celular recibe su dirección IPv4 y otros parámetros.
5. Puede utilizar los servicios de la red.

**IDEA CLAVE:**

Un mismo router doméstico puede funcionar como cliente DHCP en su interfaz WAN y servidor DHCP en su red LAN.

---

# 11.2 — CONFIGURACIÓN DE DHCPv4

## ¿QUÉ ES DHCPv4?

**DHCPv4** es el protocolo DHCP utilizado para proporcionar configuración de direccionamiento IPv4.

### ¿Cómo obtiene un cliente su dirección?

El proceso inicial habitual se conoce como **DORA**.

DORA representa cuatro mensajes:

1. Discover.
2. Offer.
3. Request.
4. Acknowledgment.

---

## PROCESO DORA — DHCP

### 1. DHCP DISCOVER

**¿Qué hace?**

El cliente busca servidores DHCP disponibles.

Como todavía no dispone de una configuración IPv4, normalmente transmite un mensaje de difusión.

**Dirección IP de destino:**

255.255.255.255

**Dirección MAC Ethernet de destino:**

FF:FF:FF:FF:FF:FF

**Ejemplo:**

Laptop → Difusión DHCP Discover

El cliente está buscando un servidor DHCP.

---

### 2. DHCP OFFER

**¿Qué hace?**

Un servidor DHCP responde ofreciendo una configuración IPv4 al cliente.

**Ejemplo:**

Servidor DHCP:

"Te ofrezco la dirección 192.168.1.100".

La oferta puede incluir también la máscara, la puerta de enlace y otros parámetros.

---

### 3. DHCP REQUEST

**¿Qué hace?**

El cliente solicita utilizar la configuración ofrecida por el servidor.

**Ejemplo:**

Laptop:

"Solicito utilizar la dirección 192.168.1.100".

---

### 4. DHCP ACK

**¿Qué hace?**

El servidor confirma el arrendamiento de la dirección IPv4.

**ACK** significa Acknowledgment, es decir, confirmación o acuse de recibo.

**Ejemplo:**

Servidor DHCP:

"Confirmo la asignación de 192.168.1.100".

---

## RESUMEN DEL PROCESO DORA

| Etapa | Mensaje | Función |
|---|---|---|
| D | Discover | Buscar servidor DHCP. |
| O | Offer | Ofrecer configuración IP. |
| R | Request | Solicitar la configuración ofrecida. |
| A | ACK | Confirmar la asignación. |

### Ejemplo completo

CLIENTE                         SERVIDOR DHCP

Discover ---------------------->

          <-------------------- Offer

Request ----------------------->

          <-------------------- ACK

### ¿Qué obtiene finalmente el cliente?

Una configuración como:

- IP: 192.168.1.100
- Máscara: 255.255.255.0
- Gateway: 192.168.1.1
- DNS: 192.168.1.1

**IMPORTANTE PARA CISCO:**

El orden correcto es:

**DISCOVER → OFFER → REQUEST → ACK**

---

# CONFIGURACIÓN DHCP EN UN ROUTER DOMÉSTICO

Cisco explica que muchos routers domésticos incorporan DHCP habilitado de manera predeterminada.

### Ejemplo de configuración

Dirección LAN del router:

192.168.0.1

Máscara:

255.255.255.0

Servidor DHCP:

Habilitado.

### Funcionamiento

El router puede asignar direcciones privadas a los dispositivos conectados a la red.

**Ejemplo:**

- Router: 192.168.0.1
- PC: 192.168.0.100
- Laptop: 192.168.0.101
- Celular: 192.168.0.102

Estos valores son ilustrativos; los rangos predeterminados dependen del fabricante.

---

# COMPARACIÓN — IP ESTÁTICA VS IP DINÁMICA

| Característica | Estática | Dinámica |
|---|---|---|
| Asignación | Manual | Automática |
| Necesita DHCP | No | Generalmente sí |
| Dirección | Permanece configurada | Depende del arrendamiento |
| Administración | Manual | Automatizada |
| Uso común | Servidores e impresoras | PC, laptops y celulares |
| Riesgo de errores manuales | Mayor | Menor |

**PARA RECORDAR:**

- Estática = administrador configura.
- Dinámica = DHCP asigna.
- Servidor DHCP = proporciona configuración.
- Cliente DHCP = solicita configuración.

---

# EJEMPLO PRÁCTICO EN CISCO PACKET TRACER

## Configurar una PC para utilizar DHCP

### Paso 1

Selecciona la computadora.

### Paso 2

Ingresa a:

Desktop → IP Configuration

### Paso 3

Selecciona:

**DHCP**

### Paso 4

La computadora intentará obtener automáticamente:

- Dirección IPv4.
- Máscara.
- Gateway.
- DNS, si el servidor lo proporciona.

### Paso 5

Verifica que los valores se hayan asignado correctamente.

**IMPORTANTE:**

Debe existir un servidor DHCP disponible para que la computadora obtenga su configuración automáticamente.

---

# GLOSARIO — MÓDULO 11

| Término | Significado |
|---|---|
| IP estática | Dirección configurada manualmente. |
| IP dinámica | Dirección obtenida automáticamente. |
| DHCP | Dynamic Host Configuration Protocol. |
| DHCPv4 | DHCP utilizado con IPv4. |
| Cliente DHCP | Dispositivo que solicita configuración IP. |
| Servidor DHCP | Servicio que proporciona configuración IP. |
| Pool DHCP | Rango de direcciones disponibles. |
| Lease | Arrendamiento temporal de dirección IP. |
| DHCP Discover | Mensaje para descubrir servidores DHCP. |
| DHCP Offer | Oferta de configuración IP. |
| DHCP Request | Solicitud de la configuración ofrecida. |
| DHCP ACK | Confirmación de asignación. |
| Gateway | Puerta de enlace predeterminada. |
| DNS | Sistema de Nombres de Dominio. |
| Broadcast | Comunicación dirigida a todos los hosts del dominio correspondiente. |

---

# RESUMEN GENERAL — MÓDULO 11

1. Las direcciones IPv4 pueden asignarse de manera estática o dinámica.
2. La asignación estática requiere configuración manual.
3. Una configuración IP incluye dirección IPv4, máscara y gateway.
4. Las direcciones estáticas son útiles para servidores e impresoras.
5. DHCP permite asignar automáticamente parámetros de red.
6. DHCP reduce el trabajo administrativo y los errores manuales.
7. Las direcciones DHCP normalmente se asignan mediante arrendamientos.
8. Un pool DHCP contiene direcciones disponibles para los clientes.
9. Los routers domésticos pueden funcionar como clientes y servidores DHCP.
10. Un router puede obtener su configuración WAN del ISP mediante DHCP.
11. El router puede proporcionar direcciones privadas a la LAN.
12. DHCP Discover busca servidores disponibles.
13. DHCP Offer ofrece una configuración.
14. DHCP Request solicita utilizar una configuración.
15. DHCP ACK confirma la asignación.
16. El proceso inicial DHCP se conoce como DORA.
17. Un cliente puede utilizar difusión para descubrir un servidor DHCP.
18. Muchos routers domésticos tienen DHCP habilitado por defecto.

**IDEA FINAL:**

DHCP automatiza la configuración IPv4 de los dispositivos. En lugar de configurar manualmente cada equipo, un servidor DHCP administra un conjunto de direcciones y las asigna a los clientes mediante un proceso de solicitud, oferta y confirmación.

---

# CUESTIONARIO — MÓDULO 11

**Total:** 10 preguntas
**Puntaje máximo:** 10 puntos

**Instrucciones:** Selecciona la respuesta correcta. Las alternativas están sin marcar. Revisa el solucionario únicamente al terminar.

## PREGUNTA 1

¿Qué método permite configurar manualmente una dirección IPv4 en una computadora?

- [ ] A. DHCP
- [ ] B. Direccionamiento estático
- [ ] C. DNS
- [ ] D. NAT

## PREGUNTA 2

¿Cuáles de los siguientes parámetros forman parte de la configuración IPv4 básica de un host? (Selecciona tres).

- [ ] A. Dirección IPv4
- [ ] B. Máscara de subred
- [ ] C. Puerta de enlace predeterminada
- [ ] D. Dirección física del monitor

## PREGUNTA 3

¿Qué protocolo permite asignar automáticamente direcciones IPv4 a los hosts?

- [ ] A. ARP
- [ ] B. DNS
- [ ] C. DHCP
- [ ] D. ICMP

## PREGUNTA 4

¿Qué tipo de dispositivo suele beneficiarse de una dirección IPv4 estática?

- [ ] A. Impresora de red
- [ ] B. Teléfono de un visitante
- [ ] C. Laptop temporal de un estudiante
- [ ] D. Dispositivo móvil de un turista

## PREGUNTA 5

¿Qué significa el término pool DHCP?

- [ ] A. Un conjunto de cables Ethernet
- [ ] B. Un rango de direcciones IP disponibles
- [ ] C. Una tabla de direcciones MAC
- [ ] D. Una lista de contraseñas Wi-Fi

## PREGUNTA 6

¿Qué término describe el período durante el cual DHCP asigna una dirección IPv4 a un cliente?

- [ ] A. Broadcast
- [ ] B. Encapsulación
- [ ] C. Lease
- [ ] D. Routing

## PREGUNTA 7

¿Cuál es el primer mensaje del proceso inicial de asignación DHCP?

- [ ] A. DHCP Offer
- [ ] B. DHCP ACK
- [ ] C. DHCP Request
- [ ] D. DHCP Discover

## PREGUNTA 8

¿Cuál es el orden correcto de los mensajes DORA?

- [ ] A. Discover, Request, Offer, ACK
- [ ] B. Offer, Discover, ACK, Request
- [ ] C. Discover, Offer, Request, ACK
- [ ] D. Request, Offer, Discover, ACK

## PREGUNTA 9

¿Qué dirección IPv4 de destino utiliza normalmente un cliente DHCP en su mensaje inicial Discover?

- [ ] A. 127.0.0.1
- [ ] B. 255.255.255.255
- [ ] C. 224.0.0.5
- [ ] D. 192.168.1.1

## PREGUNTA 10

Un router doméstico puede actuar como cliente DHCP para obtener una configuración IP del ISP y como servidor DHCP para los dispositivos de su LAN.

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
**Respuesta: B. Direccionamiento estático.**

La asignación estática requiere introducir manualmente los parámetros de direccionamiento.

### PREGUNTA 2
**Respuesta: A, B y C.**

Una configuración IPv4 básica incluye dirección IP, máscara de subred y puerta de enlace predeterminada.

### PREGUNTA 3
**Respuesta: C. DHCP.**

DHCP permite asignar automáticamente direcciones IPv4 y otros parámetros de configuración.

### PREGUNTA 4
**Respuesta: A. Impresora de red.**

Una dirección estable facilita que otros dispositivos encuentren la impresora.

### PREGUNTA 5
**Respuesta: B. Un rango de direcciones IP disponibles.**

El pool DHCP contiene las direcciones que pueden asignarse a los clientes.

### PREGUNTA 6
**Respuesta: C. Lease.**

Lease significa arrendamiento y representa el período de asignación de una dirección IP.

### PREGUNTA 7
**Respuesta: D. DHCP Discover.**

El cliente transmite inicialmente un mensaje Discover para localizar servidores DHCP.

### PREGUNTA 8
**Respuesta: C. Discover, Offer, Request, ACK.**

Es el orden correcto del proceso DORA.

### PREGUNTA 9
**Respuesta: B. 255.255.255.255.**

Es la dirección IPv4 de broadcast limitado utilizada normalmente en el descubrimiento inicial DHCP.

### PREGUNTA 10
**Respuesta: A. Verdadero.**

Muchos routers domésticos obtienen una configuración WAN del ISP mediante DHCP y proporcionan configuración IP a sus dispositivos internos.

---

**PUNTAJE FINAL: ____ / 10**

# CONCEPTOS QUE DEBES DOMINAR ANTES DEL MÓDULO 12

- Direccionamiento IPv4 estático.
- Direccionamiento IPv4 dinámico.
- Diferencias entre IP estática y dinámica.
- Funciones de DHCP.
- Cliente DHCP y servidor DHCP.
- Pool de direcciones DHCP.
- Arrendamiento (Lease).
- Proceso DORA.
- DHCP Discover, Offer, Request y ACK.
- DHCP en routers domésticos.
- Configuración de una PC mediante DHCP en Packet Tracer.
