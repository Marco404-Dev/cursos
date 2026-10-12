
# CISCO NETWORKING BASICS
## MÓDULO 2 — COMPONENTES, TIPOS Y CONEXIONES DE RED

**Objetivo:** Comprender las funciones de los clientes y servidores, las redes P2P, los componentes de una red y las diferentes formas de conectarse a Internet.

---

# 2.1 — CLIENTES Y SERVIDORES

## 2.1.2 — Roles de cliente y servidor

### ¿Qué es un host?

Un **host** es un dispositivo final conectado a una red que puede enviar o recibir información.

Ejemplos:
- Computadoras y laptops.
- Teléfonos inteligentes.
- Servidores.
- Impresoras de red.

Los hosts pueden funcionar como **clientes, servidores o ambos**, dependiendo del software que ejecuten.

### ¿Qué es un cliente?

Un **cliente** es un dispositivo o programa que solicita información o servicios a un servidor.

**Ejemplo:** cuando utilizas Google Chrome para ingresar a una página web, el navegador funciona como cliente.

### ¿Qué es un servidor?

Un **servidor** es un host que ejecuta software para proporcionar información, recursos o servicios a otros dispositivos.

**Ejemplo:** un servidor web almacena o genera contenido que los navegadores pueden solicitar.

### ¿Cómo funciona la comunicación cliente-servidor?

1. El cliente solicita un recurso.
2. La solicitud viaja por la red.
3. El servidor recibe y procesa la solicitud.
4. El servidor envía una respuesta.
5. El cliente recibe y muestra la información.

**Ejemplo:**

Cliente (Chrome) → Internet → Servidor web  
Cliente (Chrome) ← Respuesta ← Servidor web

### Tipos de servidores

| Tipo | Función | Ejemplo de cliente |
|---|---|---|
| Servidor web | Proporciona páginas y contenido web. | Google Chrome |
| Servidor de correo | Proporciona servicios de correo electrónico. | Microsoft Outlook |
| Servidor de archivos | Almacena y comparte archivos. | Explorador de archivos |

**IMPORTANTE:**
- Cliente = solicita servicios.
- Servidor = proporciona servicios.
- Host = dispositivo final que participa en la comunicación.
- Una misma computadora puede funcionar como cliente y servidor.

---

## 2.1.3 — Redes entre pares (P2P)

### ¿Qué es una red P2P?

**P2P (Peer-to-Peer)** significa red entre pares.

Es una red donde los dispositivos pueden compartir recursos directamente y funcionar como clientes y servidores según sea necesario.

No requiere un servidor dedicado para compartir esos recursos.

### ¿Cómo funciona?

Imagina dos computadoras conectadas a la misma red.

1. La PC1 comparte una carpeta.
2. La PC2 solicita acceder a esa carpeta.
3. La PC1 proporciona los archivos.
4. La PC2 también podría compartir una impresora con la PC1.

**Ejemplo:**

PC1 ↔ PC2

Ambas computadoras pueden proporcionar y solicitar recursos.

### Ventajas de las redes P2P

- **Fáciles de configurar:** requieren una configuración relativamente sencilla.
- **Menor costo:** no necesitan servidores dedicados.
- **Menor complejidad:** son adecuadas para redes pequeñas.
- **Recursos compartidos:** permiten intercambiar archivos y utilizar impresoras.

### Desventajas de las redes P2P

- **Administración descentralizada:** cada equipo administra sus recursos.
- **Menor seguridad centralizada:** resulta más difícil aplicar políticas uniformes.
- **Escalabilidad limitada:** se vuelven difíciles de administrar al aumentar los dispositivos.
- **Rendimiento:** una computadora puede volverse lenta si atiende solicitudes mientras realiza otras tareas.

### ¿Cuándo utilizar P2P?

Es útil para hogares y pequeñas oficinas donde pocos dispositivos necesitan compartir recursos.

En empresas grandes suelen utilizarse servidores dedicados para atender muchas solicitudes.

**IMPORTANTE:** P2P no significa que los dispositivos deban conectarse directamente con un solo cable. También pueden comunicarse mediante un switch o una red inalámbrica.

