
# Módulo 13: Resolución de Direcciones

## 1. Direcciones MAC e IP

Cuando un dispositivo quiere enviar información a otro, necesita conocer las direcciones correspondientes para que los datos lleguen a su destino.

En una red Ethernet se utilizan dos direcciones principales:

| Dirección | Capa OSI | Función |
|---|---|---|
| MAC (física) | Capa 2 - Enlace de datos | Entrega tramas entre interfaces de red en un mismo enlace Ethernet. |
| IP (lógica) | Capa 3 - Red | Identifica el origen y destino de los paquetes entre redes. |

**Recuerda:**
- La dirección IP identifica el destino lógico del paquete.
- La dirección MAC identifica el siguiente destino de la trama Ethernet.
- Si conocemos una IPv4 pero necesitamos su MAC, utilizamos ARP cuando corresponde.

---

## 2. Destino en la misma red

Cuando dos dispositivos pertenecen a la misma red IP, normalmente pueden comunicarse directamente sin pasar por un router.

### Ejemplo

| Dispositivo | Dirección IPv4 | Dirección MAC (simplificada) |
|---|---|---|
| PC1 | 192.168.10.10 | AA-AA-AA |
| PC2 | 192.168.10.11 | 55-55-55 |

PC1 quiere enviar información a PC2.

**Trama Ethernet (Capa 2):**
- MAC de origen: `AA-AA-AA`
- MAC de destino: `55-55-55`

**Paquete IP (Capa 3):**
- IP de origen: `192.168.10.10`
- IP de destino: `192.168.10.11`

```text
PC1 --------------------> PC2
192.168.10.10              192.168.10.11
MAC: AA-AA-AA              MAC: 55-55-55

Destino de la trama: MAC de PC2
Destino del paquete: IP de PC2
```

**Importante:** Si PC1 no conoce la dirección MAC de PC2, puede utilizar ARP para descubrirla.

---

## 3. Destino en una red remota

Cuando un dispositivo quiere comunicarse con otra red, necesita enviar el paquete a su puerta de enlace predeterminada (Default Gateway).

En este caso:
- La dirección IP de destino corresponde al dispositivo remoto.
- La dirección MAC de destino corresponde a la interfaz del router local que actúa como gateway.

### Ejemplo

PC1 quiere enviar información a PC2, que se encuentra en otra red.

```text
PC1 -----> R1 -----> R2 -----> PC2
LAN 1                         LAN 2

Origen: PC1
Destino final: PC2
```

**Primer salto (PC1 hacia R1):**

| Dirección | Valor |
|---|---|
| IP origen | IP de PC1 |
| IP destino | IP de PC2 |
| MAC origen | MAC de PC1 |
| MAC destino | MAC de la interfaz LAN de R1 |

**Segundo salto (R1 hacia R2, suponiendo Ethernet):**

| Dirección | Valor |
|---|---|
| IP origen | IP de PC1 |
| IP destino | IP de PC2 |
| MAC origen | MAC de la interfaz de salida de R1 |
| MAC destino | MAC de la interfaz de R2 |

**Último salto (R2 hacia PC2):**

- MAC origen: MAC de la interfaz LAN de R2.
- MAC destino: MAC de PC2.

### ¿Qué sucede con las direcciones?

- Las direcciones IP de origen y destino normalmente se mantienen durante el recorrido, si no interviene NAT.
- Las direcciones MAC de origen y destino cambian en cada enlace Ethernet donde el router genera una nueva trama.
- Cada router examina la IP de destino para decidir dónde reenviar el paquete.

**Recuerda:** La IP identifica el destino final; la MAC identifica el siguiente destino de la trama en el enlace local.

---

## 4. Direcciones de difusión (Broadcast)

Una difusión permite enviar una trama Ethernet a todos los dispositivos del mismo dominio de difusión.

### 4.1 Dirección MAC de difusión

La dirección MAC de broadcast es:

`FF:FF:FF:FF:FF:FF`

Características:
- Tiene 48 bits.
- Está formada por todos los bits en 1.
- Cada `F` hexadecimal representa cuatro bits en 1.
- Todos los dispositivos Ethernet del dominio de difusión reciben esta trama.

### Ejemplo

```text
              Switch
             /  |   \
           PC1 PC2  PC3

PC1 envía una trama broadcast
              |
              v
El switch la reenvía a PC2 y PC3.
```

El switch reenvía la trama por los puertos del mismo dominio de difusión, excepto por el puerto donde la recibió.

**Importante:** Un broadcast Ethernet no se envía automáticamente a otras redes a través del router.

---

## 5. Dominios de difusión

