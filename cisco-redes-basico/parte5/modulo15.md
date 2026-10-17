
# Módulo 15: TCP, UDP y Números de Puerto

## 1. ¿Qué son TCP y UDP?

TCP y UDP son protocolos de la **capa 4 (Transporte)** del modelo OSI.

Su función es permitir la comunicación entre las aplicaciones de diferentes dispositivos a través de la red.

| Característica | TCP | UDP |
|---|---|---|
| Nombre | Transmission Control Protocol | User Datagram Protocol |
| Conexión | Orientado a conexión | No orientado a conexión |
| Fiabilidad | Confirma la recepción y retransmite datos perdidos | No garantiza la entrega |
| Velocidad | Mayor sobrecarga de control | Menor sobrecarga |
| Orden de entrega | Garantiza la entrega ordenada de datos | No garantiza el orden |
| Uso común | Web, correo, FTP, SSH | VoIP, videojuegos, DNS |

**Recuerda:**
- TCP prioriza la entrega fiable y ordenada.
- UDP prioriza la simplicidad y una menor sobrecarga.
- Ambos utilizan números de puerto.

---

## 2. Funcionamiento de TCP

TCP es un protocolo orientado a conexión que proporciona una entrega fiable y ordenada de datos.

### 2.1 ¿Cómo funciona?

1. Establece una conexión entre el emisor y el receptor.
2. Divide los datos en partes llamadas segmentos.
3. Utiliza números de secuencia para organizar los datos.
4. El receptor confirma la recepción mediante ACK.
5. Si el emisor detecta que faltan datos, los retransmite.
6. El receptor puede reconstruir los datos en el orden correcto.

### Ejemplo

Una PC está descargando un archivo.

```text
PC                           Servidor
 |                               |
 | <------ Segmento 1 ---------  |
 | --------- ACK 1 ----------->  |
 | <------ Segmento 2 ---------  |
 | --------- ACK 2 ----------->  |
 |                               |
 |       Segmento 3 perdido      |
 |                               |
 | <--- Retransmisión 3 -------  |
 | --------- ACK 3 ----------->  |
```

Si se pierden datos, TCP puede retransmitirlos sin necesidad de volver a enviar todo el archivo.

**Importante:** Los segmentos TCP pueden viajar por diferentes rutas IP. TCP se encarga de reconstruir el flujo de datos correctamente.

### 2.2 ¿Cuándo se utiliza TCP?

Se utiliza cuando es importante recibir los datos completos y ordenados.

Ejemplos:
- Transferencia de archivos mediante FTP.
- Acceso remoto mediante SSH.
- Correo electrónico.
- Navegación HTTP/HTTPS mediante TCP.

---

## 3. Funcionamiento de UDP

UDP es un protocolo no orientado a conexión.

Utiliza un sistema de entrega de **mejor esfuerzo (Best Effort)**.

Esto significa que envía datagramas sin confirmar su recepción ni garantizar su entrega.

### 3.1 ¿Cómo funciona?

1. La aplicación genera los datos.
2. UDP añade los puertos de origen y destino.
3. Envía los datagramas sin establecer previamente una conexión.
4. No espera confirmaciones ACK.
5. No retransmite automáticamente los datos perdidos.

### Ejemplo

Una persona realiza una llamada de voz por Internet.

```text
Emisor                       Receptor
  |                              |
  | -------- Audio 1 ----------> |
  | -------- Audio 2 ----------> |
  | --- Audio 3 (perdido) --X    |
  | -------- Audio 4 ----------> |
  |                              |
```

Si se pierde un datagrama de audio, la comunicación puede continuar sin esperar su retransmisión.

**¿Por qué se utiliza UDP?**

En aplicaciones en tiempo real, recibir los datos rápidamente puede ser más importante que recuperar información que ya llegó demasiado tarde.

### 3.2 ¿Cuándo se utiliza UDP?

Ejemplos:
- Llamadas VoIP.
- Videojuegos en línea.
- Consultas DNS habituales.
- Transmisiones multimedia en tiempo real.

**Importante:** Una aplicación puede implementar sus propios mecanismos de control sobre UDP si necesita mayor fiabilidad.

---

## 4. ¿Qué son los números de puerto?

