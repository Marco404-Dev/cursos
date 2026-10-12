
# CISCO NETWORKING BASICS
## MÓDULO 9 — IPv4 Y SEGMENTACIÓN DE REDES

**Objetivo:** Comprender los tipos de comunicación IPv4, distinguir las direcciones públicas, privadas y especiales, y explicar por qué se segmentan las redes en subredes.

---

# 9.1 — TIPOS DE COMUNICACIÓN IPv4

En IPv4 existen tres métodos principales para enviar información:

1. **Unidifusión (Unicast):** comunicación de uno a uno.
2. **Difusión (Broadcast):** comunicación de uno a todos dentro de una red.
3. **Multidifusión (Multicast):** comunicación de uno a un grupo determinado.

---

## 9.1.2 — UNIDIFUSIÓN (UNICAST)

### ¿Qué es unicast?

**Unicast** es una comunicación en la que un dispositivo envía un paquete a un único destinatario.

Es una comunicación **uno a uno**.

### ¿Cómo funciona?

1. Un host genera un mensaje.
2. El paquete incluye una dirección IP de origen.
3. El paquete incluye la dirección IP de un único destinatario.
4. La red transporta el paquete hacia ese destinatario.

### Ejemplo

PC1: 192.168.1.10

PC2: 192.168.1.20

**Comunicación:**

PC1 → PC2

La PC1 envía información específicamente a la PC2.

**IMPORTANTE:**

- Unicast = uno a uno.
- Solo existe un dispositivo de origen por paquete.
- La dirección de origen es una dirección unicast.
- El destino del paquete corresponde a un único receptor.

---

## 9.1.4 — DIFUSIÓN (BROADCAST)

### ¿Qué es broadcast?

**Broadcast** es una comunicación en la que un dispositivo envía un paquete a todos los hosts de un mismo dominio de difusión.

Es una comunicación **uno a todos**.

### ¿Cómo funciona?

1. Un dispositivo genera un mensaje de difusión.
2. El mensaje se envía a una dirección de broadcast.
3. Los dispositivos del dominio de difusión reciben el mensaje.
4. Los hosts deben procesar la difusión según corresponda.

### Ejemplo

Red: 192.168.1.0/24

Dirección de broadcast: 192.168.1.255

Si un host envía un paquete dirigido a:

**192.168.1.255**

El paquete está dirigido a todos los hosts de esa red.

### Tipos de broadcast

**1. Broadcast dirigido**

Es una difusión dirigida a todos los hosts de una red específica.

Ejemplo:

- Red: 172.16.4.0/24
- Broadcast: 172.16.4.255

**2. Broadcast limitado**

Utiliza la dirección:

**255.255.255.255**

Se utiliza para realizar una difusión en la red local.

### ¿Los routers reenvían broadcast?

**Por defecto, los routers no reenvían los paquetes de difusión IPv4 entre redes.**

Esto permite separar los dominios de difusión.

**IMPORTANTE:**

- Broadcast = uno a todos.
- La dirección de broadcast tiene todos los bits de host en 1.
- Los switches propagan las difusiones dentro del dominio correspondiente.
- Los routers no reenvían normalmente las difusiones IPv4.
- IPv6 no utiliza broadcast.

---

## 9.1.6 — MULTIDIFUSIÓN (MULTICAST)

### ¿Qué es multicast?

**Multicast** es una comunicación en la que un host envía un paquete destinado a un grupo específico de receptores.

Es una comunicación **uno a un grupo**.

### ¿Cómo funciona?

1. Varios hosts participan en un grupo multicast.
2. El emisor genera un paquete para el grupo.
3. El paquete utiliza una dirección IPv4 multicast.
4. Los dispositivos participantes procesan la información del grupo.

### Rango de direcciones multicast

**224.0.0.0 a 239.255.255.255**

### Ejemplo de Cisco: OSPF

**OSPF (Open Shortest Path First)** es un protocolo de enrutamiento.

Los routers OSPF utilizan la dirección multicast:

**224.0.0.5**

Esta dirección permite comunicarse con los routers OSPF correspondientes.

### Ventaja del multicast

Permite enviar información a un grupo sin tener que generar necesariamente una transmisión unicast separada por cada receptor.

**PARA RECORDAR:**