Un dominio de difusión (Broadcast Domain) es el conjunto de dispositivos que pueden recibir una misma difusión Ethernet.

### ¿Qué sucede cuando una red crece?

Cuando existen muchos dispositivos:
- Aumenta el tráfico de difusión.
- Los dispositivos deben procesar más mensajes broadcast.
- Puede reducirse el rendimiento de la red.

### ¿Cómo se soluciona?

Dividiendo la red en varios dominios de difusión mediante routers o VLAN.

| Dispositivo | Comportamiento |
|---|---|
| Switch (misma VLAN) | Reenvía las tramas broadcast dentro de esa VLAN. |
| Router | Normalmente no reenvía los broadcasts Ethernet entre redes. |
| VLAN | Permite separar una red conmutada en diferentes dominios de difusión. |

**Ejemplo:**

```text
Red A                  Red B
PC1 --- Switch --- Router --- Switch --- PC3
PC2 ---/                         \--- PC4

Dominio 1                    Dominio 2
```

Si PC1 envía un broadcast, PC2 puede recibirlo, pero PC3 y PC4 no lo reciben a través del router.

---

## 6. Comunicación de la capa de acceso

En Ethernet, una tarjeta de red (NIC) normalmente acepta una trama cuando:

1. La dirección MAC de destino coincide con su propia MAC.
2. La dirección MAC de destino es de difusión.

También puede aceptar ciertos mensajes multicast a los que está suscrita.

### ¿Cuál es el problema?

Las aplicaciones normalmente conocen la dirección IP del destino, pero para construir una trama Ethernet necesitan una dirección MAC.

**Solución: Resolución de direcciones.**

| Protocolo | Uso |
|---|---|
| ARP | Resuelve direcciones IPv4 a direcciones MAC en una red local. |
| NDP (Neighbor Discovery) | Permite descubrir vecinos y resolver direcciones de enlace en IPv6 mediante ICMPv6. |

---

## 7. Protocolo ARP

ARP (Address Resolution Protocol) permite descubrir la dirección MAC asociada a una dirección IPv4 en la red local.

### 7.1 ¿Cómo funciona ARP?

Supongamos:

- PC1: `192.168.1.10`
- PC2: `192.168.1.20`

PC1 conoce la IPv4 de PC2, pero desconoce su dirección MAC.

**Paso 1: ARP Request (Solicitud)**

PC1 envía una solicitud a la dirección MAC de broadcast:

`FF:FF:FF:FF:FF:FF`

Básicamente pregunta:

"¿Quién tiene la IP 192.168.1.20?"

Todos los dispositivos del dominio de difusión reciben la solicitud.

**Paso 2: ARP Reply (Respuesta)**

PC2 reconoce que la dirección IPv4 consultada es suya.

Entonces responde directamente a PC1 indicando su dirección MAC.

La respuesta normal de ARP es unicast.

**Paso 3: Tabla ARP**

PC1 almacena la asociación entre la IPv4 y la MAC de PC2.

Ejemplo:

| Dirección IPv4 | Dirección MAC |
|---|---|
| 192.168.1.20 | AA:BB:CC:DD:EE:FF |

Ahora PC1 puede enviar tramas directamente a PC2 sin repetir inmediatamente la solicitud ARP.

**Importante:** Las entradas dinámicas de ARP no se guardan para siempre; pueden caducar.

### 7.2 ¿Qué sucede si el destino está en otra red?

ARP no busca directamente la MAC del dispositivo remoto.

En su lugar:
1. La PC identifica que la IP de destino pertenece a otra red.
2. Determina que debe enviar el paquete a su gateway.
3. Utiliza ARP para conocer la MAC del gateway, si todavía no la conoce.
4. Envía la trama Ethernet al router.

**Recuerda:** ARP permite encontrar la MAC del siguiente destino local, no atravesar Internet buscando direcciones MAC.

---

## 8. Diferencias importantes

| Concepto | Función |
|---|---|
| Dirección IP | Identifica el origen y destino lógico del paquete. |
| Dirección MAC | Identifica las interfaces de origen y destino de una trama Ethernet. |
| ARP | Descubre la MAC asociada a una IPv4 local. |
| Broadcast | Permite enviar una trama a todos los dispositivos del dominio de difusión. |
| Dominio de difusión | Conjunto de dispositivos que reciben un mismo broadcast. |
| Gateway | Permite enviar paquetes hacia otras redes. |
| Router | Conecta redes y separa dominios de difusión. |
| NDP | Realiza descubrimiento de vecinos en IPv6. |

---

## 9. Puntos clave para el examen

