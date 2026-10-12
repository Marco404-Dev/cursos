
# CISCO NETWORKING BASICS
## MÓDULO 4 — CREAR UNA RED DOMÉSTICA

**Objetivo:** Comprender los componentes de una red doméstica, las tecnologías cableadas e inalámbricas, los estándares Wi-Fi y la configuración básica de un router.

---

# 4.1 — CONCEPTOS BÁSICOS DE REDES DOMÉSTICAS

## 4.1.1 — ¿Qué es una red doméstica?

Una **red doméstica** es una red de área local (LAN) que conecta diferentes dispositivos dentro de una vivienda para compartir información, recursos y acceso a Internet.

### ¿Cómo funciona?

1. El proveedor de servicios de Internet (ISP) proporciona conectividad.
2. El router doméstico conecta la red local con la red del proveedor.
3. Los dispositivos domésticos se conectan al router mediante cables Ethernet o Wi-Fi.
4. Los equipos pueden intercambiar información dentro de la LAN y acceder a Internet.

**Ejemplo:**

Internet / ISP
       |
   Router doméstico
       |
       +-- PC (Ethernet)
       +-- Laptop (Wi-Fi)
       +-- Celular (Wi-Fi)
       +-- Smart TV (Wi-Fi)

### Ventajas de las redes WLAN

**WLAN (Wireless Local Area Network)** significa Red de Área Local Inalámbrica.

Las ventajas de las WLAN incluyen:

- Movilidad.
- Flexibilidad.
- Escalabilidad.
- Menores costos de instalación en ciertos escenarios.
- Instalación rápida.
- Posibilidad de conectarse sin cableado físico hasta cada dispositivo.

**IMPORTANTE:** Wi-Fi permite acceder a una LAN inalámbrica, pero no garantiza por sí solo acceso a Internet.

---

## 4.1.2 — Componentes de una red doméstica

Los dispositivos que pueden formar parte de una red doméstica incluyen:

- Computadoras de escritorio.
- Laptops.
- Smartphones.
- Consolas de videojuegos.
- Televisores inteligentes.
- Impresoras y escáneres.
- Cámaras de seguridad.
- Dispositivos de control del clima.

Muchos dispositivos del hogar pueden utilizar una misma red para intercambiar información o recibir instrucciones.

**Ejemplo:** puedes controlar un dispositivo de climatización compatible mediante una aplicación conectada a la red.

---

## 4.1.3 — Enrutadores de red domésticos típicos

### ¿Qué es un router doméstico integrado?

Es un equipo que puede incorporar distintas funciones de red en un solo dispositivo:

- Router.
- Switch Ethernet.
- Punto de acceso inalámbrico (AP).
- Funciones básicas de seguridad.
- Servidor DHCP.

### Tipos principales de puertos

**1. Puertos Ethernet o LAN**

Permiten conectar dispositivos de la red local mediante cables Ethernet.

Ejemplos:
- Computadoras.
- Consolas.
- Impresoras.

Los dispositivos conectados a los puertos LAN suelen pertenecer a la misma red local en la configuración doméstica predeterminada.

**2. Puerto Internet o WAN**

Permite conectar el router a otra red, normalmente a la infraestructura del proveedor de Internet.

Ejemplo:

Módem del ISP → Puerto WAN del router.

### Diferencia entre LAN y WAN

| LAN | WAN |
|---|---|
| Red de área local. | Red de área amplia. |
| Conecta dispositivos de la vivienda. | Interconecta redes a mayor escala. |
| Utiliza puertos LAN del router. | Utiliza normalmente el puerto WAN/Internet. |

**PARA RECORDAR:**

- LAN = red interna.
- WAN = conexión hacia otra red.
- Puerto LAN = conectar dispositivos locales.
- Puerto Internet = conectar el router con la red del proveedor.

**IMPORTANTE:** en la configuración predeterminada de muchos routers domésticos, los dispositivos conectados por Ethernet y Wi-Fi pertenecen a la misma LAN.

---

# 4.2 — TECNOLOGÍAS DE RED EN EL HOGAR

## 4.2.1 — Frecuencias inalámbricas LAN

Las tecnologías inalámbricas utilizan ondas electromagnéticas para transportar información.

Las redes Wi-Fi domésticas descritas en este módulo utilizan principalmente dos bandas:

- **2.4 GHz.**
- **5 GHz.**

### ¿Qué significa GHz?

**GHz (gigahercios)** es una unidad de frecuencia.

1 GHz equivale a mil millones de ciclos por segundo.

### Wi-Fi de 2.4 GHz

