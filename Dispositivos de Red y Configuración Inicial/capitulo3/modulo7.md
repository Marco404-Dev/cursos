
# Módulo 7: Resolución de Direcciones (ARP)

**Curso:** Cisco Networking Academy — Dispositivos de Red y Configuración Inicial

## 1. ¿Qué es ARP?

ARP (Address Resolution Protocol) es un protocolo que permite descubrir la dirección MAC asociada a una dirección IPv4 dentro de una red local.

### Funciones principales

1. Resolver direcciones IPv4 a direcciones MAC.
2. Mantener una tabla de asociaciones IPv4-MAC.

**Ejemplo:**

Una PC conoce la dirección IPv4 `192.168.1.20`, pero desconoce su dirección MAC.

Utiliza ARP para descubrirla antes de enviar una trama Ethernet.

**Importante:** ARP funciona con IPv4. IPv6 utiliza Neighbor Discovery (ND) mediante ICMPv6.

## 2. Tabla ARP o caché ARP

Es una tabla que almacena temporalmente asociaciones entre direcciones IPv4 y MAC.

### Ejemplo

| Dirección IPv4 | Dirección MAC |
|---|---|
| 192.168.1.1 | AA:BB:CC:11:22:33 |
| 192.168.1.10 | AA:BB:CC:44:55:66 |
| 192.168.1.20 | AA:BB:CC:77:88:99 |

Cuando una PC necesita enviar una trama, consulta su tabla ARP.

- Si conoce la MAC correspondiente, la utiliza.
- Si no conoce la MAC, envía una solicitud ARP.

**Recuerda:** La tabla ARP almacena asociaciones IP-MAC; la tabla MAC del switch almacena asociaciones MAC-puerto.

## 3. Solicitud ARP (ARP Request)

Se utiliza cuando un dispositivo necesita descubrir una dirección MAC.

### Funcionamiento

1. PC-A conoce la IPv4 de PC-B.
2. PC-A revisa su tabla ARP.
3. Si no encuentra la MAC, envía una solicitud ARP.
4. La solicitud utiliza la dirección MAC broadcast.
5. Todos los dispositivos de la LAN reciben la solicitud.
6. El dispositivo que tiene la IPv4 solicitada responde.

### Ejemplo

PC-A:

- IP: `192.168.1.10`
- MAC: `AA:AA:AA:AA:AA:AA`

PC-B:

- IP: `192.168.1.20`
- MAC: `BB:BB:BB:BB:BB:BB`

PC-A necesita conocer la MAC de `192.168.1.20`.

Envía una solicitud equivalente a:

**¿Quién tiene 192.168.1.20? Responde a 192.168.1.10.**

### Encabezado Ethernet de la solicitud ARP

| Campo | Valor |
|---|---|
| MAC origen | MAC de PC-A |
| MAC destino | FF:FF:FF:FF:FF:FF |
| EtherType | 0x0806 |

**Importante:**

- La solicitud ARP utiliza broadcast Ethernet.
- ARP se encapsula directamente en Ethernet.
- No utiliza un encabezado IPv4.
- Un router no reenvía normalmente las solicitudes ARP a otras redes.

## 4. Respuesta ARP (ARP Reply)

El dispositivo que tiene la IPv4 solicitada envía una respuesta con su dirección MAC.

### Ejemplo

PC-B responde a PC-A:

**192.168.1.20 tiene la MAC BB:BB:BB:BB:BB:BB.**

### Encabezado Ethernet de la respuesta

| Campo | Valor |
|---|---|
| MAC origen | MAC de PC-B |
| MAC destino | MAC de PC-A |
| EtherType | 0x0806 |

La respuesta ARP normalmente es unicast.

Después de recibirla, PC-A almacena la asociación en su tabla ARP.

### Diferencia fundamental

| Solicitud ARP | Respuesta ARP |
|---|---|
| Normalmente broadcast. | Normalmente unicast. |
| Pregunta por una dirección MAC. | Informa la dirección MAC correspondiente. |
| MAC destino FF:FF:FF:FF:FF:FF. | MAC destino del solicitante. |

## 5. Comunicación ARP dentro de la misma red

Supongamos:

PC-A:

- IP: `192.168.1.10/24`
- MAC: `AA:AA:AA:AA:AA:AA`

PC-B:

- IP: `192.168.1.20/24`
- MAC: `BB:BB:BB:BB:BB:BB`

Ambas computadoras pertenecen a la red:

`192.168.1.0/24`

### Proceso

1. PC-A identifica que PC-B está en su misma red.
2. Busca la MAC de PC-B en su tabla ARP.
3. Si no la conoce, envía una solicitud ARP.
4. PC-B responde con su MAC.
5. PC-A envía la trama Ethernet directamente a PC-B.

### Direcciones utilizadas

**Paquete IPv4:**

- IP origen: `192.168.1.10`
- IP destino: `192.168.1.20`

**Trama Ethernet:**

