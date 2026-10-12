
# CISCO NETWORKING BASICS
## MÓDULO 8 — EL PROTOCOLO DE INTERNET

**Objetivo:** Comprender la función de las direcciones IPv4, su estructura de 32 bits y cómo se identifican las porciones de red y de host.

---

# 8.1 — DIRECCIONAMIENTO IPv4

## 8.1.1 — La dirección IPv4

### ¿Qué es una dirección IPv4?

Una **dirección IPv4 (Internet Protocol version 4)** es una dirección lógica que permite identificar una interfaz de red de un dispositivo dentro de una red IP.

Se utiliza para que los dispositivos puedan enviar y recibir información.

**Ejemplo de dirección IPv4:**

192.168.1.10

### ¿Para qué sirve?

- Identificar interfaces de red.
- Permitir la comunicación entre dispositivos.
- Indicar el origen y destino de los paquetes IP.
- Facilitar la comunicación entre diferentes redes.

### ¿Qué es una NIC?

**NIC (Network Interface Card)** significa Tarjeta de Interfaz de Red.

Es el componente o interfaz que permite conectar un dispositivo a una red.

**Ejemplos de dispositivos con interfaces de red:**

- Computadoras.
- Servidores.
- Impresoras de red.
- Teléfonos IP.
- Routers.

### ¿Cómo funciona una dirección IPv4?

Imagina dos computadoras conectadas a una misma LAN.

**PC1:**
- IP: 192.168.1.10

**PC2:**
- IP: 192.168.1.20

Ambas utilizan la máscara 255.255.255.0.

**Funcionamiento:**

1. PC1 necesita enviar información a PC2.
2. PC1 identifica la dirección IPv4 de destino.
3. Los datos se preparan para la transmisión.
4. La información viaja mediante la red.
5. PC2 recibe los paquetes destinados a su dirección IP.

**Ejemplo:**

PC1 (192.168.1.10)
        |
      Switch
        |
PC2 (192.168.1.20)

### ¿Una computadora puede tener varias direcciones IP?

**Sí.**

Un dispositivo puede tener varias interfaces de red y cada una puede disponer de su propia configuración IPv4.

**Ejemplo:**

Un servidor puede tener dos interfaces:

- NIC1: 192.168.1.10
- NIC2: 192.168.2.10

### ¿Las direcciones IPv4 deben ser únicas?

Las direcciones IPv4 deben configurarse correctamente para evitar conflictos dentro de una misma red.

**IMPORTANTE:**

- Las direcciones IPv4 privadas pueden reutilizarse en redes diferentes.
- Las direcciones IPv4 públicas utilizadas en Internet deben administrarse de manera que no existan conflictos de direccionamiento global.
- Un router puede permitir que varios dispositivos privados accedan a Internet mediante NAT.

### ¿Qué información lleva un paquete IPv4?

Cada paquete IPv4 incluye:

- **Dirección IP de origen:** identifica al emisor.
- **Dirección IP de destino:** identifica al destinatario.

**PARA RECORDAR:**

- IPv4 = dirección lógica.
- NIC = interfaz de red.
- IP origen = quién envía.
- IP destino = quién recibe.

---

## 8.1.2 — Octetos y notación decimal con puntos

### ¿Cuántos bits tiene una dirección IPv4?

Una dirección IPv4 tiene **32 bits**.

Estos 32 bits se organizan en cuatro grupos de 8 bits llamados **octetos**.

**Fórmula:**

4 octetos × 8 bits = 32 bits.

### ¿Qué es un octeto?

Un **octeto** es un grupo de 8 bits.

Cada octeto puede representar un valor decimal entre **0 y 255**.

### Ejemplo de Cisco

**Dirección IPv4 en binario:**

11010001.10100101.11001000.00000001

**Dirección IPv4 en decimal:**

209.165.200.1

### ¿Cómo se organiza?

| Octeto | Binario | Decimal |
|---|---|---|
| 1 | 11010001 | 209 |
| 2 | 10100101 | 165 |
| 3 | 11001000 | 200 |
| 4 | 00000001 | 1 |

**Resultado:**

209.165.200.1

### ¿Qué es la notación decimal con puntos?

Es la forma de escribir una dirección IPv4 utilizando cuatro números decimales separados por puntos.

**Ejemplo:**

192.168.1.10

Se utiliza porque es más fácil de leer que una dirección de 32 bits en binario.

**IMPORTANTE:**

- IPv4 = 32 bits.
- 4 octetos.
- Cada octeto = 8 bits.
- Valores por octeto = 0 a 255.
- Los octetos se separan mediante puntos.

---

# 8.2 — ESTRUCTURA DE LA DIRECCIÓN IPv4

## 8.2.2 — Redes y hosts

### ¿Cómo está formada una dirección IPv4?

Una dirección IPv4 tiene una estructura jerárquica formada por dos partes:

**1. Porción de red**

Identifica la red a la que pertenece la dirección.

**2. Porción de host**