En condiciones habituales puede ofrecer:

- Mayor alcance que 5 GHz.
- Mejor propagación a través de obstáculos.
- Compatibilidad con numerosos dispositivos.

Puede sufrir interferencias por la presencia de otros equipos que usan frecuencias cercanas.

### Wi-Fi de 5 GHz

En condiciones habituales puede ofrecer:

- Mayor capacidad para velocidades elevadas.
- Más opciones de canales.
- Menor alcance que 2.4 GHz en circunstancias comparables.

### Comparación

| Característica | 2.4 GHz | 5 GHz |
|---|---|---|
| Alcance habitual | Mayor | Menor |
| Propagación por paredes | Generalmente mejor | Generalmente menor |
| Velocidad potencial | Depende del estándar | Puede ser mayor |
| Interferencias | Frecuentes | Dependen del entorno |

**IMPORTANTE:** la velocidad no depende únicamente de la frecuencia. También influyen el estándar Wi-Fi, el ancho del canal, las interferencias y la capacidad del equipo.

### ¿Qué relación tiene Bluetooth?

Bluetooth también utiliza la banda de 2.4 GHz.

Está diseñado principalmente para comunicaciones de corto alcance y bajo consumo energético.

**Ejemplo:**
- Wi-Fi → conectar una laptop a la red doméstica.
- Bluetooth → conectar un mouse o unos auriculares.

---

## 4.2.2 — Tecnologías para redes cableadas

Aunque Wi-Fi ofrece movilidad, las conexiones cableadas siguen siendo útiles cuando se necesita una conexión estable.

### ¿Qué es Ethernet?

**Ethernet** es una tecnología de red utilizada para comunicar dispositivos dentro de una LAN.

Puede funcionar mediante distintos medios físicos, incluidos cables de cobre y fibra óptica.

### 1. Cable UTP

**UTP (Unshielded Twisted Pair)** significa par trenzado no blindado.

Contiene pares de conductores trenzados que ayudan a reducir las interferencias eléctricas.

**Ejemplo:** cable Ethernet que conecta una computadora con un switch.

### 2. Cable categoría 5e (Cat 5e)

Es un tipo de cable de par trenzado utilizado en redes Ethernet.

Características:
- Contiene cuatro pares de hilos trenzados.
- Ayuda a reducir interferencias.
- Se utiliza en instalaciones de redes LAN.

### 3. Conector RJ-45

En redes Ethernet de cobre se utiliza comúnmente un conector modular de ocho posiciones, conocido habitualmente como RJ-45.

**Ejemplo:** conector del cable que conectas al puerto Ethernet de una laptop.

### 4. Cable coaxial

Está formado por:

- Conductor central.
- Material aislante.
- Blindaje conductor.
- Cubierta exterior.

Se utiliza, entre otras aplicaciones, en redes de televisión por cable.

### 5. Fibra óptica

Es un medio de transmisión que utiliza pulsos de luz para transportar datos.

Características:
- Alta capacidad de transmisión.
- Adecuada para largas distancias.
- No sufre interferencias electromagnéticas como los cables de cobre.

### Comparación de medios

| Medio | Tipo de señal | Ejemplo |
|---|---|---|
| UTP | Eléctrica | PC conectada a un switch |
| Coaxial | Eléctrica | Internet por cable |
| Fibra óptica | Óptica | Enlaces de alta capacidad |
| Wi-Fi | Radio | Celular conectado al router |

**PARA RECORDAR:**

- UTP = pares de cobre trenzados.
- Cat 5e = categoría de cable.
- RJ-45 = nombre común del conector Ethernet.
- Fibra óptica = pulsos de luz.
- Ethernet = tecnología de comunicación de redes cableadas.

---

# 4.3 — ESTÁNDARES INALÁMBRICOS

## 4.3.1 — Redes Wi-Fi

### ¿Qué es IEEE?

**IEEE (Institute of Electrical and Electronics Engineers)** es una organización que desarrolla estándares técnicos, incluidos los utilizados en redes.

### ¿Qué es IEEE 802.11?

**IEEE 802.11** es la familia de estándares utilizada para las redes de área local inalámbricas (WLAN).

Estos estándares definen aspectos de las comunicaciones inalámbricas, como las características de transmisión y el funcionamiento de los dispositivos.

### ¿Qué es Wi-Fi Alliance?

La **Wi-Fi Alliance** es una organización que realiza programas de certificación e interoperabilidad para dispositivos Wi-Fi.

### Estándares mencionados en el módulo

