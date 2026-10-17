
# Módulo 17: Solución de Problemas de Red

## 1. ¿Qué es la solución de problemas de red?

La solución de problemas de red (Network Troubleshooting) consiste en identificar, diagnosticar y corregir fallas que impiden la comunicación entre dispositivos.

Por ejemplo:
- Una PC no tiene conexión a Internet.
- Un dispositivo recibe una dirección IPv4 incorrecta.
- Una PC no puede comunicarse con su gateway.
- Un nombre de dominio no se resuelve.
- Un servidor está conectado, pero su aplicación no responde.

Para investigar estas situaciones utilizamos herramientas de línea de comandos (CLI).

---

## 2. Comandos principales de diagnóstico

| Comando | Función principal |
|---|---|
| `ipconfig` | Muestra la configuración IP de una PC con Windows. |
| `ping` | Comprueba si un host responde mediante ICMP. |
| `netstat` | Muestra información sobre conexiones y puertos de red. |
| `tracert` | Permite identificar los saltos de una ruta hacia el destino en Windows. |
| `nslookup` | Consulta información DNS de un dominio. |

**Recuerda:** Cada comando permite investigar un problema diferente.

---

## 3. Comando ipconfig

`ipconfig` se utiliza en Windows para consultar la configuración de red de una computadora.

Es especialmente útil cuando una PC no logra comunicarse con otros dispositivos.

### 3.1 ipconfig

```cmd
ipconfig
```

Muestra información básica:

- Dirección IPv4.
- Máscara de subred.
- Puerta de enlace predeterminada.

**Ejemplo:**

```text
Dirección IPv4:         192.168.1.10
Máscara de subred:      255.255.255.0
Puerta de enlace:       192.168.1.1
```

Esta información permite comprobar si la PC pertenece a la red correcta.

### 3.2 ipconfig /all

```cmd
ipconfig /all
```

Muestra información más detallada:

- Dirección IPv4.
- Máscara de subred.
- Dirección física (MAC).
- Gateway predeterminado.
- Servidores DNS.
- Estado de DHCP.
- Servidor DHCP.
- Información de concesión DHCP.

**Ejemplo:**

```text
Dirección IPv4:          192.168.1.10
Máscara:                 255.255.255.0
Gateway:                 192.168.1.1
Servidor DHCP:           192.168.1.1
Servidor DNS:            8.8.8.8
DHCP habilitado:         Sí
```

**Importante:** Si el servidor DNS está mal configurado, es posible que la PC pueda comunicarse mediante direcciones IP, pero no utilizando nombres de dominio.

---

## 4. Comandos ipconfig /release y /renew

Estos comandos se utilizan cuando una PC obtiene su configuración IP mediante DHCP.

### 4.1 ipconfig /release

```cmd
ipconfig /release
```

Libera la concesión IPv4 obtenida mediante DHCP.

Después de ejecutarlo, la PC puede quedarse temporalmente sin su configuración IPv4 dinámica.

### 4.2 ipconfig /renew

```cmd
ipconfig /renew
```

Solicita una concesión IPv4 al servidor DHCP.

Puede ser útil cuando la configuración anterior está incorrecta o desactualizada.

### Ejemplo práctico

Una PC recibió una dirección IPv4 incorrecta y queremos solicitar otra configuración.

```cmd
ipconfig /release
ipconfig /renew
ipconfig
```

**Proceso:**

1. Se libera la concesión DHCP actual.
2. Se solicita una concesión al servidor DHCP.
3. Se consulta la configuración obtenida.

**Importante:** Estos comandos no solucionan problemas de cableado, Wi-Fi o servidores DHCP que no responden.

Además, no sirven para renovar una dirección IPv4 configurada manualmente como estática.

---

## 5. ¿Qué pasa si DHCP no funciona?

Cuando una PC está configurada para obtener su IPv4 automáticamente, pero no logra comunicarse con un servidor DHCP, puede asignarse una dirección de enlace local mediante APIPA.