- Unicast = uno a uno.
- Broadcast = uno a todos.
- Multicast = uno a un grupo.
- Multicast IPv4 = 224.0.0.0 a 239.255.255.255.

---

# COMPARACIÓN — UNICAST, BROADCAST Y MULTICAST

| Tipo | Comunicación | Destinatarios |
|---|---|---|
| Unicast | Uno a uno | Un único host |
| Broadcast | Uno a todos | Todos los hosts del dominio de difusión |
| Multicast | Uno a un grupo | Hosts participantes del grupo |

**IDEA CLAVE:**

La diferencia está en quién debe recibir la información.

---

# 9.2 — TIPOS DE DIRECCIONES IPv4

## 9.2.1 — DIRECCIONES IPv4 PÚBLICAS Y PRIVADAS

### ¿Qué es una dirección IPv4 pública?

Una **dirección IPv4 pública** es una dirección que puede utilizarse para el enrutamiento global en Internet, siempre que pertenezca al espacio de direcciones públicas válido.

### Características

- Debe administrarse para evitar conflictos globales.
- Se utiliza en comunicaciones a través de Internet.
- Puede ser asignada a organizaciones o proveedores de servicios.

### ¿Qué es una dirección IPv4 privada?

Una **dirección IPv4 privada** está reservada para redes internas.

Se utiliza en:
- Hogares.
- Empresas.
- Instituciones.
- Redes locales.

Las direcciones privadas pueden repetirse en distintas redes independientes.

### Rangos de direcciones IPv4 privadas

Definidos por **RFC 1918**:

| Bloque | Rango |
|---|---|
| 10.0.0.0/8 | 10.0.0.0 - 10.255.255.255 |
| 172.16.0.0/12 | 172.16.0.0 - 172.31.255.255 |
| 192.168.0.0/16 | 192.168.0.0 - 192.168.255.255 |

### Ejemplos de direcciones privadas

- 10.10.10.5
- 172.16.1.10
- 192.168.1.100

### Diferencia importante

**IPv4 pública:**
Puede utilizarse en el enrutamiento global de Internet.

**IPv4 privada:**
Se utiliza dentro de redes internas y no es enrutable directamente por Internet.

**IMPORTANTE:**

No todas las direcciones que están fuera de los rangos privados son direcciones públicas utilizables. También existen bloques reservados para usos especiales.

---

## 9.2.2 — ENRUTAMIENTO A INTERNET Y NAT

### ¿Qué es NAT?

**NAT (Network Address Translation)** significa Traducción de Direcciones de Red.

Es un mecanismo que permite traducir direcciones IP durante el tránsito de paquetes.

En las redes domésticas se utiliza normalmente para permitir que dispositivos con direcciones privadas accedan a Internet mediante una dirección pública.

### ¿Cómo funciona?

Imagina una red doméstica:

- PC1: 192.168.1.10
- PC2: 192.168.1.20
- Router: conectado al ISP

### Funcionamiento simplificado

1. PC1 envía un paquete destinado a Internet.
2. El router recibe el paquete.
3. El router realiza NAT para traducir la dirección privada de origen a una dirección pública.
4. El paquete continúa hacia Internet.
5. Cuando llega una respuesta, el router utiliza la información de traducción correspondiente.
6. La respuesta se entrega al dispositivo interno.

### Ejemplo

PC: 192.168.1.10

↓

Router con NAT

↓

Dirección IPv4 pública del router

↓

Internet

### ¿Por qué es importante NAT?

- Permite utilizar direcciones privadas en redes internas.
- Facilita el acceso a Internet desde dichas redes.
- Contribuye a aprovechar el espacio limitado de direcciones IPv4.

**IMPORTANTE:**

Las direcciones IPv4 privadas no se enrutan directamente por Internet.

Para comunicarse con destinos públicos, normalmente se utiliza NAT en el router de salida.

---

## 9.2.4 — DIRECCIONES IPv4 DE USO ESPECIAL

Existen direcciones IPv4 reservadas para funciones específicas.

### 1. Direcciones de Loopback

**Loopback** permite que un dispositivo envíe tráfico hacia sí mismo.

Rango:

**127.0.0.0/8**

Dirección más conocida:

**127.0.0.1**

### ¿Para qué sirve?

Permite realizar pruebas del funcionamiento local de la pila TCP/IP.

### Ejemplo

Comando:

ping 127.0.0.1