| Estándar | Bandas utilizadas |
|---|---|
| 802.11b | 2.4 GHz |
| 802.11g | 2.4 GHz |
| 802.11n | 2.4 y 5 GHz |
| 802.11ac | 5 GHz |

**IMPORTANTE:** IEEE 802.11 define estándares técnicos y Wi-Fi Alliance se encarga de programas de certificación de productos.

---

## 4.3.2 — Configuración inalámbrica

Los routers inalámbricos disponen de distintas opciones para configurar la WLAN.

### 1. Modo de red

Determina qué estándares inalámbricos admite el router.

Ejemplos:
- 802.11b.
- 802.11g.
- 802.11n.
- Modo mixto.

### ¿Qué es el modo mixto?

El **modo mixto (Mixed Mode)** permite la conexión de dispositivos compatibles con diferentes estándares Wi-Fi.

**Ejemplo:**

Un router permite conectar una laptop antigua y un celular moderno mediante estándares compatibles.

**IMPORTANTE:** si el router solo admite un estándar determinado, un dispositivo incompatible con ese estándar no podrá conectarse mediante él.

### 2. SSID — Nombre de la red

**SSID (Service Set Identifier)** es el identificador utilizado para reconocer una red WLAN.

Características:
- Puede contener hasta 32 bytes.
- Distingue entre mayúsculas y minúsculas.
- Permite identificar la red inalámbrica.

**Ejemplo:**

CASA_WIFI

No es lo mismo que:

casa_wifi

### 3. Canal inalámbrico

Especifica el canal de radiofrecuencia utilizado para la comunicación inalámbrica.

El router puede configurarse para seleccionar automáticamente un canal.

**Ejemplo:** cuando hay muchas redes cercanas, elegir un canal adecuado puede ayudar a reducir interferencias.

### 4. Difusión del SSID

Determina si el router anuncia el nombre de la red para facilitar que los dispositivos la detecten.

**Activado:**
- Los dispositivos pueden encontrar la red en su lista de redes disponibles.

**Desactivado:**
- Normalmente será necesario introducir manualmente el SSID.

**IMPORTANTE:** ocultar el SSID no garantiza la seguridad de la red.

### ¿Cómo proteger la WLAN?

Cisco recomienda utilizar mecanismos sólidos de cifrado y autenticación.

**Ejemplo:** configurar WPA2 o WPA3 cuando los dispositivos lo admitan.

### Resumen de configuración

| Parámetro | Función |
|---|---|
| Modo de red | Selecciona los estándares Wi-Fi admitidos. |
| SSID | Identifica la red inalámbrica. |
| Canal | Define el canal de comunicación. |
| Difusión SSID | Permite anunciar el nombre de la red. |
| Seguridad | Protege el acceso inalámbrico. |

---

# 4.4 — CONFIGURAR UN ENRUTADOR DOMÉSTICO

## 4.4.1 — Configuración inicial

### ¿Cómo comenzar?

Para configurar un router doméstico, Cisco presenta un procedimiento utilizando una computadora conectada por cable Ethernet.

### Paso 1 — Conectar la computadora

1. Conecta un cable Ethernet al puerto de red de la computadora.
2. Conecta el otro extremo a un puerto LAN del router.
3. Comprueba las luces de enlace.

**IMPORTANTE:** para configurar la red local por cable, conecta la computadora a un puerto LAN y no al puerto Internet/WAN.

### Paso 2 — Obtener una dirección IP

La computadora necesita una configuración IP para comunicarse con el router.

Muchos routers domésticos incluyen un servidor DHCP que proporciona automáticamente:

- Dirección IP.
- Máscara de subred.
- Puerta de enlace predeterminada.
- Servidores DNS.

### ¿Qué es DHCP?

**DHCP (Dynamic Host Configuration Protocol)** es un protocolo que permite asignar automáticamente parámetros de configuración IP a los dispositivos.

**Ejemplo:**

Router: 192.168.1.1

PC: 192.168.1.100

Máscara: 255.255.255.0

Gateway: 192.168.1.1

Estos valores son únicamente un ejemplo de configuración.

### Paso 3 — Acceder a la configuración

Normalmente se utiliza una interfaz de administración proporcionada por el fabricante.

Puede accederse mediante:
- Navegador web.
- Aplicación de administración.
- Herramienta de configuración compatible.

### Paso 4 — Configurar la red inalámbrica

Establecer:
- Nombre de la red (SSID).
- Modo inalámbrico.
- Seguridad.
- Contraseña.
- Canal inalámbrico.

### Paso 5 — Comprobar la conectividad