---

## 2.1.4 — Aplicaciones entre pares

### ¿Qué es una aplicación P2P?

Es una aplicación que permite que un dispositivo actúe como cliente y servidor dentro de una comunicación.

Cada participante puede solicitar y proporcionar recursos.

### ¿Cómo funciona?

1. Un dispositivo solicita un recurso.
2. Otro dispositivo que dispone del recurso responde.
3. Los dispositivos intercambian información.
4. Sus funciones pueden cambiar según la comunicación.

### Sistemas P2P híbridos

Algunas aplicaciones utilizan un **servidor central de índices** para localizar recursos.

**Funcionamiento:**

1. Una computadora consulta al servidor de índices.
2. El servidor indica dónde se encuentra el recurso.
3. La computadora se comunica con el dispositivo que posee el recurso.
4. Los datos se transfieren entre los participantes.

**DIFERENCIA IMPORTANTE:**

- Red P2P = forma de organizar el intercambio de recursos entre equipos.
- Aplicación P2P = programa que utiliza funciones de cliente y servidor entre participantes.

---

## 2.1.5 — Múltiples roles en la red

Una computadora puede ejecutar varios tipos de software de cliente y servidor simultáneamente.

### Como servidor

Una sola computadora puede proporcionar:
- Archivos.
- Páginas web.
- Correo electrónico.

### Como cliente

Una computadora puede:
- Consultar páginas web.
- Revisar el correo electrónico.
- Enviar mensajes.
- Reproducir contenido de Internet.

**Ejemplo:** mientras utilizas Chrome para navegar, también puedes consultar el correo electrónico y compartir una carpeta de tu computadora.

**IDEA CLAVE:** el software determina el rol que desempeña un host en una comunicación.

---

# 2.2 — COMPONENTES DE LA RED

## 2.2.2 — Infraestructura de red

### ¿Qué es la infraestructura de red?

La **infraestructura de red** es el conjunto de componentes que permiten conectar dispositivos y transmitir información.

Cisco clasifica sus componentes de hardware en tres categorías:

1. **Dispositivos finales.**
2. **Dispositivos intermedios.**
3. **Medios de red.**

### 1. Dispositivos finales

Son los dispositivos que originan o reciben mensajes.

Ejemplos:
- Computadoras.
- Servidores.
- Impresoras de red.
- Smartphones.
- Cámaras de seguridad.

### 2. Dispositivos intermedios

Son equipos que permiten conectar dispositivos y transportar información entre ellos.

Ejemplos:
- Switch.
- Router.
- Punto de acceso inalámbrico.

**Funciones principales:**

- Switch: conecta dispositivos dentro de una LAN y reenvía tramas.
- Router: conecta diferentes redes y encamina paquetes.
- Punto de acceso (AP): permite conectar dispositivos inalámbricos a una red.

### 3. Medios de red

Son los canales utilizados para transportar las señales.

Ejemplos:
- Cable de cobre.
- Fibra óptica.
- Conexiones inalámbricas.

### Diferencias fundamentales

| Categoría | Función | Ejemplo |
|---|---|---|
| Dispositivo final | Envía o recibe información. | Laptop |
| Dispositivo intermedio | Conecta equipos o redes. | Router |
| Medio de red | Transporta señales. | Cable Ethernet |

**PARA RECORDAR:**

- Host = origen o destino de los datos.
- Router = conecta redes.
- Switch = conecta dispositivos de una LAN.
- Medio = transporta señales.

---

## 2.2.3 — Dispositivos finales

### ¿Qué son?

Los **dispositivos finales o hosts** son equipos que funcionan como origen o destino de los mensajes transmitidos por una red.

Ejemplos:
- PC y laptops.
- Servidores web y de archivos.
- Impresoras.
- Teléfonos.
- Cámaras de seguridad.
- Tablets.
- Lectores de códigos de barras.

### ¿Cómo se identifica un host?

Los hosts utilizan direcciones para poder comunicarse.

**Ejemplo:**

1. La PC1 quiere comunicarse con la PC2.
2. La PC1 identifica la dirección de destino.
3. El mensaje se transmite por la red.
4. La PC2 recibe la información.

