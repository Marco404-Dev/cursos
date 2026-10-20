
# Módulo 4: Conmutación Ethernet

**Curso:** Cisco Networking Academy — Dispositivos de Red y Configuración Inicial

## 1. ¿Qué es Ethernet?

Ethernet es una tecnología de comunicación utilizada principalmente en redes LAN cableadas.

Define cómo se organizan y transmiten los datos entre dispositivos.

### Características

- Funciona en las capas 1 y 2 del modelo OSI.
- Utiliza cables de cobre y fibra óptica.
- Utiliza direcciones MAC para entregar tramas.
- Sus estándares pertenecen a IEEE 802.3.

### Evolución de Ethernet

| Tecnología | Velocidad |
|---|---|
| Ethernet | 10 Mbps |
| Fast Ethernet | 100 Mbps |
| Gigabit Ethernet | 1 Gbps |
| 10 Gigabit Ethernet | 10 Gbps |
| 40 Gigabit Ethernet | 40 Gbps |
| 100 Gigabit Ethernet | 100 Gbps |

### Ejemplo: 100BASE-T

- **100:** velocidad de 100 Mbps.
- **BASE:** transmisión en banda base.
- **T:** cable de par trenzado.

**Importante:** Ethernet es un estándar de facto, es decir, una tecnología ampliamente adoptada en las redes LAN cableadas.

## 2. Ethernet y el modelo OSI

Ethernet trabaja principalmente en:

- **Capa 1 (Física):** transmite bits a través del medio físico.
- **Capa 2 (Enlace de datos):** utiliza direcciones MAC y tramas para la comunicación.

### Subcapas de enlace de datos

| Subcapa | Función |
|---|---|
| LLC (Logical Link Control) | Permite la comunicación entre la capa de red y la capa de enlace, identificando protocolos superiores. |
| MAC (Media Access Control) | Controla el acceso al medio, el direccionamiento MAC y la encapsulación de tramas. |

### Subcapa LLC

- Está asociada con IEEE 802.2.
- Se comunica con las capas superiores.
- Permite utilizar protocolos como IPv4 e IPv6 sobre una misma tecnología de enlace.

### Subcapa MAC

- Proporciona direccionamiento físico.
- Participa en la encapsulación de datos.
- Permite detectar errores mediante FCS.
- Define mecanismos de acceso al medio.

## 3. Half-Duplex y Full-Duplex

### Half-Duplex (medio dúplex)

Permite transmitir y recibir datos, pero no simultáneamente.

Se utilizaba principalmente en redes Ethernet antiguas con hubs.

**Ejemplo:**

PC-A transmite → PC-B recibe.

Después:

PC-B transmite → PC-A recibe.

### Full-Duplex (dúplex completo)

Permite enviar y recibir datos simultáneamente.

Es utilizado normalmente en redes Ethernet modernas con switches.

**Ejemplo:**

PC-A ↔ PC-B

Ambos pueden transmitir y recibir al mismo tiempo.

### CSMA/CD

Significa **Carrier Sense Multiple Access with Collision Detection**.

Se utiliza en Ethernet compartida de medio dúplex para gestionar las colisiones.

Su funcionamiento básico:

1. Escucha si el medio está disponible.
2. Comienza a transmitir.
3. Detecta si ocurre una colisión.
4. Espera un tiempo antes de volver a intentar.

**Importante:** Ethernet full-duplex con switches no necesita CSMA/CD.

## 4. Trama Ethernet

Una trama Ethernet es la unidad de datos utilizada en la capa 2.

Contiene direcciones MAC, datos y mecanismos de detección de errores.

### Campos de la trama Ethernet

| Campo | Tamaño | Función |
|---|---|---|
| Preámbulo | 7 bytes | Sincroniza al emisor y al receptor. |
| SFD | 1 byte | Indica el inicio de la trama. |
| MAC destino | 6 bytes | Identifica la interfaz destinataria. |
| MAC origen | 6 bytes | Identifica la interfaz emisora. |
| Tipo/Longitud | 2 bytes | Identifica el protocolo encapsulado o la longitud. |
| Datos | 46-1500 bytes | Contiene los datos encapsulados y, cuando es necesario, relleno. |
| FCS | 4 bytes | Detecta errores mediante CRC. |

### Valores EtherType importantes

| Valor | Protocolo |
|---|---|
| 0x0800 | IPv4 |
| 0x86DD | IPv6 |
| 0x0806 | ARP |

### Tamaños de la trama