Un **puerto** es un identificador numérico que utiliza TCP o UDP para dirigir los datos hacia una aplicación o servicio específico.

Las direcciones IP permiten identificar los dispositivos, mientras que los puertos ayudan a identificar las aplicaciones o servicios que se comunican.

### Ejemplo

Una computadora puede utilizar simultáneamente:

- Un navegador web.
- Un cliente de correo.
- Una aplicación de videollamadas.

Aunque todas las aplicaciones utilizan la misma dirección IP, pueden distinguirse mediante los números de puerto.

### 4.1 Puerto de origen y destino

Cada segmento TCP o datagrama UDP contiene:

| Puerto | Función |
|---|---|
| Origen | Identifica el extremo que envía los datos. |
| Destino | Identifica el servicio o extremo que recibe los datos. |

**Ejemplo de una solicitud HTTP:**

```text
Cliente                          Servidor
192.168.1.10                     192.168.1.20
Puerto: 50000                    Puerto: 80

       Solicitud HTTP
50000 -------------------------> 80

         Respuesta
50000 <------------------------- 80
```

- El cliente utiliza el puerto 50000 como puerto de origen.
- El servidor recibe la solicitud en el puerto 80.
- La respuesta se envía al puerto 50000 del cliente.

**Recuerda:** El puerto de origen ayuda a identificar la comunicación para que la respuesta llegue a la aplicación correspondiente.

---

## 5. Clasificación de los números de puerto

Los números de puerto TCP y UDP tienen 16 bits, por lo que sus valores van de 0 a 65535.

IANA administra el registro oficial de asignaciones de puertos.

| Categoría | Rango | Uso |
|---|---|---|
| Puertos conocidos (Well-Known) | 0 - 1023 | Servicios comunes |
| Puertos registrados (Registered) | 1024 - 49151 | Aplicaciones y servicios registrados |
| Puertos dinámicos o privados | 49152 - 65535 | Frecuentemente utilizados como puertos temporales |

**Nota:** El puerto 0 está reservado y no se utiliza como puerto normal de servicio.

### 5.1 Puertos conocidos

Son utilizados por servicios estandarizados.

| Puerto | Protocolo | Servicio |
|---|---|---|
| 20 | TCP | FTP (datos en modo activo) |
| 21 | TCP | FTP (control) |
| 22 | TCP | SSH |
| 23 | TCP | Telnet |
| 25 | TCP | SMTP |
| 53 | TCP/UDP | DNS |
| 67 | UDP | DHCP servidor |
| 68 | UDP | DHCP cliente |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 143 | TCP | IMAP |
| 443 | TCP | HTTPS tradicional |
| 443 | UDP | HTTP/3 mediante QUIC |

### 5.2 Puertos registrados

Van desde el 1024 hasta el 49151.

Se utilizan para diversas aplicaciones y servicios que pueden tener asignaciones registradas.

Ejemplo:

- PostgreSQL utiliza normalmente el puerto TCP 5432.

### 5.3 Puertos dinámicos o privados

Van desde el 49152 hasta el 65535.

Se utilizan frecuentemente como puertos temporales de origen cuando un cliente inicia una comunicación.

**Importante:** El sistema operativo puede utilizar otros rangos de puertos efímeros. Los puertos de origen no siempre pertenecen al rango 49152-65535.

---

## 6. ¿Qué es un socket?

Un **socket** es un extremo de comunicación identificado mediante una dirección IP y un número de puerto, dentro del contexto de un protocolo de transporte.

Se representa así:

`Dirección_IP:Puerto`

### Ejemplo

Una PC solicita una página web.

**Cliente:**

`192.168.1.5:1099`

**Servidor:**

`192.168.1.7:80`

La PC utiliza el puerto 1099 para comunicarse con el servidor web que escucha en el puerto 80.

### 6.1 Par de sockets (Socket Pair)

Un par de sockets identifica ambos extremos de una comunicación.

```text
Cliente                      Servidor

192.168.1.5:1099 ----------> 192.168.1.7:80
```

Par de sockets:

`192.168.1.5:1099 <-> 192.168.1.7:80`

### 6.2 ¿Para qué sirven?

Permiten:
- Identificar los extremos de una comunicación.
- Distinguir conversaciones simultáneas.
- Dirigir las respuestas a la aplicación correspondiente.

