
# Módulo 14: Enrutamiento entre Redes

## 1. ¿Por qué necesitamos enrutamiento?

El **enrutamiento (Routing)** es el proceso que permite enviar paquetes de datos entre diferentes redes IP, seleccionando la mejor ruta disponible hacia su destino.

Cuando una red crece, es necesario dividirla en varias redes para mejorar su rendimiento, organización y seguridad.

### 1.1 ¿Para qué dividimos una red?

| Motivo | Explicación |
|---|---|
| Reducir broadcasts | Evitar que las difusiones afecten a toda la red. |
| Seguridad | Separar y proteger grupos de dispositivos. |
| Ubicación física | Conectar redes de diferentes edificios o sedes. |
| Organización lógica | Agrupar usuarios por departamentos o necesidades. |

**Ejemplo:**

Una universidad puede dividir su infraestructura en varias redes:

- Red de estudiantes: `192.168.10.0/24`
- Red de docentes: `192.168.20.0/24`
- Red administrativa: `192.168.30.0/24`

Para permitir la comunicación entre estas redes, se necesita un dispositivo que realice enrutamiento.

**Recuerda:** Los routers conectan redes diferentes y permiten controlar la comunicación entre ellas.

---

## 2. Diferencia entre Switch y Router

Ambos dispositivos reenvían información, pero trabajan principalmente con direcciones diferentes.

| Característica | Switch (Capa 2) | Router (Capa 3) |
|---|---|---|
| Dirección utilizada | MAC | IP |
| Unidad que reenvía | Trama | Paquete |
| Función principal | Conectar dispositivos de una LAN | Conectar diferentes redes IP |
| Tabla utilizada | Tabla MAC | Tabla de enrutamiento |
| Broadcast | Lo reenvía dentro de su VLAN | Normalmente no lo reenvía entre redes |

### Ejemplo

```text
PC1 ---- Switch ---- PC2
          |
          |
        Router
          |
          |
        Otra red
```

- El switch utiliza direcciones MAC para reenviar tramas.
- El router utiliza direcciones IP para decidir hacia dónde enviar paquetes.

**Importante:** Existen switches multicapa que también pueden realizar enrutamiento.

---

## 3. ¿Cómo funciona el enrutamiento?

Cuando una PC necesita comunicarse con un dispositivo ubicado en otra red, envía el paquete a su gateway predeterminado.

### Ejemplo

```text
Red A                                  Red B
192.168.1.0/24                         192.168.2.0/24

PC1 -------- R1 -------- R2 -------- PC2

PC1: 192.168.1.10                     PC2: 192.168.2.10
GW:  192.168.1.1
```

**Proceso:**

1. PC1 identifica que PC2 pertenece a una red diferente.
2. PC1 envía el paquete a su gateway (R1).
3. R1 recibe la trama y extrae el paquete IP.
4. R1 revisa la dirección IP de destino.
5. Consulta su tabla de enrutamiento.
6. Determina la interfaz de salida o el siguiente salto.
7. Encapsula el paquete en una nueva trama y lo reenvía.
8. Los routers siguientes continúan el proceso hasta llegar a PC2.

### ¿Qué sucede con las direcciones?

- La dirección IP de destino normalmente sigue siendo la de PC2.
- Las direcciones MAC cambian al generar nuevas tramas en cada enlace Ethernet.
- El router decide el camino utilizando la dirección IP de destino.

**Recuerda:** El router no necesita conocer inicialmente la MAC del destino final cuando está en una red remota; necesita conocer cómo llegar al siguiente salto.

---

## 4. Tabla de enrutamiento

La **tabla de enrutamiento (Routing Table)** contiene información sobre las redes de destino y las rutas que el router puede utilizar para alcanzarlas.

Cada router consulta esta tabla antes de reenviar un paquete.

### 4.1 ¿Qué contiene?

| Elemento | Función |
|---|---|
| Tipo de ruta | Indica cómo se aprendió la ruta. |
| Red de destino | Identifica la red a la que se quiere llegar. |
| Máscara o prefijo | Identifica la porción de red. |
| Siguiente salto | Dirección IP del siguiente router, cuando corresponde. |
| Interfaz de salida | Interfaz utilizada para enviar el paquete. |