**IMPORTANTE:** los hosts son los dispositivos finales, mientras que los equipos intermedios ayudan a transportar los datos hasta su destino.

---

# 2.3 — CONEXIONES A INTERNET

## 2.3.1 — Servicios del ISP

### ¿Qué es un ISP?

**ISP (Internet Service Provider)** significa Proveedor de Servicios de Internet.

Es una empresa que proporciona conectividad a Internet.

Ejemplos de ISP:
- Movistar.
- Claro.
- Otros proveedores de servicios de Internet.

### ¿Qué servicios puede ofrecer?

- Acceso a Internet.
- Correo electrónico.
- Alojamiento de sitios web.
- Almacenamiento en red.
- Copias de seguridad.
- Servicios de seguridad.

### ¿Cómo funciona un ISP?

1. Tu dispositivo se conecta a la red doméstica.
2. El router permite acceder a la conexión del ISP.
3. El ISP transporta el tráfico hacia otras redes.
4. Los paquetes llegan a su destino mediante redes interconectadas.

**Ejemplo:**

Laptop → Router → ISP → Internet → Servidor web

### ¿Qué es la red troncal de Internet?

La **red troncal o backbone** es el conjunto de enlaces y equipos de alta capacidad que conectan importantes redes y proveedores de Internet.

Utiliza principalmente:
- Fibra óptica de alta capacidad.
- Routers de gran rendimiento.
- Enlaces terrestres y submarinos.

**IMPORTANTE:** los ISP se interconectan para permitir comunicaciones entre usuarios y servicios de distintas redes.

---

## 2.3.2 — Conexiones de ISP

### ¿Cómo se conecta una casa a Internet?

Una conexión doméstica habitual utiliza un router integrado.

Este equipo puede incorporar:
- Router.
- Switch Ethernet.
- Punto de acceso inalámbrico (AP).
- Funciones de seguridad.
- Asignación automática de direcciones IP.

### Funcionamiento

1. El ISP proporciona el acceso a Internet.
2. El módem u ONT, según la tecnología, termina la conexión del proveedor.
3. El router conecta la red doméstica con el ISP.
4. Las computadoras pueden conectarse por Ethernet.
5. Los celulares pueden conectarse mediante Wi-Fi.

**Ejemplo:**

Internet / ISP → Módem u ONT → Router → PC y celulares

En algunos hogares, varias de estas funciones están integradas en un único equipo.

### ¿Por qué se utiliza un router?

Porque permite compartir una conexión entre múltiples dispositivos y normalmente incorpora funciones de seguridad para la red local.

**IMPORTANTE:** conectar una computadora directamente al módem, sin protecciones adecuadas, puede exponerla a mayores riesgos.

---

## 2.3.3 — Conexiones de cable y DSL

### 1. Internet por cable

Utiliza infraestructura de televisión por cable, generalmente cable coaxial.

**¿Cómo funciona?**

1. Los datos llegan mediante la red del proveedor.
2. Un módem por cable procesa las señales de comunicación.
3. Proporciona conexión Ethernet al router o a un equipo.
4. Los dispositivos acceden a Internet.

**Características:**
- Conexión permanente.
- Puede ofrecer un ancho de banda elevado.
- Utiliza un módem por cable.

### 2. DSL (Digital Subscriber Line)

**DSL significa Línea de Suscriptor Digital.**

Permite transmitir datos por líneas telefónicas de cobre.

**¿Cómo funciona?**

1. La señal llega mediante una línea telefónica.
2. Un módem DSL procesa los datos.
3. Se separan las comunicaciones de voz y datos mediante tecnologías compatibles.
4. El usuario accede a Internet mientras la línea puede mantener el servicio telefónico.

En el ejemplo de Cisco, se describen canales separados para voz, descarga y subida.

**Características:**
- Utiliza infraestructura telefónica.
- Ofrece conexión permanente.
- La velocidad puede depender de la calidad y longitud de la línea.
- Algunas modalidades tienen mayor velocidad de descarga que de subida.

### Diferencia entre cable y DSL