Identifica la dirección del dispositivo o interfaz dentro de esa red.

### Ejemplo de Cisco

**Dirección IPv4:**

192.168.5.11

**Máscara de subred:**

255.255.255.0

**Representación:**

192.168.5 | 11

Porción de red | Porción de host

En este ejemplo:

- **192.168.5** = porción de red.
- **11** = porción de host.

La red correspondiente es:

192.168.5.0/24

### ¿Qué es una máscara de subred?

La **máscara de subred (Subnet Mask)** permite identificar qué bits de una dirección IPv4 corresponden a la red y cuáles al host.

**Ejemplo:**

IP: 192.168.5.11

Máscara: 255.255.255.0

La máscara indica que los primeros 24 bits corresponden a la red y los últimos 8 bits al host.

### ¿Qué significa /24?

Es una representación de la longitud del prefijo de red.

**Ejemplo:**

192.168.5.11/24

El número 24 indica que los primeros 24 bits pertenecen a la porción de red.

**IMPORTANTE:**

No siempre los primeros tres octetos representan la red.

Esto depende de la máscara de subred utilizada.

---

## ¿Cómo identificar si dos dispositivos pertenecen a la misma red?

Para determinarlo, se compara la porción de red calculada mediante la máscara.

### Ejemplo 1 — Misma red

**PC1:**
- IP: 192.168.5.10
- Máscara: 255.255.255.0

**PC2:**
- IP: 192.168.5.20
- Máscara: 255.255.255.0

Ambas direcciones pertenecen a:

**192.168.5.0/24**

Por lo tanto, pueden comunicarse directamente dentro de una LAN correctamente configurada.

### Ejemplo 2 — Diferentes redes

**PC1:**
- IP: 192.168.5.10/24

**PC2:**
- IP: 192.168.18.20/24

Las direcciones pertenecen a redes diferentes:

- PC1 → 192.168.5.0/24
- PC2 → 192.168.18.0/24

Para comunicarse entre estas redes se necesita un dispositivo que realice **enrutamiento (routing)**.

### ¿Qué es el routing?

**Routing o enrutamiento** es el proceso de seleccionar rutas y reenviar paquetes entre diferentes redes IP.

Los routers utilizan información de las redes de destino para tomar decisiones de encaminamiento.

**Ejemplo:**

Red A (192.168.5.0/24)
          |
        Router
          |
Red B (192.168.18.0/24)

### ¿Por qué se utiliza el direccionamiento jerárquico?

Porque permite organizar los dispositivos por redes y facilita el enrutamiento.

Un router puede utilizar rutas hacia redes completas, en lugar de necesitar una ruta individual para cada host.

**Analogía:**

En una dirección postal:

- Ciudad y calle → ayudan a identificar la ubicación general.
- Número de casa → identifica el destino particular.

En IPv4:

- Porción de red → identifica la red.
- Porción de host → identifica la dirección dentro de esa red.

---

# TABLA DE CONCEPTOS IMPORTANTES

| Concepto | Función |
|---|---|
| IPv4 | Direccionamiento lógico de red. |
| 32 bits | Longitud de una dirección IPv4. |
| Octeto | Grupo de 8 bits. |
| Notación decimal | Cuatro números separados por puntos. |
| NIC | Interfaz que permite conectar un dispositivo a una red. |
| Máscara de subred | Identifica los bits de red y host. |
| Porción de red | Identifica la red. |
| Porción de host | Identifica la dirección dentro de la red. |
| /24 | Prefijo que utiliza 24 bits para la red. |
| Router | Permite comunicar diferentes redes. |
| Routing | Proceso de enrutamiento entre redes. |

---

# RESUMEN GENERAL — MÓDULO 8

1. Una dirección IPv4 es una dirección lógica utilizada para la comunicación entre dispositivos.
2. Las direcciones IPv4 se asignan a interfaces de red.
3. Los paquetes IPv4 contienen direcciones de origen y destino.
4. Una dirección IPv4 tiene 32 bits.
5. Los 32 bits se dividen en cuatro octetos.
6. Cada octeto contiene ocho bits.
7. Cada octeto puede representar valores de 0 a 255.
8. La notación decimal con puntos facilita la lectura de las direcciones IP.
9. Una dirección IPv4 está formada por una porción de red y una porción de host.
10. La máscara de subred permite identificar ambas porciones.
11. Las direcciones que pertenecen a una misma red pueden comunicarse localmente mediante la infraestructura adecuada.
12. Los dispositivos que pertenecen a diferentes redes necesitan enrutamiento para comunicarse.
13. El direccionamiento jerárquico permite organizar y administrar redes de manera eficiente.

**IDEA CLAVE:**

La dirección IPv4 identifica lógicamente una interfaz de red. La máscara de subred permite determinar a qué red pertenece y qué parte identifica al host.

---

# CUESTIONARIO — MÓDULO 8

**Total:** 10 preguntas
**Puntaje máximo:** 10 puntos

