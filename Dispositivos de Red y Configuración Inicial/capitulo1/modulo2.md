
# Módulo 2: La Nube y Virtualización

**Curso:** Cisco Networking Academy — Dispositivos de Red y Configuración Inicial

## 1. Computación en la nube

La computación en la nube (Cloud Computing) permite utilizar recursos informáticos a través de una red, generalmente Internet, sin necesidad de tener toda la infraestructura físicamente en nuestro equipo.

Por ejemplo, una empresa puede utilizar servidores de AWS en lugar de comprar y mantener sus propios servidores.

### Tres elementos principales

| Elemento | Función |
|---|---|
| Centro de datos (Data Center) | Instalación física que alberga servidores, redes y almacenamiento. |
| Computación en la nube | Proporciona recursos informáticos bajo demanda. |
| Virtualización | Permite crear recursos virtuales utilizando hardware físico. |

### Centros de datos

Son instalaciones que contienen numerosos servidores y equipos de red.

Necesitan:

- Energía eléctrica.
- Refrigeración.
- Conexiones de red de gran capacidad.
- Seguridad física y lógica.

**Ejemplo:** AWS utiliza centros de datos para proporcionar sus servicios en la nube.

## 2. Modelos de servicios en la nube

Existen tres modelos principales:

| Modelo | Significado | ¿Qué proporciona? | Ejemplo |
|---|---|---|---|
| SaaS | Software as a Service | Aplicaciones listas para utilizar. | Gmail |
| PaaS | Platform as a Service | Plataforma para desarrollar y ejecutar aplicaciones. | Heroku |
| IaaS | Infrastructure as a Service | Servidores, redes y almacenamiento virtuales. | Amazon EC2 |

### SaaS — Software como servicio

Utilizas una aplicación que funciona en la nube sin administrar sus servidores.

**Ejemplo:** Usar Gmail desde el navegador.

### PaaS — Plataforma como servicio

El proveedor proporciona un entorno para desarrollar y ejecutar aplicaciones.

**Ejemplo:** Publicar una aplicación web en Heroku sin administrar directamente el sistema operativo del servidor.

### IaaS — Infraestructura como servicio

El proveedor ofrece infraestructura virtual, como máquinas virtuales, almacenamiento y redes.

**Ejemplo:** Crear una máquina virtual Linux en Amazon EC2 y configurar su sistema operativo.

**Recuerda:**

- SaaS = Utilizar software.
- PaaS = Desarrollar y ejecutar aplicaciones.
- IaaS = Administrar infraestructura virtual.

## 3. Tipos de nube

Existen cuatro modelos principales.

| Tipo | Descripción | Ejemplo |
|---|---|---|
| Pública | Servicios disponibles para diferentes clientes a través de un proveedor. | AWS |
| Privada | Infraestructura destinada a una sola organización. | Nube privada de una empresa. |
| Híbrida | Combina dos o más entornos de nube conectados. | Nube privada + AWS. |
| Comunitaria | Infraestructura compartida por organizaciones con necesidades comunes. | Nube compartida entre hospitales. |

### Nube pública

Los recursos son ofrecidos por un proveedor externo a múltiples clientes.

**Ejemplo:** Una empresa alquila servidores virtuales en AWS.

### Nube privada

Los recursos están destinados exclusivamente a una organización.

**Ejemplo:** Una entidad gubernamental utiliza su propia infraestructura de nube privada.

### Nube híbrida

Combina entornos de nube diferentes que pueden intercambiar información o servicios.

**Ejemplo:** Una empresa almacena datos sensibles en su nube privada y utiliza una nube pública para otras aplicaciones.

### Nube comunitaria

Es utilizada por varias organizaciones con necesidades compartidas.

**Ejemplo:** Varios hospitales utilizan una nube diseñada para cumplir requisitos específicos de seguridad y privacidad.

## 4. Virtualización

La virtualización permite crear versiones virtuales de recursos informáticos, como computadoras, servidores o sistemas operativos.

**Ejemplo:**

Tienes Windows instalado en tu computadora y utilizas VirtualBox para ejecutar Ubuntu dentro de una máquina virtual.

En ese caso:

- Windows: sistema operativo anfitrión.
- VirtualBox: software de virtualización.
- Ubuntu: sistema operativo invitado.
- Máquina virtual (VM): computadora simulada mediante software.

La máquina virtual utiliza recursos del equipo físico, como CPU, RAM, almacenamiento y red.

### Diferencia entre nube y virtualización