### Ejemplo con dos servicios

Una PC solicita simultáneamente servicios FTP y HTTP a un servidor.

| Servicio | IP cliente | Puerto origen | Puerto destino |
|---|---|---|---|
| FTP | 192.168.1.5 | 1305 | 21 |
| HTTP | 192.168.1.5 | 1099 | 80 |

Aunque ambas solicitudes provienen de la misma computadora, utilizan distintos números de puerto.

**Recuerda:** Una conexión TCP se identifica mediante la combinación de IP de origen, puerto de origen, IP de destino y puerto de destino, junto con el protocolo de transporte.

---

## 7. ¿Cómo puede una PC tener varias conexiones simultáneas?

Una misma computadora puede comunicarse con varios servidores al mismo tiempo.

### Ejemplo

```text
                  PC
             192.168.1.10
                  |
        ---------------------
        |         |         |
       Web       FTP       SSH
        |         |         |
        v         v         v
       :80       :21       :22
```

La capa de transporte utiliza los números de puerto para diferenciar las comunicaciones.

Por ejemplo:

| Aplicación | Puerto origen | Puerto destino |
|---|---|---|
| Navegador | 50001 | 80 |
| FTP | 50002 | 21 |
| SSH | 50003 | 22 |

Cuando llegan las respuestas, el sistema operativo puede identificar a qué comunicación pertenecen.

Este proceso forma parte de la **multiplexación y demultiplexación** de la capa de transporte.

---

## 8. ¿Qué es el comando netstat?

`netstat` es una utilidad que permite consultar información sobre las conexiones de red de una computadora.

Puede mostrar:
- Protocolos utilizados.
- Direcciones IP locales y remotas.
- Números de puerto.
- Estados de las conexiones TCP.
- Puertos en escucha.

### 8.1 Comandos importantes

**Windows:**

```bash
netstat
```

Muestra información de conexiones de red.

```bash
netstat -an
```

Muestra conexiones y puertos en formato numérico.

```bash
netstat -ano
```

Muestra conexiones, puertos y el identificador del proceso (PID).

### Ejemplo de resultado

```text
Proto  Local Address       Foreign Address      State
TCP    192.168.1.10:50000  142.250.1.1:443      ESTABLISHED
TCP    0.0.0.0:135         0.0.0.0:0            LISTENING
```

**Explicación:**

| Campo | Significado |
|---|---|
| Proto | Protocolo de transporte utilizado. |
| Local Address | Dirección IP y puerto local. |
| Foreign Address | Dirección IP y puerto remoto. |
| ESTABLISHED | Conexión TCP establecida. |
| LISTENING | Puerto esperando conexiones entrantes. |

### 8.2 ¿Por qué es importante?

Permite:
- Identificar conexiones TCP activas.
- Comprobar qué puertos están abiertos o en escucha.
- Detectar conexiones desconocidas para investigarlas.
- Solucionar problemas de conectividad.

**Importante:** Una conexión desconocida no significa necesariamente que exista un ataque. Debe investigarse antes de considerarla maliciosa.

---

## 9. Diferencias importantes

| Concepto | Función |
|---|---|
| TCP | Transporte fiable, orientado a conexión y ordenado. |
| UDP | Transporte no orientado a conexión, sin garantía de entrega. |
| Dirección IP | Identifica un dispositivo o interfaz de red. |
| Puerto | Identifica un servicio o extremo de comunicación. |
| Socket | Combina una dirección IP con un número de puerto. |
| Par de sockets | Identifica los extremos de una comunicación. |
| ACK | Confirmación de recepción utilizada por TCP. |
| netstat | Permite consultar conexiones y puertos de red. |

---

## 10. Puntos clave para el examen