| Característica | Cable | DSL |
|---|---|---|
| Medio de acceso | Coaxial | Línea telefónica de cobre |
| Equipo | Módem por cable | Módem DSL |
| Conexión permanente | Sí | Sí |
| Factor importante | Capacidad y condiciones de la red | Calidad y distancia de la línea |

---

## 2.3.4 — Opciones de conectividad adicionales

### 1. Red celular

Utiliza redes de telefonía móvil para proporcionar acceso a Internet.

**¿Cómo funciona?**

1. El celular se comunica con una estación base.
2. La red del operador transporta los datos.
3. El operador proporciona acceso a Internet.

**Ventajas:**
- Permite movilidad.
- Útil donde no existe conexión fija.

**Desventajas:**
- Depende de la cobertura.
- El rendimiento puede variar.
- Algunos planes tienen límites de datos o cobros adicionales.

### 2. Internet satelital

Utiliza satélites para proporcionar conectividad a Internet.

**¿Cómo funciona?**

1. La antena del usuario se comunica mediante señales de radio.
2. El satélite participa en el enlace de comunicación.
3. La información llega a la infraestructura del proveedor.
4. Se establece la comunicación con Internet.

**Ventajas:**
- Puede utilizarse en zonas rurales o alejadas.
- Útil cuando no hay otras conexiones disponibles.

**Desventajas:**
- Puede requerir equipos e instalación costosos.
- La señal puede verse afectada por obstáculos y condiciones ambientales.
- La velocidad y latencia dependen del sistema contratado.

### 3. Acceso telefónico por marcación (Dial-up)

Es una tecnología que utiliza una línea telefónica y un módem para conectarse al ISP.

**¿Cómo funciona?**

1. El módem llama a un número de acceso del ISP.
2. Se establece una conexión mediante la línea telefónica.
3. Se intercambian datos a una velocidad limitada.

**Desventajas:**
- Ancho de banda muy bajo.
- No es adecuado para aplicaciones modernas exigentes.
- Es una tecnología antigua, utilizada cuando no hay mejores alternativas.

### Comparación de conexiones

| Tecnología | Medio utilizado | Característica principal |
|---|---|---|
| Cable | Cable coaxial | Acceso fijo de banda ancha |
| DSL | Línea telefónica | Acceso mediante cobre telefónico |
| Red celular | Ondas de radio | Movilidad |
| Satelital | Enlace satelital | Cobertura en zonas alejadas |
| Dial-up | Línea telefónica | Velocidad muy limitada |
| Fibra óptica | Pulsos de luz | Alta capacidad de transmisión |

---

# GLOSARIO — MÓDULO 2

| Término | Significado |
|---|---|
| Host | Dispositivo final que participa en una red. |
| Cliente | Solicita servicios o recursos. |
| Servidor | Proporciona servicios o recursos. |
| P2P | Red o aplicación entre pares. |
| LAN | Red de área local. |
| Router | Equipo que conecta diferentes redes. |
| Switch | Equipo que conecta dispositivos dentro de una LAN. |
| AP | Punto de acceso inalámbrico. |
| ISP | Proveedor de Servicios de Internet. |
| Backbone | Red troncal de alta capacidad. |
| DSL | Línea de Suscriptor Digital. |
| Módem | Equipo que adapta señales para una tecnología de acceso. |
| ONT | Terminal de red óptica utilizada en determinadas conexiones de fibra. |
| Ethernet | Tecnología común de redes cableadas. |
| Medio de red | Canal por el que se transmiten señales. |
| Dial-up | Acceso telefónico por marcación. |

---

# RESUMEN GENERAL — MÓDULO 2

1. **Los hosts** son dispositivos finales que envían y reciben información.
2. **Los clientes** solicitan servicios y **los servidores** los proporcionan.
3. Las **redes P2P** permiten compartir recursos entre computadoras sin servidores dedicados.
4. Una computadora puede desempeñar múltiples funciones de cliente y servidor.
5. La infraestructura de red contiene **dispositivos finales, dispositivos intermedios y medios de red**.
6. Los dispositivos finales originan o reciben mensajes.
7. Los routers conectan redes y los switches conectan dispositivos dentro de una LAN.
8. Los **ISP** proporcionan conectividad a Internet y se interconectan con otros proveedores.
9. La red troncal utiliza enlaces de alta capacidad, principalmente de fibra óptica.
10. Las conexiones a Internet pueden utilizar cable, DSL, red celular, satélites, fibra óptica o acceso telefónico.

