
# Módulo 16: Servicios y Protocolos de Aplicación de Red

## 1. Relación Cliente-Servidor

El modelo **cliente-servidor** permite que los dispositivos soliciten y reciban servicios a través de una red.

- **Cliente:** dispositivo o aplicación que solicita un servicio.
- **Servidor:** dispositivo o aplicación que proporciona el servicio solicitado.

### ¿Cómo funciona?

1. El cliente solicita información al servidor.
2. El servidor recibe y procesa la solicitud.
3. El servidor envía una respuesta.
4. El cliente recibe y utiliza la información.

**Ejemplo:**

```text
Cliente (Chrome)                    Servidor Web
      |                                  |
      | -------- Solicitud HTTP -------> |
      |                                  |
      | <------- Respuesta HTTP -------- |
      |                                  |
      v                                  |
Muestra la página web
```

### Tipos de servidores

| Tipo | Función | Ejemplo de cliente |
|---|---|---|
| Servidor web | Proporciona páginas web y otros recursos. | Chrome, Firefox |
| Servidor de correo | Envía, recibe o almacena mensajes. | Outlook, Thunderbird |
| Servidor de archivos | Almacena y comparte archivos. | Explorador de Windows |

**Importante:** Una computadora puede ejecutar varios programas cliente al mismo tiempo.

---

## 2. URI, URL y URN

Los recursos de Internet necesitan identificadores para que las aplicaciones puedan localizarlos o referirse a ellos.

### 2.1 URI (Uniform Resource Identifier)

Es un identificador que permite reconocer un recurso.

Existen dos conceptos importantes:

| Concepto | Significado | Función |
|---|---|---|
| URI | Uniform Resource Identifier | Identifica un recurso. |
| URL | Uniform Resource Locator | Indica cómo localizar o acceder a un recurso. |
| URN | Uniform Resource Name | Identifica un recurso mediante un nombre persistente. |

**Recuerda:** Una URL es un tipo de URI.

### 2.2 Partes de una URL

Ejemplo:

`https://www.example.com/author/book.html#pagina155`

| Parte | Ejemplo | Función |
|---|---|---|
| Esquema | https | Indica cómo acceder al recurso. |
| Host | www.example.com | Identifica el servidor. |
| Ruta | /author/book.html | Ubicación del recurso. |
| Fragmento | #pagina155 | Identifica una sección del recurso. |

También existen URL que utilizan otros esquemas, como `ftp://` y `sftp://`.

---

## 3. Servicios de aplicación de red

Los protocolos de aplicación permiten ofrecer servicios como navegación web, transferencia de archivos, correo electrónico y acceso remoto.

### Protocolos importantes

| Protocolo | Función principal | Puerto habitual |
|---|---|---|
| DNS | Resuelve nombres de dominio a direcciones IP. | 53 TCP/UDP |
| HTTP | Permite solicitar y transferir recursos web. | 80 TCP |
| HTTPS | Permite comunicaciones HTTP protegidas mediante TLS. | 443 TCP; también UDP con HTTP/3 |
| FTP | Transfiere archivos entre cliente y servidor. | 21 TCP (control) |
| SSH | Proporciona acceso remoto seguro. | 22 TCP |
| Telnet | Proporciona acceso remoto sin cifrado. | 23 TCP |
| SMTP | Envía mensajes de correo electrónico. | 25 TCP; 587 para envío autenticado |
| POP3 | Permite descargar mensajes de correo. | 110 TCP |
| IMAP | Permite acceder y sincronizar el correo en el servidor. | 143 TCP |
| DHCP | Proporciona configuración IP automáticamente. | 67/68 UDP |

**Importante:** Algunos protocolos pueden utilizar puertos adicionales o versiones cifradas.

---

## 4. DNS: Sistema de Nombres de Dominio

DNS (Domain Name System) permite obtener la dirección IP asociada con un nombre de dominio.

Esto facilita la navegación porque los usuarios pueden escribir nombres en lugar de memorizar direcciones IP.

### Ejemplo

Cuando escribimos:

`www.cisco.com`

El dispositivo necesita descubrir una dirección IP para conectarse al servidor correspondiente.

### ¿Cómo funciona DNS?