### Ejemplo de tabla simplificada

| Tipo | Red de destino | Interfaz |
|---|---|---|
| C | 192.168.1.0/24 | G0/0 |
| C | 10.0.0.0/30 | G0/1 |
| S | 192.168.2.0/24 | G0/1 |

**Significado:**

- `C`: Connected (red conectada directamente).
- `S`: Static (ruta estática configurada por el administrador).

### 4.2 Tipos de rutas

**Rutas conectadas directamente:**
- Se incorporan cuando la interfaz correspondiente está configurada y operativa.
- El router conoce esas redes porque está conectado a ellas.

**Rutas estáticas:**
- Son configuradas manualmente por un administrador.
- Indican cómo llegar a determinadas redes.

**Rutas dinámicas:**
- Se aprenden mediante protocolos de enrutamiento.
- Permiten que los routers intercambien información sobre las redes.

### 4.3 ¿Qué pasa si no existe una ruta?

Si el router no encuentra una ruta válida hacia el destino y tampoco tiene una ruta predeterminada, descarta el paquete.

---

## 5. Ruta predeterminada (Default Route)

Una ruta predeterminada permite enviar paquetes hacia un siguiente salto cuando no existe una ruta más específica hacia la red de destino.

En IPv4 se representa mediante:

`0.0.0.0/0`

### Ejemplo

```text
PC ---- Router R1 ---- Router ISP ---- Internet
```

R1 puede utilizar una ruta predeterminada para enviar hacia el ISP los paquetes cuyos destinos no conoce mediante rutas más específicas.

### Comando Cisco

```bash
ip route 0.0.0.0 0.0.0.0 10.0.0.2
```

**Explicación:**

- `ip route`: permite configurar una ruta estática.
- `0.0.0.0 0.0.0.0`: representa la ruta predeterminada.
- `10.0.0.2`: dirección IP del siguiente salto.

**Importante:** La ruta predeterminada no garantiza que el paquete llegue a su destino. Solo indica hacia dónde debe reenviarse.

---

## 6. Puerta de enlace predeterminada

La puerta de enlace predeterminada (Default Gateway) es la dirección IP de la interfaz del router que permite a un host comunicarse con otras redes.

### Ejemplo

| Dispositivo | Dirección IPv4 |
|---|---|
| PC1 | 192.168.1.10 |
| Gateway | 192.168.1.1 |
| Servidor remoto | 192.168.2.20 |

Si PC1 quiere comunicarse con el servidor remoto:

1. Comprueba que la IP de destino no pertenece a su red local.
2. Identifica su gateway: `192.168.1.1`.
3. Utiliza ARP para descubrir la dirección MAC del gateway, si no la conoce.
4. Envía el paquete dentro de una trama Ethernet dirigida a la MAC del router.

**En la trama:**

- IP destino: `192.168.2.20`
- MAC destino: MAC del gateway.

### ¿Qué pasa si el gateway está mal configurado?

La PC puede seguir comunicándose con dispositivos de su misma red local, pero normalmente no podrá comunicarse con dispositivos de redes remotas.

### Diferencia importante

| Gateway predeterminado | Ruta predeterminada |
|---|---|
| Se configura en el host para llegar a otras redes. | Se configura en el router para destinos sin una ruta más específica. |
| Normalmente es la IP del router conectado a la LAN. | En IPv4 se representa como `0.0.0.0/0`. |

---

## 7. Redes de Área Local (LAN)

Una **LAN (Local Area Network)** es una red local o un conjunto de redes locales interconectadas que se encuentran bajo un mismo control administrativo.

Características:

- Puede abarcar una vivienda, oficina, universidad o varios edificios.
- Normalmente utiliza Ethernet o Wi-Fi.
- Generalmente permite velocidades de transmisión elevadas.
- Puede contener una o varias subredes IP.

### LAN e Intranet