- **Mínimo:** 64 bytes.
- **Máximo estándar:** 1518 bytes.
- Los 8 bytes de preámbulo y SFD no se incluyen en estos tamaños.
- Una trama estándar menor de 64 bytes se considera demasiado corta.
- Existen tramas con etiquetas VLAN y tramas jumbo que pueden superar el tamaño habitual.

### FCS y CRC

FCS (Frame Check Sequence) permite detectar errores de transmisión.

Utiliza CRC (Cyclic Redundancy Check).

Si la comprobación detecta un error, la trama se descarta.

**Importante:** FCS detecta errores, pero no repara automáticamente los datos.

## 5. Direcciones MAC Ethernet

Una dirección MAC Ethernet tiene 48 bits (6 bytes).

Se representa habitualmente mediante 12 dígitos hexadecimales.

### Ejemplo

`00:1A:2B:3C:4D:5E`

Cada dígito hexadecimal representa 4 bits.

12 × 4 = **48 bits**

### Tipos de direcciones MAC

| Tipo | Destinatario |
|---|---|
| Unicast | Un único dispositivo. |
| Broadcast | Todos los dispositivos del dominio de difusión. |
| Multicast | Un grupo específico de dispositivos. |

## 6. MAC Unicast (Unidifusión)

Se utiliza cuando un dispositivo envía información a un único destinatario.

### Ejemplo

PC-A quiere enviar información a PC-B.

- MAC origen: MAC de PC-A.
- MAC destino: MAC de PC-B.

Si PC-A no conoce la dirección MAC correspondiente a la IPv4 de PC-B, puede utilizar ARP para descubrirla.

**Importante:** En IPv6 se utiliza Neighbor Discovery (ND) en lugar de ARP.

## 7. MAC Broadcast (Difusión)

Una trama broadcast está destinada a todos los dispositivos del mismo dominio de difusión.

### Dirección MAC broadcast

`FF:FF:FF:FF:FF:FF`

En binario equivale a 48 bits en 1.

### Características

- El switch la reenvía por todos los puertos correspondientes a la misma VLAN, excepto el puerto de entrada.
- Los routers no reenvían normalmente las difusiones Ethernet.
- Se utiliza en protocolos como ARP y DHCPv4.

### Ejemplo

Una PC necesita descubrir una MAC mediante ARP.

Envía una solicitud con MAC destino:

`FF:FF:FF:FF:FF:FF`

Los dispositivos del dominio de difusión reciben la solicitud, pero normalmente solo responde quien posee la IPv4 consultada.

### Diferencia entre broadcast IP y MAC

| Dirección | Ejemplo |
|---|---|
| Broadcast IPv4 | 192.168.1.255/24 |
| Broadcast MAC | FF:FF:FF:FF:FF:FF |

**Importante:** Una solicitud ARP utiliza broadcast Ethernet, pero no es un paquete broadcast IPv4.

## 8. MAC Multicast (Multidifusión)

Permite enviar información a un grupo específico de dispositivos.

### Direcciones importantes

| Protocolo | Prefijo MAC multicast |
|---|---|
| IPv4 | 01:00:5E |
| IPv6 | 33:33 |

### Rangos IP multicast

- IPv4: `224.0.0.0` hasta `239.255.255.255`.
- IPv6: `FF00::/8`.

### Ejemplo

Un servidor transmite contenido a varios equipos que pertenecen al mismo grupo multicast.

Solo los dispositivos suscritos deben procesar la información correspondiente.

**Importante:** Un switch puede inundar inicialmente el tráfico multicast, pero con mecanismos como IGMP Snooping puede limitarlo a los puertos interesados.

## 9. Funcionamiento de un switch

Un switch Ethernet de capa 2 utiliza direcciones MAC para decidir hacia dónde enviar las tramas.

No necesita analizar la dirección IPv4 de destino para realizar su conmutación normal de capa 2.

### Tabla MAC o CAM

Es una tabla que relaciona direcciones MAC con puertos del switch.

### Ejemplo

| Dirección MAC | Puerto |
|---|---|
| 00-0A | Fa0/1 |
| 00-0B | Fa0/2 |
| 00-0C | Fa0/3 |
| 00-0D | Fa0/4 |

Con esta información, el switch sabe por dónde alcanzar cada dispositivo.

## 10. Aprendizaje de direcciones MAC

Los switches aprenden automáticamente las direcciones MAC de los dispositivos conectados.

### ¿Cómo aprenden?

1. Reciben una trama Ethernet.
2. Revisan la dirección MAC de origen.
3. Identifican el puerto por donde ingresó.
4. Guardan la asociación MAC-puerto en su tabla.