1. El usuario introduce el nombre de dominio.
2. El cliente consulta al sistema de resolución DNS.
3. Si no existe una respuesta almacenada, se consulta un servidor DNS.
4. El servidor DNS obtiene o busca la información necesaria.
5. Devuelve la dirección IP correspondiente.
6. El cliente utiliza esa dirección para establecer la comunicación.

```text
PC                       Servidor DNS
 |                            |
 | --- ¿IP de ejemplo.com? -> |
 |                            |
 | <--- Dirección IP -------- |
 |                            |
 v
Conexión al servidor de destino
```

### 4.1 Dominios de nivel superior

Ejemplos:

| Dominio | Uso común |
|---|---|
| .com | Comercial y uso general |
| .edu | Instituciones educativas |
| .net | Redes y uso general |
| .org | Organizaciones |
| .pe | Dominio territorial de Perú |

### 4.2 Comando nslookup

Permite consultar información DNS.

**Windows y Linux:**

```bash
nslookup www.cisco.com
```

El resultado puede mostrar el servidor DNS utilizado y las direcciones IP obtenidas.

**Recuerda:** DNS no proporciona acceso a Internet por sí solo; permite resolver nombres para facilitar las conexiones.

---

## 5. Clientes y servidores web: HTTP y HTTPS

Cuando un navegador necesita acceder a una página web, envía solicitudes al servidor correspondiente.

### 5.1 HTTP

HTTP (Hypertext Transfer Protocol) permite intercambiar recursos web entre clientes y servidores.

- Puerto habitual: TCP 80.
- No cifra los datos por sí mismo.

### 5.2 HTTPS

HTTPS utiliza HTTP protegido mediante TLS.

- Puerto habitual: TCP 443.
- Cifra la comunicación.
- Ayuda a proteger la confidencialidad e integridad de los datos.
- Permite autenticar al servidor mediante certificados digitales.

| Característica | HTTP | HTTPS |
|---|---|---|
| Puerto habitual | 80 | 443 |
| Cifrado | No | Sí, mediante TLS |
| Dirección | http:// | https:// |
| Seguridad del transporte | Sin cifrado propio | Comunicación protegida |

### 5.3 ¿Qué es HTML?

HTML (HyperText Markup Language) es el lenguaje de marcado utilizado para estructurar el contenido de páginas web.

**Diferencia importante:**

- HTTP/HTTPS: protocolos para intercambiar recursos web.
- HTML: lenguaje utilizado para estructurar el contenido de una página.

**Recuerda:** HTTPS protege la conexión, pero no garantiza que el sitio web sea legítimo o que su contenido sea seguro.

---

## 6. FTP: Protocolo de Transferencia de Archivos

FTP (File Transfer Protocol) permite transferir archivos entre un cliente y un servidor.

Puede utilizarse para:
- Subir archivos.
- Descargar archivos.
- Consultar directorios.
- Renombrar o eliminar archivos, si el usuario tiene permisos.

### 6.1 Puertos de FTP

FTP utiliza conexiones separadas para control y transferencia de datos.

| Puerto | Función |
|---|---|
| TCP 21 | Conexión de control y comandos. |
| TCP 20 | Transferencia de datos en modo activo tradicional. |

**Importante:** En modo pasivo, FTP utiliza otros puertos para la conexión de datos.

### Ejemplo

```text
Cliente FTP                     Servidor FTP
     |                               |
     | ----- Control (21) --------> |
     |                               |
     | <---- Transferencia de datos |
     |                               |
```

FTP tradicional no cifra las credenciales ni los archivos durante la transmisión.

Para transferencias seguras pueden utilizarse alternativas como **SFTP** o **FTPS**.

---

## 7. Terminales virtuales: Telnet y SSH

Los protocolos de acceso remoto permiten administrar dispositivos desde otra computadora.

### 7.1 Telnet

Telnet proporciona acceso remoto mediante una terminal de texto.

- Utiliza TCP 23.
- Permite ejecutar comandos remotamente.
- No cifra la información transmitida.

**Problema:** Las contraseñas y comandos pueden ser interceptados y leídos.

### 7.2 SSH

SSH (Secure Shell) proporciona acceso remoto mediante comunicaciones cifradas.

- Utiliza TCP 22.
- Permite administrar routers, switches y servidores.
- Protege las credenciales y los datos transmitidos.

### Diferencias entre Telnet y SSH

| Característica | Telnet | SSH |
|---|---|---|
| Puerto | 23 TCP | 22 TCP |
| Cifrado | No | Sí |
| Acceso remoto | Sí | Sí |
| Recomendado para producción | No | Sí |

