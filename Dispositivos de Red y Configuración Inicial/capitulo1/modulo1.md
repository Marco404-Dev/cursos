
# Módulo 1: Diseño de Redes

**Curso:** Cisco Networking Academy — Dispositivos de Red y Configuración Inicial

## 1. Arquitectura de red

La arquitectura de red es el conjunto de tecnologías, dispositivos, servicios y protocolos que permiten la comunicación entre equipos.

Una red bien diseñada debe cumplir cuatro características:

| Característica | Descripción |
|---|---|
| Tolerancia a fallas | Mantener la comunicación aunque falle un enlace o dispositivo. |
| Escalabilidad | Permitir el crecimiento de la red sin afectar significativamente su rendimiento. |
| Calidad de servicio (QoS) | Priorizar el tráfico importante cuando existe congestión. |
| Seguridad | Proteger los dispositivos, servicios y datos de la red. |

## 2. Tolerancia a fallas

Una red tolerante a fallas puede continuar funcionando cuando ocurre un problema.

### Redundancia

Consiste en disponer de varias rutas para llegar a un destino.

**Ejemplo:**

- Ruta principal: PC → R1 → R2 → Servidor.
- Ruta alternativa: PC → R1 → R3 → Servidor.

Si falla la conexión entre R1 y R2, los paquetes pueden utilizar la ruta alternativa, siempre que la red esté configurada para ello.

### Conmutación de paquetes

La información se divide en unidades más pequeñas llamadas **paquetes**.

Cada paquete contiene información necesaria para llegar a su destino.

Los paquetes pueden recorrer diferentes rutas y llegar al mismo destino.

**Importante:** La redundancia permite utilizar rutas alternativas cuando ocurre una falla.

## 3. Escalabilidad

Es la capacidad de ampliar una red para incorporar más usuarios, dispositivos y aplicaciones sin perjudicar significativamente los servicios existentes.

**Ejemplo:**

Una universidad tiene 100 computadoras y necesita agregar otras 50.

Una red escalable permite incorporar esos equipos sin rediseñar completamente su infraestructura.

La escalabilidad se facilita mediante estándares, protocolos y una arquitectura adecuada.

## 4. Calidad de servicio (QoS)

**QoS (Quality of Service)** permite administrar y priorizar el tráfico de una red.

Se utiliza especialmente cuando existe congestión.

### Congestión

Ocurre cuando la demanda de ancho de banda supera la capacidad disponible de la red.

**Ejemplo:**

Dos usuarios utilizan Internet:

- Usuario A: realiza una videollamada.
- Usuario B: descarga un archivo.

Si existe congestión, QoS puede dar prioridad a la videollamada porque necesita comunicación en tiempo real.

Los dispositivos pueden almacenar temporalmente paquetes en colas mientras esperan ser transmitidos.

### Ancho de banda

Es la capacidad de transmisión de un enlace, expresada en bits por segundo (bps).

**Importante:** QoS no aumenta el ancho de banda disponible. Administra el tráfico según las prioridades establecidas.

## 5. Seguridad de red

La seguridad protege la infraestructura y la información que circula por una red.

Se divide en:

- **Seguridad de infraestructura:** proteger routers, switches y otros dispositivos contra accesos no autorizados.
- **Seguridad de información:** proteger los datos almacenados y transmitidos.

### Principios CIA

| Principio | Significado | Ejemplo |
|---|---|---|
| Confidencialidad | Solo las personas autorizadas pueden acceder a la información. | Contraseñas y cifrado. |
| Integridad | La información no debe modificarse sin autorización. | Verificación de datos. |
| Disponibilidad | Los servicios deben estar accesibles cuando se necesiten. | Servidores redundantes. |

**Recuerda:** CIA = Confidencialidad, Integridad y Disponibilidad.

## 6. Direcciones físicas y lógicas

Para comunicarse en una red Ethernet/IP, los dispositivos utilizan direcciones MAC e IP.

| Dirección MAC | Dirección IP |
|---|---|
| Dirección física de una interfaz de red. | Dirección lógica asignada a una interfaz. |
| Trabaja en la capa 2 del modelo OSI. | Trabaja en la capa 3 del modelo OSI. |
| Identifica una interfaz en la red local. | Permite identificar y localizar dispositivos en redes IP. |
| Normalmente está asignada por el fabricante, aunque puede modificarse por software. | Puede asignarse manualmente o automáticamente mediante DHCP. |

### Ejemplo

Una computadora tiene:

- MAC: `00:1A:2B:3C:4D:5E`
- IPv4: `192.168.1.10`
- Máscara: `255.255.255.0`

La dirección IPv4 contiene dos partes determinadas por la máscara:

- **Parte de red:** `192.168.1.0/24`
- **Parte de host:** identifica al dispositivo dentro de esa red.

En este ejemplo, el identificador de host es `10`.

**Importante:** La dirección MAC se utiliza para entregar tramas en el enlace local, mientras que la dirección IP permite el direccionamiento entre redes.