| Concepto | Explicación |
|---|---|
| LAN | Red local bajo una misma administración. |
| Intranet | Red o conjunto de recursos privados de una organización, accesibles a usuarios autorizados. |

Una intranet puede utilizar la infraestructura LAN, pero también puede extenderse a varias ubicaciones.

---

## 8. Segmentos de red locales y remotos

Una red puede organizarse manteniendo los dispositivos en un solo segmento local o dividiéndolos en diferentes redes.

### 8.1 Todos los hosts en un segmento local

```text
PC1 ---- Switch 1 ---- Switch 2 ---- PC3
PC2 ----/                 \---- PC4

          192.168.1.0/24
```

Si todos pertenecen a la misma VLAN, comparten el mismo dominio de difusión.

**Ventajas:**

- Configuración sencilla.
- Menor costo y complejidad.
- Comunicación directa entre dispositivos de la misma red.
- Adecuado para redes pequeñas.

**Desventajas:**

- Mayor tráfico broadcast cuando aumenta la cantidad de hosts.
- Puede disminuir el rendimiento.
- Es más difícil aplicar políticas de seguridad diferenciadas.
- Puede complicarse la implementación de QoS.

### 8.2 Hosts divididos en redes diferentes

```text
Red A                                Red B
192.168.1.0/24                       192.168.2.0/24

PC1 ---- Switch ---- Router ---- Switch ---- PC3
PC2 ----/                       \---- PC4
```

Cada red tiene un dominio de difusión diferente.

**Ventajas:**

- Reduce el alcance del tráfico broadcast.
- Mejora la organización de la red.
- Permite implementar políticas de seguridad entre redes.
- Es más apropiado para infraestructuras grandes.

**Desventajas:**

- Requiere enrutamiento para comunicar las redes.
- Mayor complejidad de configuración.
- Puede aumentar el costo de implementación.
- El procesamiento y recorrido adicional pueden introducir latencia.

### Comparación

| Característica | Un segmento local | Varios segmentos |
|---|---|---|
| Configuración | Más sencilla | Más compleja |
| Costo | Generalmente menor | Puede ser mayor |
| Broadcast | Un dominio compartido | Dominios separados |
| Seguridad | Menor separación | Mayor capacidad de aislamiento |
| Enrutamiento entre segmentos | No necesario | Necesario |

---

## 9. Comandos Cisco importantes

Estos comandos son útiles para verificar la configuración de enrutamiento en Packet Tracer.

| Comando | Función |
|---|---|
| `show ip route` | Muestra la tabla de enrutamiento IPv4. |
| `show ip interface brief` | Muestra interfaces, direcciones IP y estados. |
| `ping 192.168.2.10` | Comprueba la conectividad hacia un destino. |
| `traceroute 192.168.2.10` | Permite observar la ruta hacia un destino. |
| `show running-config` | Muestra la configuración actual del router. |

### Ejemplo de ruta estática

Supongamos que R1 necesita llegar a la red `192.168.2.0/24` mediante el router vecino `10.0.0.2`.

```bash
enable
configure terminal
ip route 192.168.2.0 255.255.255.0 10.0.0.2
end
show ip route
```

**Explicación:**

- `192.168.2.0`: red de destino.
- `255.255.255.0`: máscara de la red de destino.
- `10.0.0.2`: dirección IP del siguiente salto.

La comunicación completa también requiere una ruta de retorno desde la red de destino, si no existe ya una ruta adecuada.

---

## 10. Puntos clave para el examen

- El enrutamiento permite la comunicación entre diferentes redes IP.
- Los routers toman decisiones de reenvío utilizando direcciones IP de capa 3.
- Los switches de capa 2 toman decisiones utilizando direcciones MAC.
- La tabla de enrutamiento contiene rutas hacia las redes de destino.
- Las rutas pueden ser conectadas, estáticas o dinámicas.
- `C` identifica una red conectada directamente.
- `S` identifica una ruta estática.
- Si no existe una ruta válida, el router descarta el paquete.
- La ruta predeterminada IPv4 es `0.0.0.0/0`.
- Un host utiliza su gateway para comunicarse con redes remotas.
- ARP permite descubrir la MAC del gateway en IPv4.
- Los routers separan dominios de difusión.
- Dividir una red mejora la organización y permite controlar el tráfico.
- `show ip route` permite revisar las rutas IPv4.