Si responde, significa que la pila IP local puede procesar esa comunicación de prueba.

**IMPORTANTE:** una respuesta al loopback no demuestra que el cable, Wi-Fi o la conexión a Internet estén funcionando.

---

### 2. Direcciones Link-Local o APIPA

**APIPA (Automatic Private IP Addressing)** permite que un dispositivo compatible se autoconfigure con una dirección local cuando no consigue obtener una dirección IPv4 mediante DHCP.

Bloque:

**169.254.0.0/16**

Direcciones utilizables habituales:

169.254.0.1 a 169.254.255.254

### Ejemplo

Una computadora intenta obtener una dirección IP de un servidor DHCP.

Si no puede obtenerla y utiliza APIPA, podría autoconfigurarse con:

169.254.10.25

### ¿Qué indica?

Puede indicar que el dispositivo no consiguió una configuración IPv4 mediante DHCP.

**PARA RECORDAR:**

- 127.0.0.1 = Loopback.
- 169.254.x.x = Link-local / APIPA.
- DHCP = asignación automática de configuración IP.

---

## 9.2.5 — DIRECCIONAMIENTO CON CLASE HEREDADO

Anteriormente, las direcciones IPv4 se organizaban mediante clases.

### Clases principales

| Clase | Primer octeto | Máscara histórica |
|---|---|---|
| A | 0 - 127 | /8 |
| B | 128 - 191 | /16 |
| C | 192 - 223 | /24 |
| D | 224 - 239 | Multicast |
| E | 240 - 255 | Reservado/experimental |

### Clase A

Fue diseñada para redes extremadamente grandes.

Máscara histórica:

255.0.0.0 (/8)

### Clase B

Fue diseñada para redes de tamaño mediano a grande.

Máscara histórica:

255.255.0.0 (/16)

### Clase C

Fue diseñada para redes pequeñas.

Máscara histórica:

255.255.255.0 (/24)

### Clase D

Se utiliza para multidifusión IPv4.

Rango:

224.0.0.0 a 239.255.255.255

### Clase E

Comprende direcciones reservadas para usos especiales o experimentales.

**IMPORTANTE:**

Las clases A, B y C forman parte del direccionamiento histórico.

Actualmente se utiliza el **direccionamiento sin clases (CIDR)**, que permite trabajar con diferentes longitudes de prefijo.

La tabla de clases es una clasificación histórica; dentro de esos rangos también existen direcciones reservadas.

---

## 9.2.6 — ASIGNACIÓN DE DIRECCIONES IP

### ¿Qué es IANA?

**IANA (Internet Assigned Numbers Authority)** es la autoridad que coordina recursos de numeración de Internet, incluidos los bloques de direcciones IP.

### ¿Qué es un RIR?

**RIR (Regional Internet Registry)** significa Registro Regional de Internet.

Los RIR administran y distribuyen recursos de direcciones IP en diferentes regiones.

### ¿Cómo se distribuyen las direcciones?

De manera simplificada:

IANA → RIR → ISP / Organizaciones → Usuarios

### Ejemplo

1. IANA distribuye bloques de direcciones a los RIR.
2. Los RIR asignan recursos según sus políticas.
3. Los ISP reciben bloques de direcciones.
4. Los ISP proporcionan conectividad y direcciones a sus clientes.

**PARA RECORDAR:**

- IANA = coordinación global de recursos de numeración.
- RIR = registro regional.
- ISP = proveedor de servicios de Internet.

---

# 9.3 — SEGMENTACIÓN DE REDES

## 9.3.2 — DOMINIOS DE DIFUSIÓN Y SEGMENTACIÓN

### ¿Qué es un dominio de difusión?

Un **dominio de difusión (Broadcast Domain)** es el conjunto de dispositivos que pueden recibir una difusión de capa 2 dentro de una red.

### ¿Cómo funciona?

Imagina una LAN con varias computadoras conectadas a un switch.

Si una computadora envía una difusión, el switch la propaga por los puertos correspondientes del dominio de difusión, excepto el puerto de entrada.

### ¿Qué es ARP?

**ARP (Address Resolution Protocol)** permite descubrir una dirección MAC asociada a una dirección IPv4 dentro de la red local.

### Funcionamiento básico