**IDEA CLAVE:** una red necesita dispositivos que intercambien información, equipos que faciliten la comunicación y medios que transporten las señales.

---

# CUESTIONARIO — MÓDULO 2

**Total:** 10 preguntas  
**Puntaje máximo:** 10 puntos  
**Instrucciones:** Selecciona la respuesta correcta. En las preguntas indicadas, elige varias opciones.

## PREGUNTA 1

¿Qué función cumple un cliente dentro de una red?

- [ ] A. Proporcionar exclusivamente servicios a otros hosts.
- [ ] B. Solicitar información o servicios a un servidor.
- [ ] C. Transportar señales mediante cables.
- [ ] D. Conectar diferentes redes.

## PREGUNTA 2

¿Cuáles son las tres categorías principales de componentes de hardware de una infraestructura de red? (Selecciona tres).

- [ ] A. Dispositivos finales.
- [ ] B. Dispositivos intermedios.
- [ ] C. Medios de red.
- [ ] D. Aplicaciones de usuario.

## PREGUNTA 3

¿Qué característica describe una red P2P?

- [ ] A. Necesita un servidor dedicado para cada servicio.
- [ ] B. Solo permite conectar una computadora.
- [ ] C. Los equipos pueden actuar como clientes y servidores.
- [ ] D. No permite compartir archivos.

## PREGUNTA 4

¿Qué equipo conecta diferentes redes y encamina paquetes entre ellas?

- [ ] A. Router.
- [ ] B. Impresora.
- [ ] C. Monitor.
- [ ] D. Cámara IP.

## PREGUNTA 5

¿Cuál de los siguientes elementos es un medio de red?

- [ ] A. Servidor web.
- [ ] B. Router inalámbrico.
- [ ] C. Cable de fibra óptica.
- [ ] D. Computadora portátil.

## PREGUNTA 6

¿Qué significa ISP?

- [ ] A. Internet Security Protocol.
- [ ] B. Internet Service Provider.
- [ ] C. Internal Server Program.
- [ ] D. Internet Switching Process.

## PREGUNTA 7

¿Qué tecnología proporciona conectividad a Internet mediante líneas telefónicas de cobre, manteniendo una conexión permanente?

- [ ] A. DSL.
- [ ] B. Wi-Fi.
- [ ] C. Ethernet.
- [ ] D. RFID.

## PREGUNTA 8

¿Cuáles de las siguientes opciones son tecnologías de acceso a Internet descritas por Cisco? (Selecciona tres).

- [ ] A. Red celular.
- [ ] B. Internet satelital.
- [ ] C. Acceso telefónico por marcación.
- [ ] D. Conexión HDMI.

## PREGUNTA 9

En una red P2P, una computadora puede compartir archivos mientras solicita otros servicios de red.

- [ ] A. Verdadero.
- [ ] B. Falso.

## PREGUNTA 10

Un router doméstico integrado puede incluir funciones de switch y punto de acceso inalámbrico.

- [ ] A. Verdadero.
- [ ] B. Falso.

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

# SOLUCIONARIO

**1. B — Solicitar información o servicios.**  
El cliente realiza solicitudes y el servidor proporciona respuestas o recursos.

**2. A, B y C — Dispositivos finales, dispositivos intermedios y medios.**  
Son las tres categorías principales de infraestructura de red descritas por Cisco.

**3. C — Los equipos pueden actuar como clientes y servidores.**  
Las redes P2P permiten compartir recursos directamente entre dispositivos.

**4. A — Router.**  
El router conecta redes y encamina paquetes hacia otras redes.

**5. C — Cable de fibra óptica.**  
Es un medio utilizado para transmitir señales mediante luz.

**6. B — Internet Service Provider.**  
Es una empresa que proporciona servicios de conectividad a Internet.