**Instrucciones:** Selecciona la alternativa correcta. En las preguntas indicadas debes elegir varias opciones.

## PREGUNTA 1

¿Cuántos bits contiene una dirección IPv4?

- [ ] A. 8 bits.
- [ ] B. 16 bits.
- [ ] C. 32 bits.
- [ ] D. 64 bits.

## PREGUNTA 2

¿Cuántos octetos tiene una dirección IPv4?

- [ ] A. 2.
- [ ] B. 4.
- [ ] C. 6.
- [ ] D. 8.

## PREGUNTA 3

¿Qué es un octeto?

- [ ] A. Un grupo de 4 bits.
- [ ] B. Un grupo de 8 bits.
- [ ] C. Un grupo de 16 bits.
- [ ] D. Un grupo de 32 bits.

## PREGUNTA 4

¿Cuál de las siguientes direcciones utiliza correctamente la notación decimal con puntos de IPv4?

- [ ] A. 192.168.1.10
- [ ] B. 192.168.1
- [ ] C. 192.168.300.10
- [ ] D. 192:168:1:10

## PREGUNTA 5

¿Qué componente permite identificar qué parte de una dirección IPv4 corresponde a la red y cuál al host?

- [ ] A. Dirección MAC.
- [ ] B. Máscara de subred.
- [ ] C. Cable Ethernet.
- [ ] D. Servidor web.

## PREGUNTA 6

Una computadora tiene la dirección 192.168.5.11 y la máscara 255.255.255.0.

¿Cuál es la porción de red?

- [ ] A. 192.168.5
- [ ] B. 11
- [ ] C. 255.255.255
- [ ] D. 192.168.11

## PREGUNTA 7

Dos computadoras tienen las siguientes direcciones:

PC1: 192.168.1.10/24

PC2: 192.168.1.20/24

¿Qué afirmación es correcta?

- [ ] A. Pertenecen a redes diferentes.
- [ ] B. Pertenecen a la misma red IP.
- [ ] C. Necesitan obligatoriamente un router para comunicarse.
- [ ] D. No pueden utilizar Ethernet.

## PREGUNTA 8

¿Qué dispositivo permite comunicar hosts que pertenecen a diferentes redes IPv4?

- [ ] A. Hub.
- [ ] B. Router.
- [ ] C. Monitor.
- [ ] D. Teclado.

## PREGUNTA 9

¿Cuáles de las siguientes afirmaciones sobre IPv4 son correctas? (Selecciona tres).

- [ ] A. Utiliza direcciones de 32 bits.
- [ ] B. Se representa mediante cuatro octetos.
- [ ] C. Cada octeto contiene ocho bits.
- [ ] D. Cada dirección IPv4 tiene seis octetos.

## PREGUNTA 10

La porción de red de una dirección IPv4 siempre corresponde exactamente a los primeros tres octetos.

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

# SOLUCIONARIO — NO REVISAR ANTES DE TERMINAR

### PREGUNTA 1
**Respuesta: C. 32 bits.**

Las direcciones IPv4 tienen una longitud de 32 bits.

### PREGUNTA 2
**Respuesta: B. 4.**

Una dirección IPv4 contiene cuatro octetos.

### PREGUNTA 3
**Respuesta: B. Un grupo de 8 bits.**

Cada octeto contiene exactamente ocho bits.

### PREGUNTA 4
**Respuesta: A. 192.168.1.10.**

IPv4 utiliza cuatro valores decimales separados por puntos, cada uno entre 0 y 255.

### PREGUNTA 5
**Respuesta: B. Máscara de subred.**

La máscara permite diferenciar los bits de red de los bits de host.

### PREGUNTA 6
**Respuesta: A. 192.168.5.**

Con una máscara 255.255.255.0, los primeros tres octetos corresponden a la porción de red.

La dirección completa de red es 192.168.5.0/24.

### PREGUNTA 7
**Respuesta: B. Pertenecen a la misma red IP.**

Ambas computadoras pertenecen a la red 192.168.1.0/24.

### PREGUNTA 8
**Respuesta: B. Router.**

El router permite encaminar paquetes entre diferentes redes.

### PREGUNTA 9
**Respuesta: A, B y C.**

IPv4 utiliza 32 bits organizados en cuatro octetos de ocho bits cada uno.

### PREGUNTA 10
**Respuesta: B. Falso.**

La porción de red depende de la máscara de subred. No siempre corresponde a los primeros tres octetos.

---

**PUNTAJE FINAL: ____ / 10**

# CONCEPTOS QUE DEBES DOMINAR ANTES DEL MÓDULO 9

- Función de una dirección IPv4.
- Diferencia entre IP y NIC.
- Longitud de 32 bits.
- Cuatro octetos de ocho bits.
- Notación decimal con puntos.
- Valores válidos de un octeto.
- Porción de red y porción de host.
- Función de la máscara de subred.
- Significado básico del prefijo /24.
- Diferencia entre hosts de la misma red y de redes diferentes.
- Función del enrutamiento.