1. PC1 conoce la dirección IPv4 de un dispositivo local.
2. PC1 necesita averiguar la dirección MAC correspondiente.
3. Envía una solicitud ARP mediante broadcast.
4. El dispositivo correspondiente responde con su dirección MAC.
5. PC1 puede utilizar esa información para enviar tramas Ethernet.

### ¿Qué relación tiene DHCP?

Un cliente DHCP puede utilizar mensajes de difusión para encontrar un servidor DHCP en su red local.

### Diferencia entre switch y router

**Switch:**
Propaga las difusiones dentro del dominio de difusión correspondiente.

**Router:**
No reenvía normalmente las difusiones entre sus diferentes redes.

**IDEA CLAVE:**

Los routers permiten separar dominios de difusión.

---

## 9.3.3 — PROBLEMAS CON DOMINIOS DE DIFUSIÓN GRANDES

### ¿Qué ocurre cuando hay demasiados hosts?

En una red con muchos dispositivos puede generarse demasiado tráfico de difusión.

### Consecuencias

- Mayor consumo de recursos de red.
- Más paquetes de broadcast que deben procesar los hosts.
- Posible disminución del rendimiento.
- Mayor impacto de determinadas fallas o configuraciones incorrectas.

### ¿Cuál es la solución?

**Segmentar la red en subredes más pequeñas.**

### Ejemplo de Cisco

Red original:

172.16.0.0/16

En el ejemplo del curso, los dispositivos se dividen en dos redes:

- LAN 1: 172.16.0.0/24
- LAN 2: 172.16.1.0/24

Cada LAN contiene aproximadamente 200 usuarios.

### ¿Qué se consigue?

Las difusiones pueden quedar limitadas a cada red, siempre que se configuren dominios de difusión separados.

**IMPORTANTE:**

Dividir el direccionamiento IPv4 en subredes no separa por sí solo los broadcasts de capa 2.

También debe implementarse la separación correspondiente mediante routers, interfaces o VLAN y mecanismos de enrutamiento.

---

## 9.3.4 — RAZONES PARA LA SEGMENTACIÓN DE REDES

### ¿Qué es subnetting?

**Subnetting o división en subredes** es el proceso de dividir un bloque de direcciones IP en redes más pequeñas.

Para ello, se utilizan bits que anteriormente pertenecían a la porción de host.

### ¿Por qué dividir una red?

**1. Reducir el tráfico de difusión**

Ayuda a evitar que una gran cantidad de dispositivos reciba todas las difusiones de una red extensa.

**2. Mejorar el rendimiento**

Permite limitar el tráfico local y organizar mejor las comunicaciones.

**3. Facilitar la administración**

Los dispositivos pueden organizarse por departamentos, edificios o funciones.

**4. Aplicar políticas de seguridad**

Es posible definir qué subredes pueden comunicarse entre sí mediante los equipos y reglas correspondientes.

**5. Reducir el impacto de problemas**

Una configuración incorrecta o tráfico anormal puede afectar a un conjunto más reducido de dispositivos.

---

## ¿Cómo organizar una red mediante subredes?

Cisco presenta tres formas habituales:

### 1. Por ubicación

Ejemplo:

- Edificio A.
- Edificio B.
- Edificio C.

### 2. Por grupo o función

Ejemplo:

- Administración.
- Contabilidad.
- Soporte técnico.

### 3. Por tipo de dispositivo

Ejemplo:

- Computadoras.
- Cámaras IP.
- Teléfonos IP.

**IMPORTANTE:**

Las subredes permiten organizar una red lógicamente según las necesidades de la organización.

---

# INTRODUCCIÓN A LOS PREFIJOS

### ¿Qué significa /16?

Indica que los primeros 16 bits de la dirección IPv4 pertenecen a la porción de red.

### ¿Qué significa /24?

Indica que los primeros 24 bits pertenecen a la porción de red.

### Ejemplo

Red original:

172.16.0.0/16

Subredes posibles dentro de ese bloque:

- 172.16.0.0/24
- 172.16.1.0/24
- 172.16.2.0/24
- 172.16.3.0/24

Estas son solo cuatro de las posibles subredes /24 del bloque /16.

**PARA RECORDAR:**

Cuanto mayor es el número del prefijo, menor es la cantidad de bits disponibles para hosts.

Ejemplo:

- /16 = más bits para hosts.
- /24 = menos bits para hosts.
- /27 = aún menos bits para hosts.