---

## 11. Preguntas de repaso tipo Cisco

**1. ¿Cuál es la función principal del enrutamiento?**

- A) Asignar direcciones MAC a los dispositivos.
- B) Determinar la mejor ruta para enviar paquetes entre redes.
- C) Convertir direcciones IP en nombres de dominio.
- D) Reenviar todas las tramas broadcast.

**2. ¿Qué dirección utiliza principalmente un router para tomar decisiones de reenvío?**

- A) Dirección MAC de origen.
- B) Dirección MAC de destino.
- C) Dirección IP de destino.
- D) Dirección IP del servidor DNS.

**3. ¿Qué información contiene principalmente una tabla de enrutamiento?**

- A) Las contraseñas de todos los hosts.
- B) Las direcciones MAC de todos los dispositivos.
- C) Las direcciones de red y las rutas para alcanzarlas.
- D) Los nombres de todos los usuarios conectados.

**4. ¿Qué significa la letra C en una tabla de enrutamiento Cisco?**

- A) Connected.
- B) Client.
- C) Configured.
- D) Computer.

**5. ¿Qué sucede cuando un router no encuentra una ruta válida hacia un destino ni dispone de una ruta predeterminada?**

- A) Envía el paquete a todos los dispositivos.
- B) Convierte el paquete IPv4 en IPv6.
- C) Envía el paquete automáticamente al servidor DNS.
- D) Descarta el paquete.

**6. ¿Cuál es la representación de una ruta predeterminada IPv4?**

- A) 255.255.255.255/32
- B) 192.168.1.0/24
- C) 0.0.0.0/0
- D) 127.0.0.1/8

**7. Una PC necesita enviar un paquete a una red remota. ¿Qué dirección MAC utiliza como destino en la primera trama Ethernet?**

- A) La MAC del servidor remoto.
- B) La MAC de su gateway predeterminado.
- C) La MAC de broadcast.
- D) La MAC del servidor DNS.

**8. ¿Qué ventaja ofrece dividir una LAN en varias redes mediante enrutamiento?**

- A) Elimina la necesidad de direcciones IP.
- B) Hace que todos los dispositivos compartan un único broadcast.
- C) Reduce los dominios de difusión y permite mayor control del tráfico.
- D) Evita completamente cualquier latencia.

**9. ¿Qué comando permite consultar la tabla de enrutamiento IPv4 en un router Cisco?**

- A) show mac address-table
- B) show ip route
- C) ipconfig
- D) show vlan brief

**10. Una PC tiene la IP 192.168.1.10/24, pero no tiene gateway configurado. ¿Qué comunicación normalmente seguirá funcionando?**

- A) La comunicación con dispositivos de su misma red local.
- B) La comunicación con cualquier red remota.
- C) La conexión con Internet mediante rutas automáticas.
- D) La comunicación con todas las redes externas sin router.

---

## 12. Respuestas correctas

| N.º | Respuesta | Explicación |
|---|---|---|
| 1 | B | El enrutamiento identifica la mejor ruta disponible para alcanzar otras redes. |
| 2 | C | Los routers utilizan la IP de destino para decidir el reenvío. |
| 3 | C | La tabla contiene información sobre redes y caminos para alcanzarlas. |
| 4 | A | C significa Connected, es decir, una red conectada directamente. |
| 5 | D | Si no existe una ruta válida, el router descarta el paquete. |
| 6 | C | 0.0.0.0/0 representa la ruta predeterminada IPv4. |
| 7 | B | La trama se envía inicialmente a la MAC del gateway. |
| 8 | C | La segmentación reduce el alcance del broadcast y permite controlar el tráfico. |
| 9 | B | show ip route muestra la tabla de enrutamiento IPv4. |
| 10 | A | Sin gateway, la PC normalmente puede seguir comunicándose dentro de su propia red local. |