| Virtualización | Computación en la nube |
|---|---|
| Crea recursos virtuales utilizando hardware físico. | Ofrece recursos y servicios informáticos bajo demanda. |
| Puede funcionar sin Internet. | Habitualmente se accede mediante una red. |
| Ejemplo: Ubuntu en VirtualBox. | Ejemplo: máquina virtual en AWS. |

**Importante:** Virtualización y computación en la nube no son lo mismo. La virtualización es una tecnología fundamental para muchos servicios de nube.

## 5. Servidores dedicados

Tradicionalmente, las empresas utilizaban servidores físicos dedicados a determinadas tareas.

Por ejemplo:

- Servidor 1: página web.
- Servidor 2: correo electrónico.
- Servidor 3: base de datos.

### Problemas principales

**Punto único de falla (Single Point of Failure):**

Si falla el servidor y no existe un sistema de respaldo, el servicio deja de funcionar.

**Proliferación de servidores (Server Sprawl):**

Tener demasiados servidores físicos que utilizan pocos recursos.

Esto provoca mayor consumo de energía, espacio y costos de mantenimiento.

### Solución: consolidación de servidores

Consiste en ejecutar varias máquinas virtuales sobre menos servidores físicos.

**Ejemplo:**

En lugar de utilizar tres servidores físicos, una empresa podría ejecutar tres máquinas virtuales en un único servidor.

Esto reduce costos, aunque también requiere considerar la redundancia para evitar un punto único de falla.

## 6. Ventajas de la virtualización

| Ventaja | Explicación |
|---|---|
| Menos equipos | Varios servidores virtuales pueden compartir un servidor físico. |
| Menor consumo eléctrico | Se necesitan menos equipos y refrigeración. |
| Menos espacio | Disminuye la cantidad de servidores físicos. |
| Laboratorios de prueba | Permite experimentar en entornos aislados. |
| Aprovisionamiento rápido | Las máquinas virtuales se pueden crear rápidamente. |
| Mayor disponibilidad | Algunas plataformas incorporan mecanismos de redundancia. |
| Recuperación ante desastres | Facilita respaldos y recuperación de servicios. |
| Compatibilidad | Permite seguir utilizando sistemas operativos antiguos. |

**Ejemplo práctico:**

Puedes crear una VM con Ubuntu para practicar Linux y redes sin tener que reemplazar Windows.

## 7. Hipervisores

Un hipervisor (Hypervisor) es software, firmware o una capa especializada que permite crear y ejecutar máquinas virtuales.

Administra el acceso a los recursos físicos:

- CPU.
- RAM.
- Almacenamiento.
- Tarjetas de red (NIC).

Existen dos tipos principales.

### 7.1. Hipervisor tipo 1 — Bare Metal

Se instala directamente sobre el hardware físico, sin necesitar un sistema operativo anfitrión convencional.

**Estructura:**

Hardware físico  
↓  
Hipervisor tipo 1  
↓  
Máquinas virtuales (Windows, Linux, etc.)

**Características:**

- Acceso directo al hardware.
- Buen rendimiento y escalabilidad.
- Utilizado principalmente en centros de datos y servidores empresariales.

**Ejemplos:**
- VMware ESXi.
- Microsoft Hyper-V Server.
- Xen.

### 7.2. Hipervisor tipo 2 — Hosted

Se instala sobre un sistema operativo existente, como Windows o Linux.

**Estructura:**

Hardware físico  
↓  
Sistema operativo anfitrión  
↓  
Hipervisor tipo 2  
↓  
Máquinas virtuales (Windows, Linux, etc.)

**Características:**

- Fácil de instalar y utilizar.
- Ideal para estudiantes y laboratorios.
- Depende del sistema operativo anfitrión.
- Comparte los recursos físicos con el anfitrión.

**Ejemplos:**
- Oracle VirtualBox.
- VMware Workstation.
- VMware Fusion.

### Comparación de hipervisores

| Característica | Tipo 1 | Tipo 2 |
|---|---|---|
| Instalación | Directamente sobre el hardware. | Sobre un sistema operativo. |
| Uso principal | Servidores empresariales. | Computadoras personales y laboratorios. |
| Rendimiento | Generalmente mayor eficiencia. | Mayor sobrecarga por el sistema anfitrión. |
| Ejemplo | VMware ESXi. | VirtualBox. |

**Importante:** Un hipervisor tipo 2 requiere que el equipo anfitrión tenga suficientes recursos para ejecutar sus máquinas virtuales.

---

# 10 preguntas de repaso — Módulo 2

### 1. ¿Cuáles son los tres elementos principales relacionados con la computación en la nube?

A) Routers, switches y firewalls.  
B) Centros de datos, computación en la nube y virtualización.  
C) LAN, MAN y WAN.  
D) SaaS, TCP y UDP.