### APIPA

Rango:

`169.254.0.0/16`

Máscara:

`255.255.0.0`

Ejemplo:

`169.254.10.25`

**¿Qué significa?**

La PC no consiguió una concesión DHCP y se autoconfiguró con una dirección IPv4 de enlace local.

Esta dirección puede permitir comunicación con otros dispositivos compatibles dentro del mismo enlace, pero normalmente no proporciona acceso a Internet mediante un router.

### ¿Qué debemos revisar?

1. Verificar que el cable Ethernet esté conectado o que el Wi-Fi funcione.
2. Comprobar que la tarjeta de red esté habilitada.
3. Revisar si el servidor DHCP está disponible.
4. Ejecutar `ipconfig /all`.
5. Intentar renovar la configuración mediante `ipconfig /renew`.

**Recuerda:** Una dirección `169.254.x.x` suele indicar que el host no obtuvo una dirección válida mediante DHCP.

---

## 6. Comando ping

`ping` es una de las herramientas más utilizadas para comprobar conectividad IP.

Utiliza mensajes ICMP Echo Request y Echo Reply.

### ¿Cómo funciona?

1. El dispositivo origen envía una solicitud ICMP Echo Request.
2. El dispositivo destino recibe la solicitud.
3. Si puede y tiene permitido responder, envía un ICMP Echo Reply.
4. El origen recibe la respuesta y comprueba la conectividad.

### Ejemplo

```cmd
ping 192.168.1.1
```

Resultado exitoso:

```text
Respuesta desde 192.168.1.1:
bytes=32 tiempo<1ms TTL=64
```

Esto indica que recibimos una respuesta del dispositivo consultado.

### Ejemplo de error

```text
Tiempo de espera agotado para esta solicitud.
```

Puede significar:

- Problemas de conectividad.
- Dispositivo de destino apagado.
- Firewall que bloquea ICMP.
- Problemas de enrutamiento.
- Pérdida de paquetes.

**Importante:** Un ping fallido no demuestra necesariamente que el dispositivo esté desconectado.

---

## 7. Interpretación de los resultados de ping

Podemos utilizar ping para identificar dónde se encuentra un problema.

### 7.1 Ping al gateway

```cmd
ping 192.168.1.1
```

Si responde, significa que existe conectividad IP con el gateway.

Si falla, debemos revisar:

- Configuración IP local.
- Máscara de subred.
- Gateway configurado.
- Cableado o conexión Wi-Fi.
- Estado del router.
- Reglas que bloqueen ICMP.

### 7.2 Ping a una dirección IP externa

```cmd
ping 8.8.8.8
```

Si responde, existe conectividad IP hacia ese destino externo.

Si el gateway responde, pero la IP externa no, el problema podría encontrarse en:

- El router.
- La conexión con el ISP.
- Las rutas configuradas.
- Un firewall.
- El dispositivo remoto.

### 7.3 Ping a un nombre de dominio

```cmd
ping www.cisco.com
```

Antes de enviar las solicitudes ICMP, el sistema necesita resolver el nombre mediante DNS.

Si el ping a una IP funciona, pero el nombre no se resuelve, puede existir un problema DNS.

**Atención:** Si el nombre se resuelve correctamente, pero no responde al ping, DNS podría estar funcionando y el destino simplemente estar bloqueando ICMP.

---

## 8. Tabla para diagnosticar problemas

| Situación | Posible causa |
|---|---|
| IP `169.254.x.x` | No se obtuvo una concesión DHCP. |
| IP incorrecta | Configuración manual incorrecta o DHCP mal configurado. |
| Ping al gateway falla | Problema local, configuración o bloqueo ICMP. |
| Gateway responde, pero Internet no | Problema de enrutamiento, ISP, firewall u otro punto de la ruta. |
| Ping a IP funciona, pero falla la resolución de nombres | Posible problema DNS. |
| Ping funciona, pero la aplicación no | Posible problema de aplicación, servicio, puerto o firewall. |
| `ipconfig /renew` falla | DHCP inaccesible o problema de conectividad. |