- MAC origen: MAC de PC-A.
- MAC destino: MAC de PC-B.

**Importante:** Para comunicarse con otro dispositivo de la misma red, normalmente no necesita enviar el paquete al gateway.

## 6. ARP para comunicarse con otra red

Si el destino pertenece a otra red, la PC necesita enviar el paquete al gateway predeterminado.

### Ejemplo

PC-A:

- IP: `192.168.1.10/24`
- Gateway: `192.168.1.1`

Servidor remoto:

- IP: `10.10.10.20`

### Proceso

1. PC-A compara su red con la dirección IP de destino.
2. Identifica que el servidor está en otra red.
3. Busca en su tabla ARP la MAC del gateway `192.168.1.1`.
4. Si no la conoce, envía una solicitud ARP preguntando por el gateway.
5. El router responde con su dirección MAC.
6. PC-A envía la trama al router.
7. El router reenvía el paquete hacia la red remota.

### Direcciones utilizadas

**Paquete IP:**

- IP origen: `192.168.1.10`
- IP destino: `10.10.10.20`

**Trama Ethernet inicial:**

- MAC origen: MAC de PC-A.
- MAC destino: MAC del gateway.

**Recuerda:** Si el destino está en otra red, ARP busca la MAC del siguiente salto (normalmente el gateway), no la MAC del servidor remoto.

## 7. ¿Qué ocurre si nadie responde a ARP?

Si un dispositivo necesita una dirección MAC y nadie responde a sus solicitudes ARP, no podrá entregar la trama a ese siguiente salto.

**Ejemplo:**

PC-A busca la MAC de `192.168.1.20`, pero PC-B está apagada.

PC-A envía solicitudes ARP, pero no recibe respuesta.

Después de agotar sus intentos, no puede enviar la trama al destino.

**Importante:** El paquete pendiente puede descartarse porque no se logró resolver la dirección MAC necesaria.

## 8. Eliminación de entradas ARP

Las entradas ARP dinámicas no permanecen indefinidamente.

Los dispositivos utilizan temporizadores para eliminar o renovar las asociaciones almacenadas.

### Tipos de entradas

| Tipo | Característica |
|---|---|
| Dinámica | Se aprende automáticamente y puede caducar. |
| Estática | Se configura manualmente y normalmente permanece hasta que se elimina o modifica. |

Los tiempos de caducidad dependen del sistema operativo y de su configuración.

Cuando una asociación ya no está disponible, puede ser necesario realizar otra solicitud ARP.

## 9. Comandos ARP importantes

### Windows

Mostrar la tabla ARP:

```cmd
arp -a
```

Eliminar una entrada ARP específica:

```cmd
arp -d 192.168.1.20
```

### Router Cisco

Mostrar la tabla ARP:

```cisco
show ip arp
```

También puede utilizarse:

```cisco
show arp
```

**Importante:** Estos comandos permiten verificar qué asociaciones IPv4-MAC conoce el dispositivo.

## 10. Problemas relacionados con ARP

### 10.1. Exceso de solicitudes ARP

Las solicitudes ARP utilizan broadcast.

Por eso, todos los dispositivos del dominio de difusión reciben las solicitudes.

Si muchos dispositivos envían solicitudes simultáneamente, puede generarse tráfico adicional.

Esto puede afectar temporalmente el rendimiento de la LAN.

### 10.2. ARP Spoofing y ARP Poisoning

ARP Spoofing es una técnica de suplantación de direcciones ARP.

Un atacante puede enviar información falsa para relacionar una dirección IPv4 legítima con una MAC incorrecta.

**Ejemplo:**

Un atacante intenta convencer a una PC de que su propia MAC corresponde a la dirección IP del gateway.

Si la PC acepta la asociación incorrecta, podría enviar tráfico hacia el atacante.

### Consecuencias

- Intercepción de comunicaciones.
- Redirección de tráfico.
- Interrupción de conexiones.

### Protección

Una medida de seguridad utilizada en switches administrables es:

**DAI (Dynamic ARP Inspection)**

Permite inspeccionar y validar mensajes ARP según las configuraciones de seguridad del switch.

## 11. Diferencia entre ARP y la tabla MAC del switch

| ARP | Tabla MAC |
|---|---|
| Relaciona IPv4 con MAC. | Relaciona MAC con puerto del switch. |
| La utilizan hosts y routers IPv4. | La utilizan switches de capa 2. |
| Ayuda a descubrir la MAC del siguiente salto. | Ayuda a decidir por qué puerto reenviar una trama. |
| Utiliza solicitudes y respuestas ARP. | Aprende mediante la MAC de origen de las tramas. |

**Ejemplo:**

PC-A conoce mediante ARP que `192.168.1.20` tiene la MAC `BB:BB:BB:BB:BB:BB`.

El switch conoce mediante su tabla MAC que esa dirección se encuentra en el puerto `Fa0/2`.

Así, ambos mecanismos cumplen funciones diferentes y complementarias.

---

# 10 preguntas de repaso — Módulo 7