### Ejemplo

PC-A envía una trama:

- MAC origen: `00-0A`.
- MAC destino: `00-0D`.
- Puerto de entrada: Fa0/1.

El switch aprende:

`00-0A → Fa0/1`

**Recuerda:** Un switch aprende examinando la MAC de origen, no la MAC de destino.

### Tiempo de aprendizaje

Las entradas dinámicas suelen mantenerse aproximadamente 300 segundos (5 minutos), dependiendo de la configuración.

Cuando el switch vuelve a recibir tráfico desde esa MAC, actualiza su temporizador.

## 11. Reenvío y filtrado de tramas

Cuando un switch recibe una trama, consulta su tabla MAC para tomar una decisión.

### Caso 1: MAC destino conocida

El switch encuentra la dirección MAC de destino en su tabla.

**Resultado:** Envía la trama únicamente por el puerto correspondiente.

Ejemplo:

`PC-A → Switch → PC-D`

El switch sabe que PC-D está en Fa0/4 y reenvía la trama solamente por ese puerto.

### Caso 2: MAC destino desconocida

La MAC de destino no aparece en la tabla.

**Resultado:** El switch inunda la trama por los demás puertos de la misma VLAN, excepto el de entrada.

Esto se llama **unicast desconocido (Unknown Unicast)**.

### Caso 3: MAC destino broadcast

La trama utiliza:

`FF:FF:FF:FF:FF:FF`

**Resultado:** El switch realiza una difusión por los demás puertos de esa VLAN.

### Caso 4: MAC destino en el mismo puerto de entrada

Si el switch sabe que la MAC de destino se encuentra en el mismo puerto por el que ingresó la trama, no necesita reenviarla por otro puerto.

**Resultado:** Filtra la trama.

### Resumen

| Situación | Acción del switch |
|---|---|
| MAC destino conocida en otro puerto | Reenvía por el puerto correspondiente. |
| MAC destino desconocida | Inunda los demás puertos de la VLAN. |
| MAC broadcast | Inunda los demás puertos de la VLAN. |
| MAC multicast | Inunda o limita el tráfico según su configuración. |
| MAC destino conocida en el puerto de entrada | Filtra la trama. |

## 12. Switches conectados entre sí

Un switch puede aprender varias direcciones MAC por un mismo puerto.

Esto ocurre, por ejemplo, cuando tiene otro switch conectado.

### Ejemplo

Switch 1 está conectado a Switch 2.

En Switch 2 existen tres computadoras:

- PC-A
- PC-B
- PC-C

Switch 1 puede aprender las tres direcciones MAC utilizando el mismo puerto que conecta ambos switches.

**Importante:** Una interfaz de switch no está limitada necesariamente a una sola dirección MAC aprendida.

## 13. Comunicación con redes remotas

Cuando una computadora necesita enviar un paquete a otra red, utiliza su gateway predeterminado.

### Ejemplo

PC-A:

- IP: `192.168.1.10`
- Gateway: `192.168.1.1`

Servidor remoto:

- IP: `10.10.10.20`

PC-A no envía la trama Ethernet directamente a la MAC del servidor remoto.

En su lugar, utiliza la dirección MAC del gateway predeterminado.

### Direcciones utilizadas

**Paquete IP:**

- IP origen: `192.168.1.10`
- IP destino: `10.10.10.20`

**Trama Ethernet del primer enlace:**

- MAC origen: MAC de PC-A.
- MAC destino: MAC del gateway.

El router recibe la trama, procesa el paquete IP y lo reenvía hacia la red de destino.

**Importante:**

- La IP de destino sigue siendo la del servidor remoto durante el enrutamiento normal.
- Las direcciones MAC cambian según el enlace por el que viaja el paquete.
- Si PC-A desconoce la MAC del gateway, puede utilizar ARP para descubrirla.

---

# 10 preguntas de repaso — Módulo 4

### 1. ¿Qué estándar IEEE corresponde a Ethernet?

A) IEEE 802.11.  
B) IEEE 802.3.  
C) IEEE 802.15.  
D) IEEE 802.1X.

<details>
<summary>Ver respuesta</summary>

✅ **B) IEEE 802.3.**

IEEE 802.3 define los estándares Ethernet.

IEEE 802.11 se utiliza para redes inalámbricas Wi-Fi.

</details>

### 2. ¿Cuáles son las dos subcapas de enlace de datos?

A) TCP y UDP.  
B) IP y ARP.  
C) LLC y MAC.  
D) Física y transporte.