### Ejemplo Cisco

Para conectarse por SSH a un router:

```bash
ssh -l admin 192.168.1.1
```

Para conectarse mediante Telnet:

```bash
telnet 192.168.1.1
```

**Recuerda:** Siempre que sea posible, debemos utilizar SSH en lugar de Telnet.

---

## 8. Correo electrónico

El correo electrónico utiliza distintos protocolos para enviar y recibir mensajes.

### 8.1 SMTP

SMTP (Simple Mail Transfer Protocol) se utiliza para enviar correos electrónicos.

- TCP 25: habitualmente entre servidores de correo.
- TCP 587: habitualmente para el envío autenticado desde clientes.

### 8.2 POP3

POP3 (Post Office Protocol version 3) permite descargar mensajes desde un servidor de correo.

- Puerto habitual: TCP 110.
- Está orientado a la descarga de mensajes.
- Puede configurarse para mantener o eliminar copias en el servidor.

### 8.3 IMAP

IMAP (Internet Message Access Protocol) permite acceder a los mensajes almacenados en el servidor.

- Puerto habitual: TCP 143.
- Facilita la sincronización entre varios dispositivos.
- Normalmente conserva los mensajes en el servidor.

### Diferencias

| Protocolo | Función |
|---|---|
| SMTP | Enviar correos electrónicos. |
| POP3 | Descargar correos desde el servidor. |
| IMAP | Consultar y sincronizar correos almacenados en el servidor. |

### Ejemplo

```text
Usuario A
    |
    | SMTP
    v
Servidor de correo A
    |
    | SMTP
    v
Servidor de correo B
    |
    | IMAP o POP3
    v
Usuario B
```

### Puertos de correo importantes

| Protocolo | Puerto tradicional | Puerto cifrado habitual |
|---|---|---|
| SMTP | 25 | 465 (TLS implícito); 587 (STARTTLS habitual) |
| POP3 | 110 | 995 |
| IMAP | 143 | 993 |

**Recuerda:**
- SMTP envía.
- POP3 descarga.
- IMAP sincroniza.

---

## 9. Mensajería instantánea

La mensajería instantánea permite intercambiar mensajes mediante Internet, normalmente en tiempo real.

Ejemplos:
- WhatsApp.
- Microsoft Teams.
- Cisco Webex.
- Facebook Messenger.

Estas aplicaciones pueden incluir:
- Mensajes de texto.
- Envío de archivos.
- Imágenes y videos.
- Llamadas de voz y videollamadas.

**Importante:** Los protocolos y puertos utilizados dependen de cada aplicación.

---

## 10. Voz sobre IP (VoIP)

VoIP (Voice over Internet Protocol) permite transmitir conversaciones de voz a través de redes IP.

### ¿Cómo funciona?

1. El usuario habla mediante un micrófono.
2. El dispositivo convierte la voz en datos digitales.
3. Los datos se codifican y se transmiten mediante paquetes IP.
4. El receptor recibe los datos y reproduce el audio.

```text
Persona A                    Persona B
    |                            |
Micrófono                    Altavoz
    |                            ^
    v                            |
Datos digitales ---- Red IP ----> |
```

### Ventajas

- Permite llamadas mediante redes IP.
- Puede integrarse con aplicaciones de mensajería.
- Admite comunicación entre usuarios de diferentes ubicaciones.

### Conexión con teléfonos tradicionales

Para conectar una llamada VoIP con una red telefónica tradicional puede ser necesaria una puerta de enlace hacia la PSTN.

**PSTN:** Public Switched Telephone Network, o Red Pública de Telefonía Conmutada.

**Recuerda:** En aplicaciones VoIP, la latencia, la variación del retardo (jitter) y la pérdida de paquetes pueden afectar la calidad de la llamada.

---

## 11. Comandos importantes

| Comando | Función |
|---|---|
| `nslookup www.cisco.com` | Consultar direcciones IP mediante DNS. |
| `ping www.cisco.com` | Comprobar conectividad utilizando un nombre de dominio. |
| `ssh -l admin 192.168.1.1` | Conectarse remotamente mediante SSH en Cisco IOS. |
| `telnet 192.168.1.1` | Iniciar una conexión Telnet. |
| `netstat -an` | Consultar conexiones y puertos en formato numérico. |