**Recuerda:** Los resultados permiten formular hipótesis, pero debemos realizar otras pruebas antes de confirmar la causa.

---

## 9. Comando netstat

`netstat` permite consultar conexiones y puertos utilizados por una computadora.

### Comandos en Windows

```cmd
netstat
```

Muestra información de conexiones de red.

```cmd
netstat -an
```

Muestra conexiones y puertos en formato numérico.

```cmd
netstat -ano
```

Muestra conexiones y el identificador del proceso (PID).

### Ejemplo

```text
Proto  Dirección local       Dirección remota       Estado
TCP    192.168.1.10:50000    192.168.1.20:80       ESTABLISHED
```

Indica una conexión TCP establecida entre dos dispositivos.

**Utilidad:** Permite verificar conexiones de red y servicios que están escuchando en determinados puertos.

---

## 10. Comando tracert

`tracert` permite identificar los saltos de red hacia un destino.

En Windows:

```cmd
tracert www.cisco.com
```

En Linux normalmente utilizamos:

```bash
traceroute www.cisco.com
```

### Ejemplo simplificado

```text
1    192.168.1.1
2    10.0.0.1
3    200.10.10.1
4    Destino
```

Cada línea representa un salto que respondió durante la prueba.

### ¿Para qué sirve?

- Identificar routers intermedios.
- Investigar problemas de enrutamiento.
- Detectar en qué parte de una ruta dejan de recibirse respuestas.

**Importante:** `tracert` no garantiza mostrar todos los routers ni una ruta exacta en todos los casos. Algunos dispositivos bloquean o limitan las respuestas.

---

## 11. Comando nslookup

`nslookup` permite consultar información DNS.

### Ejemplo

```cmd
nslookup www.cisco.com
```

Si el servidor DNS responde correctamente, puede mostrar las direcciones IP asociadas con el dominio.

### ¿Cuándo lo utilizamos?

Cuando:
- Las conexiones por IP funcionan.
- Los nombres de dominio no se resuelven.
- Queremos comprobar qué información devuelve un servidor DNS.

**Recuerda:** `nslookup` comprueba la resolución DNS, no que el servicio web esté disponible.

---

## 12. Procedimiento recomendado para diagnosticar una red

Cuando una PC no tiene acceso a Internet, podemos seguir este orden:

### Paso 1: Comprobar la configuración IP

```cmd
ipconfig /all
```

Revisamos IP, máscara, gateway y DNS.

### Paso 2: Comprobar la conectividad local

```cmd
ping 192.168.1.1
```

Verificamos si el gateway responde.

### Paso 3: Comprobar conectividad externa

```cmd
ping 8.8.8.8
```

Comprobamos si podemos alcanzar una dirección IP externa.

### Paso 4: Comprobar DNS

```cmd
nslookup www.cisco.com
```

Verificamos si el dominio puede resolverse.

### Paso 5: Revisar la ruta

```cmd
tracert 8.8.8.8
```

Investigamos los saltos hacia el destino.

### Paso 6: Comprobar conexiones y servicios

```cmd
netstat -ano
```

Revisamos las conexiones y puertos de red en Windows.

**Importante:** No debemos ejecutar todos los comandos obligatoriamente. Seleccionamos las pruebas según los síntomas del problema.

---

## 13. Puntos clave para el examen