### 1. ¿Cuál es la función principal de ARP?

A) Convertir nombres de dominio en direcciones IP.  
B) Descubrir una dirección MAC asociada a una dirección IPv4.  
C) Asignar direcciones IPv4 automáticamente.  
D) Seleccionar la mejor ruta entre redes.

<details>
<summary>Ver respuesta</summary>

✅ **B) Descubrir una dirección MAC asociada a una dirección IPv4.**

ARP permite conocer la dirección MAC correspondiente a una IPv4 del enlace local.

</details>

### 2. ¿Qué dirección MAC se utiliza como destino en una solicitud ARP normal?

A) 00:00:00:00:00:00.  
B) MAC del servidor DNS.  
C) FF:FF:FF:FF:FF:FF.  
D) MAC del gateway en todos los casos.

<details>
<summary>Ver respuesta</summary>

✅ **C) FF:FF:FF:FF:FF:FF.**

Las solicitudes ARP normales se envían mediante broadcast Ethernet.

</details>

### 3. ¿Cómo se envía normalmente una respuesta ARP?

A) Mediante unicast al dispositivo solicitante.  
B) Mediante broadcast a todas las redes.  
C) Mediante multicast IPv6.  
D) Mediante una conexión TCP.

<details>
<summary>Ver respuesta</summary>

✅ **A) Mediante unicast al dispositivo solicitante.**

El dispositivo que tiene la dirección IPv4 solicitada responde directamente al solicitante.

</details>

### 4. Una PC desea enviar un paquete a una IPv4 ubicada en otra red. ¿Qué MAC debe utilizar como destino de la trama Ethernet inicial?

A) MAC del servidor remoto.  
B) MAC del servidor DHCP.  
C) MAC broadcast obligatoriamente.  
D) MAC del gateway predeterminado.

<details>
<summary>Ver respuesta</summary>

✅ **D) MAC del gateway predeterminado.**

Cuando el destino pertenece a otra red, la PC envía la trama al siguiente salto, normalmente su router.

</details>

### 5. ¿Qué comando permite visualizar la tabla ARP en Windows?

A) show ip arp  
B) arp -a  
C) ipconfig /release  
D) show mac address-table

<details>
<summary>Ver respuesta</summary>

✅ **B) arp -a**

Permite consultar las asociaciones IPv4-MAC almacenadas en Windows.

</details>

### 6. ¿Qué comando permite visualizar la tabla ARP de un router Cisco?

A) show running-config  
B) show interfaces  
C) show ip arp  
D) show vlan brief

<details>
<summary>Ver respuesta</summary>

✅ **C) show ip arp**

Muestra las asociaciones entre direcciones IPv4 y direcciones MAC conocidas por el router.

</details>

### 7. ¿Qué valor EtherType identifica ARP en Ethernet?

A) 0x0806.  
B) 0x0800.  
C) 0x86DD.  
D) 0x8100.

<details>
<summary>Ver respuesta</summary>

✅ **A) 0x0806.**

Valores importantes:

- 0x0806 = ARP.
- 0x0800 = IPv4.
- 0x86DD = IPv6.

</details>

### 8. ¿Qué sucede si un host no consigue resolver la MAC necesaria mediante ARP?

A) Utiliza automáticamente la MAC de cualquier computadora.  
B) Convierte el paquete en IPv6.  
C) Envía el paquete directamente sin trama Ethernet.  
D) No puede entregar la trama al siguiente salto y puede descartar el paquete.

<details>
<summary>Ver respuesta</summary>

✅ **D) No puede entregar la trama al siguiente salto y puede descartar el paquete.**

Sin la dirección MAC necesaria, el dispositivo no puede realizar la entrega Ethernet correspondiente.

</details>

### 9. ¿Cuál es una diferencia entre ARP y la tabla MAC de un switch?

A) Ambos almacenan exclusivamente direcciones IPv6.  
B) ARP relaciona IPv4-MAC y la tabla MAC relaciona MAC-puerto.  
C) La tabla MAC se utiliza para resolver nombres DNS.  
D) ARP identifica puertos TCP.

<details>
<summary>Ver respuesta</summary>

✅ **B) ARP relaciona IPv4-MAC y la tabla MAC relaciona MAC-puerto.**

ARP identifica la dirección MAC que se necesita para la entrega local.

El switch utiliza su tabla MAC para saber por qué puerto reenviar la trama.

</details>

### 10. ¿Qué mecanismo de seguridad permite inspeccionar mensajes ARP para reducir ataques de suplantación?

A) DHCP Discover.  
B) DNS Lookup.  
C) Dynamic ARP Inspection (DAI).  
D) ICMP Echo Request.

<details>
<summary>Ver respuesta</summary>

✅ **C) Dynamic ARP Inspection (DAI).**

DAI permite validar mensajes ARP y ayuda a proteger la red contra ataques de ARP Spoofing.

</details>

---

**Fin del Módulo 7 — Resolución de Direcciones (ARP)**