## 7. Diseño de redes jerárquico

Consiste en organizar una red en diferentes niveles para facilitar su administración, crecimiento y funcionamiento.

### ¿Por qué utilizarlo?

En una red Ethernet muy grande, las difusiones (broadcast) pueden generar tráfico innecesario.

Por eso, es conveniente dividir las redes grandes en redes más pequeñas y fáciles de administrar.

### Analogía geográfica

Para localizar una dirección podemos utilizar una jerarquía:

América del Norte → Canadá → Nueva Escocia → Halifax

De manera similar, las direcciones IP permiten identificar redes y dispositivos dentro de ellas.

Las direcciones MAC identifican interfaces, pero no indican por sí mismas su ubicación dentro de una red IP.

## 8. Capas del diseño jerárquico

El modelo jerárquico de Cisco tiene tres capas principales.

### 8.1. Capa de acceso (Access Layer)

Es el punto donde los dispositivos finales se conectan a la red.

**Dispositivos habituales:**
- Switches de acceso.
- Puntos de acceso inalámbricos.

**Ejemplo Cisco:** Catalyst 2960-XR.

**Función:** Conectar computadoras, impresoras y otros dispositivos finales.

### 8.2. Capa de distribución (Distribution Layer)

Conecta las redes de acceso y controla el tráfico entre ellas.

Puede utilizar switches de capa 3 y routers.

**Funciones:**
- Conectar diferentes redes.
- Realizar enrutamiento entre redes.
- Aplicar políticas y controlar el tráfico.
- Conectar la capa de acceso con la capa de núcleo.

**Ejemplo Cisco:** Catalyst C9300.

### 8.3. Capa de núcleo (Core Layer)

Es la parte central de alta velocidad de una red jerárquica.

Transporta grandes cantidades de información entre diferentes partes de la infraestructura.

**Características:**
- Alta velocidad.
- Alta disponibilidad.
- Enlaces redundantes.
- Transporte eficiente de paquetes.

**Ejemplo Cisco:** Catalyst 9600.

### Comparación

| Capa | Función principal |
|---|---|
| Acceso | Conectar dispositivos finales. |
| Distribución | Conectar redes y administrar el tráfico. |
| Núcleo | Transportar información rápidamente entre redes. |

### Ejemplo práctico

Una computadora necesita comunicarse con un servidor ubicado en otra red de una universidad.

El tráfico puede seguir esta estructura:

PC → Switch de acceso → Switch de distribución → Núcleo → Red del servidor

**Nota:** No todas las comunicaciones necesitan atravesar las tres capas. Depende de la ubicación del destino y de la topología.

---

# 10 preguntas de repaso

### 1. ¿Cuáles son las cuatro características principales de una red confiable?

<details>
<summary>Ver respuesta</summary>

Tolerancia a fallas, escalabilidad, calidad de servicio (QoS) y seguridad.

</details>

### 2. ¿Qué significa redundancia en una red?

<details>
<summary>Ver respuesta</summary>

Disponer de rutas o recursos alternativos para mantener la comunicación cuando ocurre una falla.

</details>

### 3. ¿Qué es la conmutación de paquetes?

<details>
<summary>Ver respuesta</summary>

Es un método de comunicación que divide la información en paquetes que pueden viajar por diferentes rutas hasta llegar al destino.

</details>

### 4. ¿Qué significa que una red sea escalable?

<details>
<summary>Ver respuesta</summary>

Que puede incorporar nuevos usuarios, dispositivos y aplicaciones sin afectar significativamente el rendimiento existente.

</details>

### 5. ¿Cuál es la función principal de QoS?

<details>
<summary>Ver respuesta</summary>

Administrar y priorizar el tráfico de la red, especialmente cuando existe congestión.

</details>

### 6. ¿Cuáles son los tres principios de seguridad de la información?

<details>
<summary>Ver respuesta</summary>

Confidencialidad, integridad y disponibilidad (CIA).

</details>

### 7. ¿Cuál es la diferencia entre una dirección MAC y una dirección IP?

<details>
<summary>Ver respuesta</summary>

La MAC identifica una interfaz de red a nivel de enlace, mientras que la IP es una dirección lógica utilizada para el direccionamiento y enrutamiento.

</details>

### 8. ¿Por qué es recomendable dividir una red Ethernet grande?

<details>
<summary>Ver respuesta</summary>

Para reducir los dominios de difusión cuando se realiza una segmentación adecuada, facilitar la administración y mejorar la escalabilidad.

</details>

### 9. ¿Cuáles son las tres capas de un diseño de red jerárquico?

<details>
<summary>Ver respuesta</summary>

Acceso, distribución y núcleo.

</details>

### 10. ¿Qué capa del modelo jerárquico se encarga principalmente de transportar grandes cantidades de datos a alta velocidad?

<details>
<summary>Ver respuesta</summary>

La capa de núcleo (Core Layer).

</details>

---

**Fin del Módulo 1 — Diseño de Redes**