<details>
<summary>Ver respuesta</summary>

✅ **C) LLC y MAC.**

LLC comunica la capa de enlace con las capas superiores.

MAC se encarga del direccionamiento de enlace, encapsulación y acceso al medio.

</details>

### 3. ¿Cuál es el tamaño mínimo de una trama Ethernet estándar?

A) 32 bytes.  
B) 46 bytes.  
C) 128 bytes.  
D) 64 bytes.

<details>
<summary>Ver respuesta</summary>

✅ **D) 64 bytes.**

El tamaño mínimo es de 64 bytes, desde la MAC de destino hasta el FCS.

No incluye el preámbulo ni el SFD.

</details>

### 4. ¿Cuál es la función del campo FCS en Ethernet?

A) Detectar errores utilizando CRC.  
B) Asignar direcciones IPv4.  
C) Identificar el puerto TCP.  
D) Establecer la velocidad del enlace.

<details>
<summary>Ver respuesta</summary>

✅ **A) Detectar errores utilizando CRC.**

FCS permite comprobar si una trama sufrió alteraciones durante su transmisión.

Si se detecta un error, la trama se descarta.

</details>

### 5. ¿Cuál es la dirección MAC de broadcast?

A) 00:00:00:00:00:00.  
B) FF:FF:FF:FF:FF:FF.  
C) 01:00:5E:00:00:01.  
D) 192.168.1.255.

<details>
<summary>Ver respuesta</summary>

✅ **B) FF:FF:FF:FF:FF:FF.**

Es la dirección MAC utilizada para enviar una trama a todos los dispositivos del dominio de difusión.

</details>

### 6. ¿Qué dirección utiliza un switch para aprender automáticamente la ubicación de un dispositivo?

A) Dirección IPv4 de destino.  
B) Dirección MAC de destino.  
C) Dirección MAC de origen.  
D) Dirección del servidor DNS.

<details>
<summary>Ver respuesta</summary>

✅ **C) Dirección MAC de origen.**

El switch examina la MAC de origen y la asocia con el puerto por donde recibió la trama.

</details>

### 7. ¿Qué sucede cuando un switch recibe una trama unicast cuya MAC de destino no aparece en su tabla?

A) La descarta inmediatamente.  
B) La envía exclusivamente al router.  
C) Cambia la dirección MAC de destino.  
D) La envía por los demás puertos de la misma VLAN.

<details>
<summary>Ver respuesta</summary>

✅ **D) La envía por los demás puertos de la misma VLAN.**

Este proceso se denomina inundación de unicast desconocido.

No reenvía la trama por el puerto donde la recibió.

</details>

### 8. ¿Qué sucede cuando un switch conoce la dirección MAC de destino en otro puerto?

A) Reenvía la trama únicamente por el puerto correspondiente.  
B) Envía la trama a todos los puertos.  
C) Elimina la dirección MAC de origen.  
D) Convierte la trama en broadcast.

<details>
<summary>Ver respuesta</summary>

✅ **A) Reenvía la trama únicamente por el puerto correspondiente.**

El switch utiliza su tabla MAC para realizar el reenvío selectivo de tramas.

</details>

### 9. Una PC desea comunicarse con un servidor ubicado en otra red. ¿Qué dirección MAC utiliza como destino en la primera trama Ethernet?

A) La MAC del servidor remoto.  
B) La MAC del gateway predeterminado.  
C) La MAC del servidor DNS.  
D) FF:FF:FF:FF:FF:FF en todos los casos.

<details>
<summary>Ver respuesta</summary>

✅ **B) La MAC del gateway predeterminado.**

La PC envía la trama al router para que este pueda reenviar el paquete IP hacia la red remota.

La dirección IP de destino continúa siendo la del servidor remoto.

</details>

### 10. ¿Cuál de las siguientes afirmaciones sobre las direcciones MAC es correcta?

A) Las MAC tienen 32 bits.  
B) Las MAC cambian obligatoriamente cada vez que se envía un paquete.  
C) Las MAC Ethernet tienen 48 bits y se representan normalmente con 12 dígitos hexadecimales.  
D) Los switches de capa 2 utilizan principalmente direcciones IPv4 para aprender los puertos.

<details>
<summary>Ver respuesta</summary>

✅ **C) Las MAC Ethernet tienen 48 bits y se representan normalmente con 12 dígitos hexadecimales.**

Cada dígito hexadecimal equivale a 4 bits.

12 × 4 = 48 bits.

</details>

---

**Fin del Módulo 4 — Conmutación Ethernet**