- `ipconfig` muestra la configuración IP en Windows.
- `ipconfig /all` muestra información adicional como DNS, MAC y DHCP.
- `ipconfig /release` libera una concesión IPv4 DHCP.
- `ipconfig /renew` solicita una concesión IPv4 DHCP.
- APIPA utiliza el bloque `169.254.0.0/16`.
- `ping` utiliza ICMP Echo Request y Echo Reply.
- Un ping exitoso confirma que se recibió una respuesta ICMP del destino.
- Un ping fallido no significa necesariamente que no exista conectividad.
- Si una IP funciona pero un dominio no se resuelve, debemos investigar DNS.
- `nslookup` permite consultar información DNS.
- `netstat` muestra conexiones y puertos de red.
- `tracert` permite investigar los saltos hacia un destino.
- Si una aplicación falla pero el ping funciona, puede existir un problema en el servicio o puerto correspondiente.

---

## 14. Preguntas de repaso tipo Cisco

**1. ¿Qué comando de Windows muestra la dirección IPv4, máscara de subred y puerta de enlace predeterminada?**

- A) netstat
- B) ipconfig
- C) tracert
- D) nslookup

**2. ¿Qué comando muestra información detallada sobre DNS, DHCP y la dirección MAC de una PC con Windows?**

- A) ipconfig /renew
- B) ping
- C) ipconfig /all
- D) netstat

**3. Una computadora necesita solicitar una nueva concesión DHCP. ¿Qué comando debe utilizar?**

- A) ipconfig /release
- B) ipconfig /renew
- C) nslookup
- D) tracert

**4. Una PC recibe la dirección IPv4 169.254.25.10. ¿Qué situación es más probable?**

- A) La PC recibió una dirección pública del ISP.
- B) El servidor DNS asignó correctamente la IP.
- C) La PC tiene una ruta predeterminada válida.
- D) La PC no pudo obtener una concesión DHCP y utilizó APIPA.

**5. ¿Qué protocolo utiliza el comando ping para comprobar conectividad?**

- A) TCP
- B) UDP
- C) ICMP
- D) DHCP

**6. Una PC puede hacer ping a 8.8.8.8, pero no logra resolver www.cisco.com. ¿Qué servicio debemos investigar primero?**

- A) DNS
- B) FTP
- C) SSH
- D) ARP

**7. Una PC no puede hacer ping a su gateway predeterminado. ¿Qué debemos revisar primero?**

- A) El servidor de correo electrónico.
- B) La conexión local y la configuración IP.
- C) El protocolo FTP.
- D) El contenido de las páginas web.

**8. ¿Qué comando de Windows permite investigar los saltos hacia una dirección IP remota?**

- A) ipconfig
- B) nslookup
- C) netstat
- D) tracert

**9. ¿Qué comando permite consultar las conexiones TCP activas de una computadora?**

- A) netstat
- B) ping
- C) nslookup
- D) ipconfig /release

**10. Una PC puede hacer ping correctamente a un servidor, pero no puede acceder a su aplicación web. ¿Cuál es una posible causa?**

- A) La dirección MAC de la PC necesariamente está dañada.
- B) El protocolo ICMP dejó de funcionar.
- C) El servicio web no está ejecutándose o su puerto está bloqueado.
- D) La PC no puede comunicarse mediante IP.

---

## 15. Respuestas correctas

| N.º | Respuesta | Explicación |
|---|---|---|
| 1 | B | `ipconfig` muestra la configuración IP básica de Windows. |
| 2 | C | `ipconfig /all` muestra DNS, MAC, DHCP y otros datos. |
| 3 | B | `ipconfig /renew` solicita una concesión DHCP. |
| 4 | D | APIPA se utiliza cuando no se consigue una concesión IPv4 DHCP. |
| 5 | C | Ping utiliza mensajes ICMP Echo Request y Echo Reply. |
| 6 | A | Si existe conectividad por IP pero falla la resolución de nombres, debemos comprobar DNS. |
| 7 | B | Se debe investigar primero la conectividad y configuración local. |
| 8 | D | `tracert` permite observar los saltos que responden hacia el destino. |
| 9 | A | `netstat` muestra conexiones de red y puertos. |
| 10 | C | El servicio web podría estar detenido o el puerto bloqueado, aunque el servidor responda a ping. |