1. Conectar un dispositivo a la red.
2. Verificar que reciba una configuración IP.
3. Comprobar la comunicación con el router.
4. Verificar el acceso a Internet si está disponible.

**IMPORTANTE:** en Packet Tracer puedes practicar la configuración básica del router doméstico mediante su interfaz gráfica.

---

## 4.4.2 — Consideraciones de diseño

Antes de configurar una red doméstica, es importante planificar su funcionamiento y seguridad.

### 1. ¿Cómo se llamará la red?

El SSID debe permitir identificar la WLAN sin revelar innecesariamente información sobre los dispositivos utilizados.

**Ejemplo recomendado:**

RED_CASA

No es recomendable incluir la marca y el modelo exacto del router si esto revela información técnica innecesaria.

### 2. ¿Qué dispositivos se conectarán?

Debes verificar la compatibilidad con los estándares Wi-Fi utilizados.

**Ejemplo:**

Una laptop antigua puede necesitar un modo de compatibilidad para conectarse a un router moderno.

### 3. ¿Qué es el modo heredado?

El **modo heredado (Legacy Mode)** permite admitir determinados estándares inalámbricos antiguos.

Algunos fabricantes utilizan el término **modo mixto** para configuraciones compatibles con varias generaciones.

### 4. ¿Qué es una red de invitados?

Una **red de invitados (Guest Network)** es una red inalámbrica separada o restringida para proporcionar acceso a visitantes.

Puede configurarse para:
- Permitir acceso a Internet.
- Restringir el acceso a dispositivos internos.
- Utilizar un SSID diferente.

**Ejemplo:**

Red principal: CASA_PRIVADA

Red de invitados: CASA_VISITAS

### 5. Seguridad de la red doméstica

Buenas prácticas:

- Configurar una contraseña segura para el Wi-Fi.
- Utilizar WPA2 o WPA3 cuando sea compatible.
- Cambiar las credenciales de administración predeterminadas.
- Mantener actualizado el firmware del router.
- Restringir el acceso de invitados a los recursos internos cuando corresponda.

---

# GLOSARIO — MÓDULO 4

| Término | Significado |
|---|---|
| LAN | Red de Área Local. |
| WLAN | Red de Área Local Inalámbrica. |
| WAN | Red de Área Amplia. |
| ISP | Proveedor de Servicios de Internet. |
| Router | Equipo que conecta diferentes redes. |
| Switch | Equipo que conecta dispositivos en una LAN. |
| AP | Punto de acceso inalámbrico. |
| Ethernet | Tecnología de redes cableadas. |
| UTP | Par trenzado no blindado. |
| Cat 5e | Categoría de cable de par trenzado. |
| RJ-45 | Denominación habitual del conector Ethernet. |
| GHz | Gigahercios, unidad de frecuencia. |
| IEEE 802.11 | Familia de estándares WLAN. |
| SSID | Identificador de una red inalámbrica. |
| STA | Estación inalámbrica. |
| Canal inalámbrico | Canal de radiofrecuencia utilizado por la WLAN. |
| Modo mixto | Compatibilidad con diferentes estándares Wi-Fi. |
| DHCP | Protocolo de configuración dinámica de host. |
| Gateway | Puerta de enlace hacia otras redes. |
| DNS | Sistema de nombres de dominio. |
| NIC | Tarjeta o interfaz de red. |
| WPA2/WPA3 | Estándares de seguridad inalámbrica. |

---

# RESUMEN GENERAL — MÓDULO 4

1. Una red doméstica conecta dispositivos dentro de una LAN.
2. Una WLAN permite conexiones locales mediante Wi-Fi.
3. El router doméstico puede integrar router, switch y punto de acceso.
4. Los puertos LAN conectan dispositivos locales y el puerto WAN conecta con otra red.
5. Wi-Fi utiliza ondas electromagnéticas, principalmente en las bandas de 2.4 y 5 GHz estudiadas en este módulo.
6. Bluetooth utiliza la banda de 2.4 GHz para comunicaciones de corto alcance.
7. Ethernet permite conectar dispositivos mediante medios cableados.
8. Cat 5e contiene cuatro pares de conductores trenzados.
9. La fibra óptica transmite datos mediante señales luminosas.
10. IEEE 802.11 establece los estándares utilizados en WLAN.
11. El SSID identifica una red inalámbrica y distingue mayúsculas de minúsculas.
12. El modo mixto permite compatibilidad con diferentes estándares inalámbricos.
13. Desactivar la difusión del SSID no garantiza seguridad.
14. DHCP permite asignar automáticamente información de configuración IP.
15. Una red de invitados puede ofrecer Internet y restringir acceso a recursos internos.