**7. A — DSL.**  
Utiliza líneas telefónicas de cobre para proporcionar conectividad de datos.

**8. A, B y C — Red celular, satélite y dial-up.**  
Son opciones de acceso a Internet; HDMI es una interfaz audiovisual.

**9. A — Verdadero.**  
En una red P2P, un host puede solicitar y proporcionar recursos.

**10. A — Verdadero.**  
Muchos routers domésticos integran un switch Ethernet y un punto de acceso Wi-Fi.

---

**PUNTAJE FINAL: ____ / 10**

## CONCEPTOS QUE DEBES DOMINAR ANTES DEL MÓDULO 3

- Diferencia entre cliente y servidor.
- Funcionamiento de una red P2P.
- Ventajas y desventajas del modelo P2P.
- Dispositivos finales, intermedios y medios de red.
- Diferencia entre router, switch y punto de acceso.
- Función de un ISP.
- Funcionamiento básico de cable, DSL, celular y satélite.
- Diferencia entre conexión fija e inalámbrica.







#######################################################################################


# CISCO NETWORKING BASICS — MÓDULO 2
## SIMULACRO DE REFUERZO

**Instrucciones:** 10 preguntas. Selecciona la respuesta correcta. La pregunta 2 tiene dos respuestas.

### Pregunta 1
Una familia tiene un módem y desea conectar tres laptops y varios celulares. ¿Qué equipo debería instalar?
- [ ] A. Switch sin funciones inalámbricas
- [ ] B. Router inalámbrico integrado
- [ ] C. Servidor de archivos
- [ ] D. Computadora de escritorio

### Pregunta 2
¿Cuáles son dispositivos finales? (Elige dos)
- [ ] A. Computadora portátil
- [ ] B. Router
- [ ] C. Impresora de red
- [ ] D. Switch

### Pregunta 3
¿Qué tecnología proporciona Internet mediante la infraestructura de televisión por cable coaxial?
- [ ] A. DSL
- [ ] B. Red celular
- [ ] C. Internet por cable
- [ ] D. Dial-up

### Pregunta 4
¿Qué conexión utiliza líneas telefónicas de cobre para proporcionar banda ancha sin marcación por llamada?
- [ ] A. DSL
- [ ] B. Dial-up
- [ ] C. Satélite
- [ ] D. Red celular

### Pregunta 5
¿Qué conexión es adecuada para una tableta en movimiento con cobertura 4G/5G?
- [ ] A. Acceso telefónico
- [ ] B. Cable coaxial
- [ ] C. Fibra Ethernet local
- [ ] D. Datos móviles

### Pregunta 6
¿Qué conexión puede servir a una estación aislada sin redes terrestres?
- [ ] A. DSL
- [ ] B. Acceso por satélite
- [ ] C. Cable módem
- [ ] D. Dial-up

### Pregunta 7
¿Qué modelo permite compartir una carpeta directamente entre PC sin servidor dedicado?
- [ ] A. P2P
- [ ] B. Servidor dedicado
- [ ] C. Red troncal ISP
- [ ] D. Acceso DSL

### Pregunta 8
¿Cuál es la función principal de un servidor?
- [ ] A. Transportar señales por cobre
- [ ] B. Proporcionar archivos solicitados por otros hosts
- [ ] C. Conectar cables físicamente
- [ ] D. Emitir ondas de radio como medio

### Pregunta 9
Un switch que conecta PC dentro de una LAN es un dispositivo intermedio.
- [ ] A. Verdadero
- [ ] B. Falso

### Pregunta 10
Una impresora conectada a una PC y compartida con otras requiere obligatoriamente un servidor dedicado independiente.
- [ ] A. Verdadero
- [ ] B. Falso

---
## SOLUCIONARIO
1. B — Router inalámbrico integrado.
2. A y C — Laptop e impresora de red.
3. C — Internet por cable.
4. A — DSL.
5. D — Datos móviles.
6. B — Acceso satelital.
7. A — P2P.
8. B — Proporcionar archivos y servicios.
9. A — Verdadero.
10. B — Falso.

**PUNTAJE: ____ / 10**