---

# GLOSARIO — MÓDULO 9

| Término | Significado |
|---|---|
| Unicast | Comunicación uno a uno. |
| Broadcast | Comunicación uno a todos dentro de un dominio. |
| Multicast | Comunicación uno a un grupo. |
| IPv4 pública | Dirección utilizable en el enrutamiento global de Internet. |
| IPv4 privada | Dirección reservada para redes internas. |
| RFC 1918 | Documento que define rangos privados IPv4. |
| NAT | Traducción de Direcciones de Red. |
| Loopback | Comunicación IP del dispositivo consigo mismo. |
| APIPA | Configuración automática de IPv4 local. |
| DHCP | Protocolo de Configuración Dinámica de Host. |
| ARP | Protocolo de Resolución de Direcciones. |
| IANA | Internet Assigned Numbers Authority. |
| RIR | Registro Regional de Internet. |
| ISP | Proveedor de Servicios de Internet. |
| Broadcast Domain | Dominio de difusión. |
| Subnet | Subred. |
| Subnetting | División de una red en subredes. |
| CIDR | Direccionamiento entre dominios sin clases. |

---

# RESUMEN GENERAL — MÓDULO 9

1. IPv4 utiliza comunicaciones unicast, broadcast y multicast.
2. Unicast envía información a un único destinatario.
3. Broadcast envía información a todos los hosts del dominio de difusión.
4. Multicast envía información a un grupo específico.
5. El rango multicast IPv4 es 224.0.0.0 a 239.255.255.255.
6. Las direcciones IPv4 privadas se definen en RFC 1918.
7. Las direcciones privadas no se enrutan directamente por Internet.
8. NAT permite traducir direcciones privadas y públicas.
9. Loopback permite probar la comunicación IP local.
10. APIPA puede aparecer cuando un dispositivo no obtiene una dirección IPv4 mediante DHCP.
11. Las clases A, B y C pertenecen al direccionamiento histórico.
12. Actualmente se utiliza direccionamiento sin clases (CIDR).
13. IANA coordina la distribución global de recursos de numeración IP.
14. Los RIR distribuyen recursos de direcciones según sus regiones y políticas.
15. Los switches propagan las difusiones dentro de un dominio de broadcast.
16. Los routers no reenvían normalmente los broadcasts entre redes.
17. Los dominios de difusión grandes pueden afectar el rendimiento.
18. La división en subredes permite organizar bloques IP en redes más pequeñas.
19. La segmentación facilita la administración y aplicación de políticas de seguridad.
20. Los prefijos indican cuántos bits pertenecen a la porción de red.

**IDEA FINAL:**

IPv4 permite diferentes formas de comunicación. Las direcciones públicas y privadas cumplen funciones distintas, mientras que NAT facilita el acceso a Internet desde redes internas. La segmentación en subredes ayuda a organizar dispositivos y controlar el tráfico de difusión.

---

# CUESTIONARIO — MÓDULO 9

**Total:** 10 preguntas  
**Puntaje máximo:** 10 puntos

**Instrucciones:** Marca la respuesta correcta. Las preguntas de selección múltiple indican cuántas opciones debes elegir.

## PREGUNTA 1

¿Qué tipo de comunicación IPv4 permite enviar un paquete desde un host hacia un único destinatario?

- [ ] A. Broadcast
- [ ] B. Multicast
- [ ] C. Unicast
- [ ] D. NAT

## PREGUNTA 2

¿Cuál de las siguientes direcciones representa una dirección de difusión limitada de IPv4?

- [ ] A. 192.168.1.1
- [ ] B. 255.255.255.255
- [ ] C. 127.0.0.1
- [ ] D. 224.0.0.5

## PREGUNTA 3

¿Qué rango está reservado para direcciones multicast IPv4?

- [ ] A. 10.0.0.0 a 10.255.255.255
- [ ] B. 172.16.0.0 a 172.31.255.255
- [ ] C. 224.0.0.0 a 239.255.255.255
- [ ] D. 192.168.0.0 a 192.168.255.255

## PREGUNTA 4

¿Cuáles de las siguientes direcciones IPv4 son privadas? (Selecciona tres).

- [ ] A. 10.10.10.5
- [ ] B. 172.20.1.10
- [ ] C. 192.168.1.100
- [ ] D. 8.8.8.8