**IDEA CLAVE:**

Para configurar correctamente una red doméstica es necesario comprender sus componentes, elegir medios y estándares compatibles, establecer la configuración IP y proteger el acceso inalámbrico.

---

# CUESTIONARIO — MÓDULO 4

**Total:** 10 preguntas  
**Puntaje máximo:** 10 puntos

**Instrucciones:** Marca la respuesta correcta. En las preguntas indicadas debes seleccionar varias opciones.

## PREGUNTA 1

¿Qué puerto de un router doméstico se utiliza normalmente para conectarlo a la red del proveedor de Internet?

- [ ] A. Puerto LAN.
- [ ] B. Puerto WAN/Internet.
- [ ] C. Puerto USB.
- [ ] D. Puerto de consola.

## PREGUNTA 2

¿Cuáles son funciones que puede integrar un router doméstico inalámbrico? (Selecciona tres).

- [ ] A. Switch Ethernet.
- [ ] B. Punto de acceso inalámbrico.
- [ ] C. Router.
- [ ] D. Impresora de red.

## PREGUNTA 3

¿Qué frecuencia se utiliza tanto en Bluetooth como en numerosas redes Wi-Fi domésticas?

- [ ] A. 900 MHz.
- [ ] B. 2.4 GHz.
- [ ] C. 10 GHz.
- [ ] D. 60 GHz.

## PREGUNTA 4

¿Qué estándar establece las especificaciones técnicas de las redes WLAN?

- [ ] A. IEEE 802.11.
- [ ] B. IEEE 802.3.
- [ ] C. DHCP.
- [ ] D. DNS.

## PREGUNTA 5

¿Qué parámetro identifica el nombre de una red Wi-Fi?

- [ ] A. DNS.
- [ ] B. Dirección MAC.
- [ ] C. SSID.
- [ ] D. Gateway.

## PREGUNTA 6

¿Qué configuración permite conectar dispositivos compatibles con diferentes estándares Wi-Fi?

- [ ] A. Modo exclusivo.
- [ ] B. Modo mixto.
- [ ] C. Canal deshabilitado.
- [ ] D. Difusión desactivada.

## PREGUNTA 7

¿Qué servicio permite que una computadora reciba automáticamente una dirección IP y otros parámetros de red?

- [ ] A. DNS.
- [ ] B. DHCP.
- [ ] C. Bluetooth.
- [ ] D. NFC.

## PREGUNTA 8

¿Cuáles son medidas adecuadas para mejorar la seguridad de una red inalámbrica doméstica? (Selecciona dos).

- [ ] A. Utilizar WPA2 o WPA3.
- [ ] B. Mantener las contraseñas predeterminadas.
- [ ] C. Utilizar una contraseña segura.
- [ ] D. Desactivar el cifrado.

## PREGUNTA 9

Si se desactiva la difusión del SSID, la red inalámbrica queda completamente protegida contra accesos no autorizados.

- [ ] A. Verdadero.
- [ ] B. Falso.

## PREGUNTA 10

En muchos routers domésticos, los dispositivos conectados por los puertos LAN y Wi-Fi forman parte de la misma red local predeterminada.

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

# SOLUCIONARIO EXPLICADO

**1. B — Puerto WAN/Internet.**  
Se utiliza normalmente para conectar el router doméstico con la red del proveedor.

**2. A, B y C — Switch, punto de acceso y router.**  
Los routers domésticos integrados pueden proporcionar estas tres funciones.

**3. B — 2.4 GHz.**  
Bluetooth y muchas redes Wi-Fi utilizan la banda de 2.4 GHz.

**4. A — IEEE 802.11.**  
Es la familia de estándares utilizada para las redes WLAN.

**5. C — SSID.**  
Es el identificador que permite reconocer una red Wi-Fi.

**6. B — Modo mixto.**  
Permite que dispositivos compatibles con diferentes estándares inalámbricos se conecten.

**7. B — DHCP.**  
Asigna automáticamente parámetros IP a los clientes de una red.

**8. A y C — WPA2/WPA3 y contraseña segura.**  
Son medidas que ayudan a proteger el acceso inalámbrico.

**9. B — Falso.**  
Ocultar el SSID no sustituye los mecanismos de autenticación y cifrado.

**10. A — Verdadero.**  
En la configuración predeterminada habitual, las conexiones LAN cableadas e inalámbricas pertenecen a la misma red local.

---

**PUNTAJE FINAL: ____ / 10**

# CONCEPTOS QUE DEBES DOMINAR ANTES DEL MÓDULO 5