- MAC corresponde a la capa 2 del modelo OSI.
- IP corresponde a la capa 3 del modelo OSI.
- Cuando el destino está en la misma red, la trama se dirige a la MAC del host de destino.
- Cuando el destino está en una red remota, la primera trama se dirige a la MAC del gateway.
- Los routers modifican el encapsulamiento de capa 2 al reenviar paquetes entre enlaces.
- ARP permite resolver una IPv4 a una dirección MAC.
- ARP Request normalmente utiliza broadcast.
- ARP Reply normalmente utiliza unicast.
- La dirección MAC broadcast es `FF:FF:FF:FF:FF:FF`.
- Un router separa dominios de difusión.
- IPv6 utiliza Neighbor Discovery, basado en ICMPv6, en lugar de ARP.
- La tabla ARP almacena asociaciones entre direcciones IPv4 y MAC.

---

## 10. Preguntas de repaso tipo Cisco

**1. ¿Cuál es la función principal de una dirección MAC?**

- A) Identificar la red remota de destino.
- B) Identificar interfaces para entregar tramas en un enlace Ethernet.
- C) Asignar direcciones IPv4 automáticamente.
- D) Traducir nombres de dominio.

**2. PC1 desea comunicarse con PC2 dentro de la misma red local. ¿Qué dirección MAC colocará PC1 como destino en su trama Ethernet?**

- A) La MAC del gateway.
- B) La MAC de broadcast.
- C) La MAC de PC2.
- D) La MAC del servidor DNS.

**3. PC1 necesita enviar información a un servidor ubicado en una red remota. ¿Qué dirección MAC utilizará como destino en la primera trama Ethernet?**

- A) La MAC del servidor remoto.
- B) La MAC de su gateway predeterminado.
- C) La MAC de broadcast.
- D) La MAC de cualquier switch.

**4. ¿Qué sucede normalmente con las direcciones MAC cuando un paquete atraviesa varios routers mediante enlaces Ethernet?**

- A) Permanecen iguales desde el origen hasta el destino.
- B) Se convierten en direcciones IPv4.
- C) Se eliminan permanentemente del paquete IP.
- D) Cambian según el enlace Ethernet utilizado.

**5. ¿Cuál es la dirección MAC de difusión de Ethernet?**

- A) 00:00:00:00:00:00
- B) 255.255.255.255
- C) FF:FF:FF:FF:FF:FF
- D) 127.0.0.1

**6. ¿Qué dispositivo se utiliza normalmente para separar dominios de difusión?**

- A) Hub
- B) Router
- C) Repetidor
- D) Cable Ethernet

**7. ¿Cuál es el objetivo principal de ARP?**

- A) Asignar una IPv4 a cada dispositivo.
- B) Traducir nombres de dominio a direcciones IP.
- C) Descubrir la dirección MAC asociada a una IPv4 local.
- D) Enviar paquetes entre diferentes redes.

**8. ¿Cómo se transmite normalmente una solicitud ARP (ARP Request) en una red Ethernet?**

- A) Unicast al dispositivo remoto.
- B) Broadcast a los dispositivos del dominio de difusión.
- C) Exclusivamente al servidor DNS.
- D) Directamente a Internet.

**9. ¿Qué almacena una tabla ARP?**

- A) Direcciones IPv4 asociadas con direcciones MAC.
- B) Contraseñas de los dispositivos.
- C) Nombres de dominio y direcciones de servidores web.
- D) Direcciones IPv6 y sus máscaras únicamente.

**10. ¿Qué mecanismo utiliza IPv6 en lugar de ARP para descubrir vecinos y resolver direcciones de enlace?**

- A) DHCPv4
- B) DNS
- C) NAT
- D) Neighbor Discovery mediante ICMPv6

---

## 11. Respuestas correctas

| N.º | Respuesta | Explicación |
|---|---|---|
| 1 | B | La dirección MAC se utiliza para entregar tramas entre interfaces Ethernet. |
| 2 | C | Si PC2 está en la misma red, PC1 utiliza la MAC de PC2. |
| 3 | B | Para llegar a otra red, la primera trama se envía al gateway. |
| 4 | D | Los routers generan nuevas tramas con direcciones MAC apropiadas para cada enlace. |
| 5 | C | La dirección MAC broadcast contiene 48 bits en 1. |
| 6 | B | Los routers separan dominios de difusión. |
| 7 | C | ARP descubre la dirección MAC correspondiente a una IPv4 local. |
| 8 | B | ARP Request utiliza normalmente una trama broadcast. |
| 9 | A | La tabla ARP almacena asociaciones entre IPv4 y MAC. |
| 10 | D | IPv6 utiliza Neighbor Discovery mediante ICMPv6. |