## PREGUNTA 5

¿Qué tecnología permite traducir direcciones IPv4 privadas a direcciones públicas para facilitar la comunicación con Internet?

- [ ] A. ARP
- [ ] B. NAT
- [ ] C. DHCP
- [ ] D. DNS

## PREGUNTA 6

¿Qué dirección IPv4 se utiliza comúnmente para probar la pila TCP/IP local mediante loopback?

- [ ] A. 169.254.1.1
- [ ] B. 192.168.1.1
- [ ] C. 127.0.0.1
- [ ] D. 255.255.255.255

## PREGUNTA 7

Una computadora Windows no logra obtener una dirección IPv4 mediante DHCP y se autoconfigura con una dirección 169.254.20.15.

¿Qué mecanismo está utilizando?

- [ ] A. NAT
- [ ] B. APIPA
- [ ] C. Multicast
- [ ] D. OSPF

## PREGUNTA 8

¿Qué dispositivo normalmente separa los dominios de difusión IPv4 y evita reenviar broadcasts entre sus interfaces?

- [ ] A. Hub
- [ ] B. Switch de capa 2
- [ ] C. Router
- [ ] D. Cable Ethernet

## PREGUNTA 9

¿Cuáles son beneficios de segmentar una red en subredes y dominios de difusión separados? (Selecciona tres).

- [ ] A. Reducir el tráfico de difusión entre segmentos.
- [ ] B. Facilitar la administración.
- [ ] C. Ayudar a aplicar políticas de seguridad.
- [ ] D. Eliminar la necesidad de direcciones IP.

## PREGUNTA 10

Una empresa divide una red IPv4 /16 en varias subredes /24.

¿Qué sucede con la cantidad de bits destinados a identificar la red?

- [ ] A. Disminuye de 16 a 8.
- [ ] B. Aumenta de 16 a 24.
- [ ] C. Permanece en 16.
- [ ] D. Desaparece la porción de host.

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
**Respuesta: C. Unicast.**

Unicast permite enviar información desde un dispositivo hacia un único destinatario.

### PREGUNTA 2
**Respuesta: B. 255.255.255.255.**

Es la dirección de difusión limitada en IPv4.

### PREGUNTA 3
**Respuesta: C. 224.0.0.0 a 239.255.255.255.**

Ese bloque está reservado para comunicaciones multicast IPv4.

### PREGUNTA 4
**Respuesta: A, B y C.**

Son direcciones pertenecientes a los bloques privados RFC 1918:

- 10.0.0.0/8
- 172.16.0.0/12
- 192.168.0.0/16

### PREGUNTA 5
**Respuesta: B. NAT.**

NAT permite traducir direcciones IP durante el tránsito de paquetes, como ocurre cuando una red privada accede a Internet.

### PREGUNTA 6
**Respuesta: C. 127.0.0.1.**

Es la dirección loopback más conocida y permite probar la pila IP local.

### PREGUNTA 7
**Respuesta: B. APIPA.**

APIPA permite la autoconfiguración de direcciones IPv4 link-local dentro del bloque 169.254.0.0/16.

### PREGUNTA 8
**Respuesta: C. Router.**

Los routers separan dominios de difusión y no reenvían normalmente los paquetes broadcast entre redes.

### PREGUNTA 9
**Respuesta: A, B y C.**

La segmentación permite reducir tráfico de difusión, organizar mejor los dispositivos y aplicar políticas de seguridad cuando se configura correctamente.

### PREGUNTA 10
**Respuesta: B. Aumenta de 16 a 24.**

Al pasar de /16 a /24, se utilizan ocho bits adicionales para identificar subredes.

---

**PUNTAJE FINAL: ____ / 10**

# CONCEPTOS QUE DEBES DOMINAR ANTES DEL MÓDULO 10

- Diferencias entre unicast, broadcast y multicast.
- Direcciones IPv4 públicas y privadas.
- Los tres rangos privados RFC 1918.
- Funcionamiento básico de NAT.
- Direcciones especiales loopback y APIPA.
- Direccionamiento histórico por clases.
- Función de IANA y los RIR.
- Funcionamiento de los dominios de difusión.
- Diferencias entre switch y router ante broadcasts.
- Razones para utilizar subnetting.
- Relación entre prefijos y porciones de red y host.