- Diferencia entre puertos LAN y WAN.
- Funciones de un router doméstico integrado.
- Diferencias entre 2.4 GHz y 5 GHz.
- Tecnología Ethernet y cableado UTP.
- Función de IEEE 802.11.
- Configuración del SSID y del canal inalámbrico.
- Modo mixto y compatibilidad con estándares antiguos.
- Difusión del SSID y seguridad de la WLAN.
- Configuración automática mediante DHCP.
- Redes de invitados y protección de la red doméstica.





# CISCO NETWORKING BASICS
## MÓDULO 4 — CUESTIONARIO DE REFUERZO
### Crear una Red Doméstica

**Total:** 8 preguntas  
**Temas:** Puertos LAN/WAN, Bluetooth, redes de invitados, Wi-Fi, cableado Ethernet y SSID.

---

### PREGUNTA 1

¿Qué tipo de dispositivo se conecta comúnmente a los puertos del switch Ethernet en un enrutador inalámbrico doméstico?

- [ ] A. Cable módem
- [ ] B. Módem DSL
- [ ] C. Antena inalámbrica
- [ ] D. Dispositivo LAN

### PREGUNTA 2

¿Qué tipo de tecnología de red se usa para la comunicación de baja velocidad entre dispositivos periféricos?

- [ ] A. Canales
- [ ] B. 802.11
- [ ] C. Ethernet
- [ ] D. Bluetooth

### PREGUNTA 3

¿Qué se puede usar para permitir que los dispositivos móviles de los visitantes se conecten a una red inalámbrica y para restringir el acceso de esos dispositivos solo a Internet?

- [ ] A. Encriptación
- [ ] B. Filtrado de direcciones MAC
- [ ] C. Autenticación
- [ ] D. SSID de invitados

### PREGUNTA 4

¿Qué propósito tendría un usuario doméstico para implementar Wi-Fi?

- [ ] A. Crear una red inalámbrica que pueda ser utilizada por otros dispositivos.
- [ ] B. Conectar auriculares inalámbricos a un dispositivo móvil.
- [ ] C. Conectar un teclado a una PC.
- [ ] D. Escuchar diversas estaciones de radio.

### PREGUNTA 5

¿Cuál es otro término para el puerto de Internet de un router inalámbrico?

- [ ] A. Puerto de switch
- [ ] B. Puerto local
- [ ] C. Puerto WAN
- [ ] D. Puerto LAN

### PREGUNTA 6

¿Qué tipo de cable de red consta de 4 pares de cables trenzados?

- [ ] A. Fibra óptica
- [ ] B. Ethernet sobre línea eléctrica
- [ ] C. Coaxial
- [ ] D. Categoría 5e

### PREGUNTA 7

¿Cuál es la configuración de transmisión de SSID predeterminada en un enrutador inalámbrico?

- [ ] A. Disabled
- [ ] B. Auto
- [ ] C. Desactivado
- [ ] D. Enabled

### PREGUNTA 8

¿Cuál es una característica del SSID de la red?

- [ ] A. Está encriptado de manera predeterminada.
- [ ] B. Solo se requiere para el acceso de usuarios temporales.
- [ ] C. Contiene exactamente 16 caracteres.
- [ ] D. Debe respetar las mayúsculas y minúsculas.

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

---

# CISCO NETWORKING BASICS
## MÓDULO 4 — CUESTIONARIO DE REFUERZO
### Crear una Red Doméstica

**Total:** 8 preguntas  
**Puntaje máximo:** 8 puntos

**Instrucciones:** Selecciona una respuesta por pregunta. No revises el solucionario hasta terminar.

---

### PREGUNTA 1

¿Qué tipo de dispositivo se conecta comúnmente a los puertos del switch Ethernet en un enrutador inalámbrico doméstico?

- [ ] A. Cable módem
- [ ] B. Módem DSL
- [ ] C. Antena inalámbrica
- [ ] D. Dispositivo LAN

### PREGUNTA 2

¿Qué tipo de tecnología de red se usa para la comunicación de baja velocidad entre dispositivos periféricos?

- [ ] A. Canales
- [ ] B. 802.11
- [ ] C. Ethernet
- [ ] D. Bluetooth

### PREGUNTA 3

¿Qué se puede usar para permitir que los dispositivos móviles de los visitantes se conecten a una red inalámbrica y para restringir el acceso de esos dispositivos solo a Internet?

- [ ] A. Encriptación
- [ ] B. Filtrado de direcciones MAC
- [ ] C. Autenticación
- [ ] D. SSID de invitados