<details>
<summary>Ver respuesta</summary>

✅ **B) Centros de datos, computación en la nube y virtualización.**

Son tres elementos fundamentales que permiten proporcionar servicios informáticos mediante la nube.

</details>

### 2. ¿Qué modelo de servicio permite utilizar aplicaciones listas para usar sin administrar su infraestructura?

A) IaaS.  
B) PaaS.  
C) SaaS.  
D) Nube híbrida.

<details>
<summary>Ver respuesta</summary>

✅ **C) SaaS.**

Software como servicio proporciona aplicaciones listas para utilizar, como Gmail.

</details>

### 3. Una empresa necesita alquilar máquinas virtuales y configurar sus sistemas operativos. ¿Qué modelo debe utilizar?

A) IaaS.  
B) SaaS.  
C) PaaS.  
D) Nube comunitaria.

<details>
<summary>Ver respuesta</summary>

✅ **A) IaaS.**

Infraestructura como servicio proporciona servidores virtuales, almacenamiento y redes que el cliente puede administrar.

</details>

### 4. ¿Qué tipo de nube combina entornos públicos y privados conectados?

A) Comunitaria.  
B) Pública.  
C) Privada.  
D) Híbrida.

<details>
<summary>Ver respuesta</summary>

✅ **D) Híbrida.**

La nube híbrida permite integrar recursos de diferentes entornos de nube.

</details>

### 5. ¿Cuál es la diferencia principal entre virtualización y computación en la nube?

A) La virtualización siempre necesita Internet.  
B) La virtualización crea recursos virtuales y la nube proporciona servicios informáticos bajo demanda.  
C) Ambas son exactamente lo mismo.  
D) La nube solamente funciona con servidores físicos dedicados.

<details>
<summary>Ver respuesta</summary>

✅ **B) La virtualización crea recursos virtuales y la nube proporciona servicios informáticos bajo demanda.**

La virtualización es una tecnología fundamental para muchas infraestructuras de nube.

</details>

### 6. ¿Qué significa que un servidor sea un punto único de falla?

A) Que tiene demasiada memoria RAM.  
B) Que puede ejecutar varias máquinas virtuales.  
C) Que su falla puede interrumpir un servicio porque no existe una alternativa de respaldo.  
D) Que siempre tiene dos conexiones a Internet.

<details>
<summary>Ver respuesta</summary>

✅ **C) Que su falla puede interrumpir un servicio porque no existe una alternativa de respaldo.**

Un punto único de falla representa un componente cuya pérdida puede dejar un servicio indisponible.

</details>

### 7. ¿Cuál de las siguientes es una ventaja de la virtualización?

A) Reduce la cantidad de servidores físicos necesarios mediante consolidación.  
B) Elimina completamente las fallas de hardware.  
C) Permite ejecutar máquinas virtuales sin consumir RAM.  
D) Hace innecesaria la seguridad informática.

<details>
<summary>Ver respuesta</summary>

✅ **A) Reduce la cantidad de servidores físicos necesarios mediante consolidación.**

Permite aprovechar mejor los recursos físicos y reducir costos operativos.

</details>

### 8. ¿Qué caracteriza a un hipervisor tipo 1?

A) Se instala exclusivamente en Windows.  
B) Necesita VirtualBox para funcionar.  
C) Solo se utiliza para videojuegos.  
D) Se instala directamente sobre el hardware físico.

<details>
<summary>Ver respuesta</summary>

✅ **D) Se instala directamente sobre el hardware físico.**

Se denomina Bare Metal y es habitual en entornos empresariales y centros de datos.

</details>

### 9. Un estudiante utiliza VirtualBox en Windows para ejecutar Ubuntu. ¿Qué tipo de hipervisor está utilizando?

A) Tipo 1.  
B) Tipo 2.  
C) Un servidor dedicado.  
D) Una nube comunitaria.

<details>
<summary>Ver respuesta</summary>

✅ **B) Tipo 2.**

VirtualBox funciona sobre un sistema operativo anfitrión como Windows.

</details>

### 10. ¿Qué función cumple principalmente un hipervisor?

A) Asignar direcciones IP públicas a Internet.  
B) Sustituir todos los protocolos de red.  
C) Crear y administrar máquinas virtuales utilizando recursos físicos.  
D) Convertir automáticamente una LAN en una WAN.

<details>
<summary>Ver respuesta</summary>

✅ **C) Crear y administrar máquinas virtuales utilizando recursos físicos.**

Un hipervisor permite compartir y administrar CPU, RAM, almacenamiento y otros recursos entre diferentes máquinas virtuales.

</details>

---

**Fin del Módulo 2 — La Nube y Virtualización**