**Nota sobre Packet Tracer:** Los verificadores de sintaxis pueden exigir comandos completos. Packet Tracer y equipos Cisco reales normalmente permiten ciertas abreviaciones válidas.

---

## 12. Puntos clave para el examen

- El cliente solicita servicios y el servidor responde.
- DNS permite resolver nombres de dominio a direcciones IP.
- `nslookup` permite realizar consultas DNS.
- URI identifica recursos; URL indica cómo localizarlos.
- HTTP utiliza normalmente TCP 80.
- HTTPS utiliza normalmente el puerto 443 y protege la comunicación mediante TLS.
- HTML estructura el contenido de las páginas web.
- FTP utiliza TCP 21 para control.
- FTP activo tradicional utiliza TCP 20 para datos.
- Telnet utiliza TCP 23 y no cifra la comunicación.
- SSH utiliza TCP 22 y proporciona acceso remoto seguro.
- SMTP permite enviar correo electrónico.
- POP3 permite descargar mensajes.
- IMAP facilita la sincronización del correo.
- VoIP permite transmitir voz mediante redes IP.
- La mensajería instantánea permite comunicarse en tiempo real.

---

## 13. Preguntas de repaso tipo Cisco

**1. ¿Cuál es la función principal de un servidor en el modelo cliente-servidor?**

- A) Solicitar siempre información a los clientes.
- B) Proporcionar servicios o recursos a los clientes.
- C) Asignar direcciones MAC a todos los dispositivos.
- D) Reemplazar al router de la red.

**2. ¿Qué protocolo permite resolver un nombre de dominio a una dirección IP?**

- A) DHCP
- B) SMTP
- C) DNS
- D) FTP

**3. ¿Qué comando se utiliza para consultar la dirección IP asociada a un nombre de dominio?**

- A) netstat
- B) nslookup
- C) traceroute
- D) show ip route

**4. ¿Cuál es la principal diferencia entre HTTP y HTTPS?**

- A) HTTP utiliza direcciones MAC y HTTPS utiliza direcciones IP.
- B) HTTPS utiliza cifrado para proteger la comunicación.
- C) HTTP funciona exclusivamente con IPv6.
- D) HTTPS no necesita un servidor web.

**5. ¿Qué puerto TCP se utiliza normalmente para establecer la conexión de control FTP?**

- A) 20
- B) 22
- C) 21
- D) 80

**6. ¿Por qué SSH es más seguro que Telnet?**

- A) Porque utiliza direcciones IP privadas.
- B) Porque evita la necesidad de contraseñas.
- C) Porque utiliza siempre UDP.
- D) Porque cifra los datos transmitidos.

**7. ¿Qué protocolo se utiliza principalmente para enviar mensajes de correo electrónico?**

- A) POP3
- B) SMTP
- C) IMAP
- D) DNS

**8. ¿Qué protocolo permite mantener y sincronizar los mensajes de correo almacenados en un servidor?**

- A) FTP
- B) POP3
- C) IMAP
- D) Telnet

**9. ¿Cuál es la función principal de una URL?**

- A) Identificar cómo localizar o acceder a un recurso.
- B) Asignar una dirección IP automáticamente.
- C) Cifrar los mensajes del usuario.
- D) Identificar la dirección MAC del servidor.

**10. ¿Qué tecnología permite transmitir llamadas de voz a través de redes IP?**

- A) ARP
- B) DNS
- C) FTP
- D) VoIP

---

## 14. Respuestas correctas

| N.º | Respuesta | Explicación |
|---|---|---|
| 1 | B | El servidor proporciona información o servicios solicitados por los clientes. |
| 2 | C | DNS permite obtener direcciones IP asociadas con nombres de dominio. |
| 3 | B | nslookup consulta información DNS. |
| 4 | B | HTTPS utiliza TLS para proteger la comunicación. |
| 5 | C | FTP utiliza TCP 21 para su conexión de control. |
| 6 | D | SSH protege los datos de la sesión mediante cifrado. |
| 7 | B | SMTP se utiliza para enviar correo electrónico. |
| 8 | C | IMAP permite acceder y sincronizar mensajes almacenados en el servidor. |
| 9 | A | Una URL indica cómo localizar o acceder a un recurso. |
| 10 | D | VoIP permite transmitir voz a través de redes IP. |