### PREGUNTA 4

¿Qué propósito tendría un usuario doméstico para implementar Wi-Fi?

- [ ] A. Crear una red inalámbrica que pueda ser utilizada por otros dispositivos.
- [ ] B. Conectar auriculares inalámbricos a un dispositivo móvil.
- [ ] C. Conectar un teclado a una PC.
- [ ] D. Escuchar diversas estaciones de radio.

### PREGUNTA 5

¿Cuál es otro término para el puerto de Internet de un router inalámbrico?

- [ ] A. Puerto de switch
- [ ] B. Puerto local
- [ ] C. Puerto WAN
- [ ] D. Puerto LAN

### PREGUNTA 6

¿Qué tipo de cable de red consta de 4 pares de cables trenzados?

- [ ] A. Fibra óptica
- [ ] B. Ethernet sobre línea eléctrica
- [ ] C. Coaxial
- [ ] D. Categoría 5e

### PREGUNTA 7

¿Cuál es la configuración de transmisión de SSID predeterminada en un enrutador inalámbrico?

- [ ] A. Disabled
- [ ] B. Auto
- [ ] C. Desactivado
- [ ] D. Enabled

### PREGUNTA 8

¿Cuál es una característica del SSID de la red?

- [ ] A. Está encriptado de manera predeterminada.
- [ ] B. Solo se requiere para el acceso de usuarios temporales.
- [ ] C. Contiene exactamente 16 caracteres.
- [ ] D. Debe respetar las mayúsculas y minúsculas.

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

---

# SOLUCIONARIO — NO REVISAR ANTES DE TERMINAR

### Pregunta 1
**Respuesta: D. Dispositivo LAN**

Los puertos Ethernet del switch integrado permiten conectar dispositivos de la red local, como computadoras e impresoras.

### Pregunta 2
**Respuesta: D. Bluetooth**

Bluetooth permite la comunicación inalámbrica de corto alcance entre periféricos como teclados, mouse y auriculares.

### Pregunta 3
**Respuesta: D. SSID de invitados**

Una red de invitados puede proporcionar acceso a Internet sin permitir el acceso a los dispositivos internos, si el aislamiento está configurado correctamente.

### Pregunta 4
**Respuesta: A. Crear una red inalámbrica que pueda ser utilizada por otros dispositivos.**

Wi-Fi permite conectar computadoras, celulares y otros dispositivos a una red local inalámbrica.

### Pregunta 5
**Respuesta: C. Puerto WAN**

El puerto WAN o Internet permite conectar el router doméstico con una red externa, normalmente la del ISP.

### Pregunta 6
**Respuesta: D. Categoría 5e**

El cable Cat 5e está compuesto por cuatro pares de conductores de cobre trenzados que ayudan a reducir las interferencias.

### Pregunta 7
**Respuesta: D. Enabled**

En el material de Cisco, la difusión del SSID se encuentra activada de manera predeterminada.

Enabled = Activado.  
Disabled = Desactivado.

### Pregunta 8
**Respuesta: D. Debe respetar las mayúsculas y minúsculas.**

El SSID distingue las letras mayúsculas de las minúsculas.

Ejemplo:

CASA_WIFI y casa_wifi son identificadores diferentes.

---

**PUNTAJE FINAL: ____ / 8**







# CISCO NETWORKING BASICS
## CUESTIONARIO DE REFUERZO — MÓDULOS 2, 3 Y 4

**Total:** 5 preguntas  
**Instrucciones:** Responde sin consultar el solucionario. Algunas preguntas tienen varias respuestas correctas.

---

### PREGUNTA 1

¿Cuáles son los tres dispositivos que se consideran intermedios en una red? (Elija tres opciones).

- [ ] A. Switch
- [ ] B. Estación de trabajo
- [ ] C. Punto de acceso inalámbrico
- [ ] D. Router
- [ ] E. Impresora de red
- [ ] F. Servidor

### PREGUNTA 2

¿Cuáles son dos tipos de conexiones de Internet de alta velocidad cableadas? (Elija dos opciones).

- [ ] A. DSL
- [ ] B. Red celular
- [ ] C. Satelital
- [ ] D. Cable
- [ ] E. Internet por acceso telefónico

### PREGUNTA 3

¿Qué dos métodos se utilizan para conectar directamente dispositivos móviles, como tablets y smartphones, a una red de datos? (Elija dos opciones).

- [ ] A. WiMax
- [ ] B. Wi-Fi
- [ ] C. Ethernet por cable
- [ ] D. Comunicaciones de datos móviles
- [ ] E. Bluetooth