- TCP y UDP pertenecen a la capa 4 del modelo OSI.
- TCP es orientado a conexión; UDP no lo es.
- TCP utiliza ACK y retransmisiones para proporcionar fiabilidad.
- UDP no garantiza que los datagramas lleguen ni que lleguen ordenados.
- TCP utiliza números de secuencia.
- Los números de puerto identifican servicios y extremos de comunicación.
- Los puertos TCP y UDP van del 0 al 65535.
- Los puertos conocidos van del 0 al 1023, con el 0 reservado.
- Los puertos registrados van del 1024 al 49151.
- Los puertos dinámicos o privados van del 49152 al 65535.
- HTTP utiliza normalmente TCP 80.
- HTTPS tradicional utiliza TCP 443.
- FTP utiliza TCP 21 para control.
- SSH utiliza TCP 22.
- DNS utiliza UDP 53 y también TCP 53 cuando corresponde.
- Un socket combina una dirección IP y un puerto.
- Un par de sockets identifica ambos extremos de la comunicación.
- `netstat` permite revisar conexiones y puertos.

---

## 11. Preguntas de repaso tipo Cisco

**1. ¿Cuál es la principal diferencia entre TCP y UDP?**

- A) TCP utiliza direcciones MAC y UDP utiliza direcciones IP.
- B) TCP proporciona entrega fiable y UDP no garantiza la entrega.
- C) UDP funciona en la capa 3 y TCP en la capa 2.
- D) TCP no utiliza números de puerto.

**2. ¿Qué mecanismo utiliza TCP para confirmar la recepción de datos?**

- A) ARP
- B) DNS
- C) ACK
- D) DHCP

**3. ¿Qué protocolo de transporte es apropiado cuando se necesita baja latencia y se tolera cierta pérdida de datos?**

- A) FTP
- B) TCP
- C) HTTP
- D) UDP

**4. ¿Cuál es la función principal de los números de puerto?**

- A) Identificar las aplicaciones o servicios involucrados en una comunicación.
- B) Identificar físicamente una tarjeta de red.
- C) Determinar la dirección MAC del gateway.
- D) Asignar direcciones IPv4 automáticamente.

**5. ¿Cuál de los siguientes puertos se utiliza normalmente para HTTP tradicional?**

- A) 22
- B) 80
- C) 25
- D) 53

**6. ¿Cuál es el rango de los puertos registrados según IANA?**

- A) 0 - 1023
- B) 1 - 255
- C) 1024 - 49151
- D) 49152 - 65535

**7. Una PC tiene la dirección 192.168.1.5 y utiliza el puerto 1099. ¿Cuál es la representación correcta de su socket?**

- A) 192.168.1.5:1099
- B) 192.168.1.5/1099
- C) 1099:192.168.1.5:80
- D) 192.168.1.5-255.255.255.0

**8. ¿Cuál de las siguientes opciones representa correctamente un par de sockets?**

- A) 192.168.1.1 y 255.255.255.0
- B) AA:BB:CC:DD:EE:FF y 192.168.1.10
- C) 192.168.1.5:1099 y 192.168.1.7:80
- D) 192.168.1.0/24 y 192.168.2.0/24

**9. ¿Qué comando permite visualizar las conexiones TCP activas en una computadora?**

- A) ping
- B) ipconfig
- C) arp -a
- D) netstat

**10. Una PC realiza simultáneamente dos solicitudes HTTP al mismo servidor. ¿Cómo puede el sistema distinguir las conexiones TCP?**

- A) Todas las conexiones deben utilizar direcciones MAC distintas.
- B) Mediante los números de puerto y las direcciones IP de los extremos.
- C) Utilizando una dirección IPv4 pública diferente para cada solicitud.
- D) Cambiando la máscara de subred para cada conexión.

---

## 12. Respuestas correctas

| N.º | Respuesta | Explicación |
|---|---|---|
| 1 | B | TCP proporciona entrega fiable; UDP no garantiza la entrega. |
| 2 | C | TCP utiliza ACK para confirmar la recepción de datos. |
| 3 | D | UDP tiene poca sobrecarga y resulta útil en aplicaciones sensibles a la latencia. |
| 4 | A | Los puertos permiten identificar aplicaciones y servicios. |
| 5 | B | HTTP tradicional utiliza normalmente TCP 80. |
| 6 | C | Los puertos registrados abarcan del 1024 al 49151. |
| 7 | A | Un socket se representa como dirección IP y puerto. |
| 8 | C | Un par de sockets identifica los dos extremos de la comunicación. |
| 9 | D | netstat permite consultar conexiones de red. |
| 10 | B | Las conexiones TCP se distinguen mediante las IP y los puertos de origen y destino. |