### PREGUNTA 4

¿Qué función es característica del filtrado MAC en redes inalámbricas?

- [ ] A. Permite que solo los usuarios autorizados detecten la red.
- [ ] B. Cifra los datos que se transmiten en una red inalámbrica.
- [ ] C. Se configura en la computadora en lugar de en el enrutador.
- [ ] D. Restringe el acceso de la computadora a una red inalámbrica.

### PREGUNTA 5

¿Qué banda de RF inalámbrica utilizan los dispositivos IEEE 802.11b/g?

- [ ] A. 900 MHz
- [ ] B. Banda de 60 GHz
- [ ] C. 2.4 GHz
- [ ] D. 5 GHz

---

# HOJA DE RESPUESTAS

| Pregunta | Mi respuesta |
|---|---|
| 1 | |
| 2 | |
| 3 | |
| 4 | |
| 5 | |

---

# SOLUCIONARIO — NO REVISAR ANTES DE TERMINAR

### PREGUNTA 1
**Respuesta: A, C y D.**

- Switch.
- Punto de acceso inalámbrico.
- Router.

**Explicación:**

Los dispositivos intermedios conectan equipos y permiten transportar información dentro de una red o entre diferentes redes.

- Switch: conecta dispositivos dentro de una LAN.
- Router: conecta diferentes redes.
- Punto de acceso: permite conectar dispositivos inalámbricos a una red.

**IMPORTANTE:**
- PC, impresora de red y servidor = dispositivos finales.
- Switch, router y punto de acceso = dispositivos intermedios.

### PREGUNTA 2
**Respuesta: A y D.**

- DSL.
- Cable.

**Explicación:**

Son dos tecnologías de acceso cableado a Internet de banda ancha.

- DSL: utiliza líneas telefónicas de cobre.
- Cable: utiliza infraestructura de televisión por cable, generalmente coaxial.

**IMPORTANTE:**

El acceso telefónico por marcación también utiliza una línea telefónica, pero proporciona un ancho de banda muy bajo.

### PREGUNTA 3
**Respuesta: B y D.**

- Wi-Fi.
- Comunicaciones de datos móviles.

**Explicación:**

Son dos métodos comunes que permiten conectar directamente smartphones y tablets a redes de datos.

- Wi-Fi: permite conectarse mediante un punto de acceso inalámbrico.
- Datos móviles: permite conectarse mediante la red celular del operador.

**IMPORTANTE:**

Bluetooth permite conectar accesorios y también puede utilizarse para compartir Internet mediante anclaje, pero en esta pregunta Cisco busca los dos métodos habituales de acceso directo a redes de datos.

### PREGUNTA 4
**Respuesta: D. Restringe el acceso de la computadora a una red inalámbrica.**

**Explicación:**

El filtrado MAC permite aplicar reglas de acceso utilizando las direcciones MAC de los dispositivos.

Ejemplo:

Un router puede configurarse para permitir o bloquear determinados dispositivos según sus direcciones MAC.

**IMPORTANTE:**

- Filtrado MAC = control de acceso por dirección MAC.
- WPA2/WPA3 = mecanismos de seguridad y cifrado Wi-Fi.
- SSID = identificador de la red inalámbrica.

El filtrado MAC no cifra los datos y tampoco garantiza por sí solo una protección segura, porque las direcciones MAC pueden falsificarse.

### PREGUNTA 5
**Respuesta: C. 2.4 GHz.**

**Explicación:**

Los estándares IEEE 802.11b y 802.11g utilizan la banda de frecuencia de 2.4 GHz.

**PARA RECORDAR:**

- 802.11b = 2.4 GHz.
- 802.11g = 2.4 GHz.
- 802.11n = 2.4 GHz y 5 GHz.
- 802.11ac = 5 GHz.

---

# CONCEPTOS IMPORTANTES PARA CISCO

1. Dispositivos intermedios: switch, router y punto de acceso.
2. Dispositivos finales: computadora, servidor e impresora de red.
3. DSL y cable: conexiones cableadas de banda ancha.
4. Wi-Fi y datos celulares: métodos comunes de acceso de dispositivos móviles a redes de datos.
5. Filtrado MAC: restringe o permite acceso según direcciones MAC.
6. WPA2/WPA3: seguridad de redes inalámbricas.
7. IEEE 802.11b/g: banda de 2.4 GHz.
8. IEEE 802.11n: bandas de 2.4 y 5 GHz.
9. IEEE 802.11ac: banda de 5 GHz.

---

**PUNTAJE FINAL: ____ / 5**

