
# CISCO NETWORKING BASICS
## MÓDULO 10 — FORMATOS Y REGLAS DE DIRECCIONAMIENTO IPv6

**Objetivo:** Comprender la necesidad de IPv6, sus mecanismos de coexistencia con IPv4, el sistema hexadecimal y las reglas para representar y comprimir direcciones IPv6.

---

# 10.1 — PROBLEMAS CON IPv4

## 10.1.1 — LA NECESIDAD DE IPv6

### ¿Qué es IPv6?

**IPv6 (Internet Protocol version 6)** es la versión del Protocolo de Internet diseñada para suceder a IPv4.

Su principal característica es que utiliza direcciones de **128 bits**, mientras que IPv4 utiliza 32 bits.

### ¿Por qué se creó IPv6?

La principal razón fue el **agotamiento del espacio de direcciones IPv4**.

Cada vez existen más dispositivos conectados a Internet:

- Computadoras.
- Smartphones.
- Servidores.
- Cámaras inteligentes.
- Automóviles conectados.
- Sensores IoT.
- Electrodomésticos inteligentes.

IPv4 no dispone de suficientes direcciones públicas para cubrir indefinidamente este crecimiento.

### Comparación entre IPv4 e IPv6

| Característica | IPv4 | IPv6 |
|---|---|---|
| Longitud | 32 bits | 128 bits |
| Representación | Decimal | Hexadecimal |
| Ejemplo | 192.168.1.10 | 2001:db8::1 |
| Cantidad teórica | Aproximadamente 4 300 millones | Aproximadamente 3.4 × 10^38 |

### ¿Cuántas direcciones permite IPv6?

IPv6 permite:

**2^128 direcciones posibles.**

Esto representa aproximadamente:

**340 seguido de 36 ceros.**

Es un espacio muchísimo mayor que el de IPv4.

### Mejoras adicionales

IPv6 no solo aumenta la cantidad de direcciones.

También incorpora mejoras en el funcionamiento de las redes.

Por ejemplo, **ICMPv6** incorpora funciones relacionadas con:

- Resolución de direcciones.
- Descubrimiento de dispositivos vecinos.
- Configuración automática de direcciones.

### ¿Qué relación tiene IPv6 con IoT?

**IoT (Internet of Things)** significa Internet de las Cosas.

Permite conectar objetos físicos a redes para intercambiar información.

**Ejemplo:**

Sensor de temperatura → Red → Servidor

El crecimiento de dispositivos IoT es una de las razones por las que se necesita un espacio de direccionamiento mayor.

**IMPORTANTE:**

IPv6 fue desarrollado principalmente debido al agotamiento del espacio de direcciones IPv4 y también incorpora mejoras en los protocolos de comunicación.

---

## 10.1.2 — COEXISTENCIA DE IPv4 E IPv6

### ¿IPv6 reemplazó completamente a IPv4?

**No.**

Ambos protocolos pueden coexistir mientras las redes realizan la transición hacia IPv6.

Cisco presenta tres mecanismos principales de transición:

1. **Doble pila (Dual Stack).**
2. **Tunelización (Tunneling).**
3. **Traducción (Translation).**

---

### 1. DOBLE PILA (DUAL STACK)

### ¿Qué es?

**Dual Stack** permite que un dispositivo utilice simultáneamente IPv4 e IPv6.

Esto significa que el dispositivo puede comunicarse utilizando cualquiera de los dos protocolos.

### ¿Cómo funciona?

Un mismo dispositivo mantiene configuraciones de IPv4 e IPv6.

**Ejemplo:**

Computadora:

IPv4: 192.168.1.10

IPv6: 2001:db8::10

La computadora puede utilizar IPv4 o IPv6 según la conectividad y el servicio disponible.

**PARA RECORDAR:**

Dual Stack = IPv4 e IPv6 funcionando simultáneamente.

---

### 2. TUNELIZACIÓN (TUNNELING)

### ¿Qué es?

La **tunelización** permite transportar paquetes IPv6 a través de una infraestructura IPv4.

### ¿Cómo funciona?

1. Se genera un paquete IPv6.
2. El paquete IPv6 se encapsula dentro de un paquete IPv4.
3. El paquete atraviesa la red IPv4.
4. En el extremo correspondiente se retira la encapsulación.
5. El paquete IPv6 continúa su recorrido.

### Ejemplo

Red IPv6 A → Red IPv4 → Red IPv6 B

**IMPORTANTE:**

Tunelización = transportar IPv6 dentro de IPv4.

No significa convertir una dirección IPv6 en una IPv4.

---

### 3. TRADUCCIÓN (TRANSLATION)

### ¿Qué es NAT64?

**NAT64 (Network Address Translation 64)** permite la comunicación entre dispositivos que utilizan IPv6 y servicios que utilizan IPv4, mediante un mecanismo de traducción.

### ¿Cómo funciona?

1. Un dispositivo IPv6 necesita comunicarse con un destino IPv4.
2. Un traductor NAT64 procesa los paquetes.
3. Se realiza la traducción correspondiente entre IPv6 e IPv4.
4. Los dispositivos pueden intercambiar información mediante esa infraestructura.

**PARA RECORDAR:**

- Dual Stack = ambos protocolos simultáneamente.
- Tunneling = IPv6 encapsulado dentro de IPv4.
- NAT64 = traducción entre IPv6 e IPv4.

### Comparación

| Técnica | Función |
|---|---|
| Doble pila | Utilizar IPv4 e IPv6 simultáneamente. |
| Tunelización | Transportar IPv6 por una red IPv4. |
| Traducción | Permitir comunicación entre IPv6 e IPv4. |

**IDEA CLAVE:**

El objetivo a largo plazo es utilizar comunicaciones IPv6 nativas de extremo a extremo cuando sea posible.

---

# 10.2 — ASIGNACIÓN Y REPRESENTACIÓN DE DIRECCIONES IPv6

## 10.2.1 — SISTEMA DE NÚMEROS HEXADECIMALES

### ¿Qué es el sistema hexadecimal?

El **sistema hexadecimal** es un sistema de numeración de base 16.

Utiliza los siguientes símbolos:

0 1 2 3 4 5 6 7 8 9 A B C D E F

### Valores hexadecimales

| Hexadecimal | Decimal |
|---|---|
| 0 | 0 |
| 1 | 1 |
| 2 | 2 |
| 3 | 3 |
| 4 | 4 |
| 5 | 5 |
| 6 | 6 |
| 7 | 7 |
| 8 | 8 |
| 9 | 9 |
| A | 10 |
| B | 11 |
| C | 12 |
| D | 13 |
| E | 14 |
| F | 15 |

### ¿Por qué se utiliza hexadecimal?

Porque permite representar direcciones IPv6 de 128 bits de una forma más compacta y legible que escribir todos sus bits.

**IMPORTANTE:**

Cada dígito hexadecimal representa **4 bits**.

---

## 10.2.2 — FORMATOS DE DIRECCIONAMIENTO IPv6

### ¿Cuántos bits tiene IPv6?

Una dirección IPv6 tiene:

**128 bits.**

Se organiza en:

**8 hextetos de 16 bits cada uno.**

### ¿Qué es un hexteto?

Un **hexteto** es un grupo de 16 bits, representado mediante cuatro dígitos hexadecimales.

### Estructura IPv6

XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XXXX

Cada grupo representa 16 bits.

### Cálculo

8 hextetos × 16 bits = 128 bits.

Cada hexteto:

4 dígitos hexadecimales × 4 bits = 16 bits.

### Ejemplo de IPv6

fe80:0000:0000:0000:0123:4567:89ab:cdef

Esta dirección contiene:

- 8 hextetos.
- 32 dígitos hexadecimales.
- 128 bits.

### ¿IPv6 distingue mayúsculas y minúsculas?

**No.**

Las siguientes representaciones corresponden al mismo valor:

ABCD = abcd

Por ejemplo:

2001:DB8::1

2001:db8::1

Ambas representan la misma dirección IPv6.

**IMPORTANTE:**

- IPv4 = 4 octetos.
- IPv6 = 8 hextetos.
- Octeto = 8 bits.
- Hexteto = 16 bits.
- IPv6 = 128 bits.

---

## 10.2.4 — REGLA 1: OMITIR CEROS INICIALES

### ¿En qué consiste?

La primera regla para abreviar direcciones IPv6 permite **eliminar los ceros que aparecen al inicio de un hexteto**.

Solo se eliminan los ceros que están a la izquierda.

### Ejemplos de Cisco

| Forma original | Forma abreviada |
|---|---|
| 01ab | 1ab |
| 09f0 | 9f0 |
| 0a00 | a00 |
| 00ab | ab |
| 0001 | 1 |
| 0000 | 0 |

### Ejemplo completo

**Dirección original:**

2001:0db8:0000:0000:0000:0000:0000:0001

**Después de omitir ceros iniciales:**

2001:db8:0:0:0:0:0:1

### ¿Qué ceros no se pueden eliminar?

**No se deben eliminar los ceros finales de un hexteto.**

Ejemplo:

0a00 → a00

No se puede convertir en:

a

Porque cambiaría su valor.

### ¿Por qué?

Los siguientes hextetos no representan el mismo número:

- 0abc
- abc0

Después de eliminar ceros iniciales:

0abc → abc

Pero abc0 no puede convertirse en abc.

**PARA RECORDAR:**

Regla 1 = eliminar ceros iniciales, nunca ceros finales.

---

## 10.2.5 — REGLA 2: DOS PUNTOS DOBLES (::)

### ¿En qué consiste?

Los **dos puntos dobles (::)** permiten reemplazar una secuencia continua de uno o más hextetos que contienen exclusivamente ceros.

### Ejemplo

**Dirección original:**

2001:0db8:0000:0000:0000:0000:0000:0001

### Paso 1 — Omitir ceros iniciales

2001:db8:0:0:0:0:0:1

### Paso 2 — Comprimir los hextetos consecutivos con valor cero

**Resultado:**

2001:db8::1

Las tres representaciones anteriores corresponden a la misma dirección IPv6.

### ¿Cuántas veces se puede utilizar ::?

**Solamente una vez por dirección IPv6.**

### ¿Por qué?

Porque utilizar :: dos veces produciría ambigüedad sobre cuántos hextetos de ceros representa cada abreviatura.

### Ejemplo incorrecto

2001:db8::abcd::1234

**INCORRECTO.**

Contiene dos apariciones de ::.

### ¿Qué ocurre cuando hay varios grupos de ceros?

Se recomienda comprimir la secuencia continua más larga de hextetos con valor cero.

Si existen secuencias de la misma longitud, se utiliza la primera.

### Ejemplo

**Dirección original:**

2001:0000:0000:abcd:0000:0000:0000:0001

Primero se eliminan los ceros iniciales:

2001:0:0:abcd:0:0:0:1

Hay dos secuencias de ceros:

- Primera: 2 hextetos.
- Segunda: 3 hextetos.

Se comprime la segunda porque es más larga.

**Resultado:**

2001:0:0:abcd::1

### Reglas para memorizar

1. Los ceros iniciales pueden eliminarse.
2. Los ceros finales de un hexteto no se eliminan.
3. :: representa una secuencia de hextetos completos de ceros.
4. :: se utiliza como máximo una vez por dirección.
5. Se comprime preferentemente la secuencia más larga de ceros.
6. Si hay empate, se comprime la primera secuencia.

---

# EJEMPLOS RESUELTOS — COMPRESIÓN IPv6

## EJEMPLO 1

Dirección:

2001:0db8:0000:0000:0000:0000:0000:0005

**Paso 1:**

2001:db8:0:0:0:0:0:5

**Paso 2:**

2001:db8::5

**Respuesta final:**

2001:db8::5

---

## EJEMPLO 2

Dirección:

fe80:0000:0000:0000:1234:0000:0000:0001

**Paso 1:**

fe80:0:0:0:1234:0:0:1

**Paso 2:**

fe80::1234:0:0:1

**Respuesta final:**

fe80::1234:0:0:1

---

## EJEMPLO 3

Dirección:

2001:0db8:0000:0000:abcd:0000:0000:0001

**Paso 1:**

2001:db8:0:0:abcd:0:0:1

**Paso 2:**

2001:db8::abcd:0:0:1

**Respuesta final:**

2001:db8::abcd:0:0:1

Se comprime la primera secuencia porque ambas tienen dos hextetos de ceros.

---

# ¿CÓMO EXPANDIR UNA DIRECCIÓN IPv6?

Expandir significa convertir una dirección abreviada nuevamente en ocho hextetos de cuatro dígitos cada uno.

### Ejemplo

Dirección abreviada:

2001:db8::1

### Paso 1 — Contar los hextetos visibles

- 2001
- db8
- 1

Hay tres hextetos visibles.

### Paso 2 — Calcular cuántos faltan

8 - 3 = 5 hextetos.

Por lo tanto, :: representa cinco hextetos de ceros.

### Paso 3 — Completar

2001:0db8:0000:0000:0000:0000:0000:0001

**PARA RECORDAR:**

Una dirección IPv6 completa siempre tiene ocho hextetos.

---

# COMPARACIÓN IPv4 VS IPv6

| Característica | IPv4 | IPv6 |
|---|---|---|
| Bits | 32 | 128 |
| Grupos | 4 octetos | 8 hextetos |
| Bits por grupo | 8 | 16 |
| Sistema | Decimal | Hexadecimal |
| Separador | Punto | Dos puntos |
| Ejemplo | 192.168.1.1 | 2001:db8::1 |
| Compresión de ceros | No utiliza :: | Permite :: una vez |

---

# GLOSARIO — MÓDULO 10

| Término | Significado |
|---|---|
| IPv4 | Protocolo de Internet versión 4. |
| IPv6 | Protocolo de Internet versión 6. |
| Hexadecimal | Sistema numérico de base 16. |
| Hexteto | Grupo de 16 bits de IPv6. |
| Octeto | Grupo de 8 bits. |
| Dual Stack | Uso simultáneo de IPv4 e IPv6. |
| Tunneling | Transporte de IPv6 encapsulado en IPv4. |
| NAT64 | Traducción para comunicación entre IPv6 e IPv4. |
| ICMPv6 | Protocolo de mensajes de control utilizado con IPv6. |
| IoT | Internet de las Cosas. |
| IETF | Internet Engineering Task Force. |
| Compresión IPv6 | Reducción de la representación textual de una dirección. |
| Ceros iniciales | Ceros situados a la izquierda de un hexteto. |
| Doble dos puntos (::) | Abreviación para hextetos consecutivos de ceros. |

---

# RESUMEN GENERAL — MÓDULO 10

1. IPv6 fue desarrollado para afrontar el agotamiento de direcciones IPv4.
2. IPv4 utiliza direcciones de 32 bits.
3. IPv6 utiliza direcciones de 128 bits.
4. IPv6 permite aproximadamente 3.4 × 10^38 direcciones.
5. IPv4 e IPv6 pueden coexistir.
6. Dual Stack permite utilizar ambos protocolos simultáneamente.
7. Tunneling permite transportar IPv6 a través de IPv4.
8. NAT64 permite comunicación mediante traducción entre IPv6 e IPv4.
9. IPv6 utiliza el sistema hexadecimal.
10. El sistema hexadecimal utiliza los dígitos 0-9 y las letras A-F.
11. Cada dígito hexadecimal representa cuatro bits.
12. Una dirección IPv6 tiene ocho hextetos.
13. Cada hexteto contiene 16 bits.
14. Un hexteto completo contiene cuatro dígitos hexadecimales.
15. IPv6 no distingue entre mayúsculas y minúsculas.
16. La primera regla de compresión elimina los ceros iniciales.
17. La segunda regla utiliza :: para comprimir hextetos consecutivos de ceros.
18. :: solo puede aparecer una vez por dirección.
19. Se recomienda comprimir la secuencia de ceros más larga.
20. Si existen dos secuencias de igual longitud, se comprime la primera.

**IDEA FINAL:**

IPv6 amplía enormemente el espacio de direccionamiento de Internet. Sus direcciones utilizan 128 bits expresados en hexadecimal y pueden abreviarse mediante dos reglas: eliminar ceros iniciales y comprimir hextetos consecutivos de ceros con ::.

---

# CUESTIONARIO — MÓDULO 10

**Total:** 10 preguntas  
**Puntaje máximo:** 10 puntos

**Instrucciones:** Selecciona la respuesta correcta. Las alternativas no están marcadas. Revisa el solucionario únicamente al terminar.

## PREGUNTA 1

¿Cuál fue la principal razón para desarrollar IPv6?

- [ ] A. Eliminar completamente Ethernet.
- [ ] B. Resolver el agotamiento de direcciones IPv4.
- [ ] C. Reemplazar las conexiones Wi-Fi.
- [ ] D. Eliminar los routers.

## PREGUNTA 2

¿Cuántos bits tiene una dirección IPv6?

- [ ] A. 32 bits.
- [ ] B. 64 bits.
- [ ] C. 128 bits.
- [ ] D. 256 bits.

## PREGUNTA 3

¿Qué mecanismo permite ejecutar IPv4 e IPv6 simultáneamente en un mismo dispositivo?

- [ ] A. NAT64.
- [ ] B. Tunelización.
- [ ] C. Dual Stack.
- [ ] D. DHCP.

## PREGUNTA 4

¿Qué técnica permite transportar un paquete IPv6 encapsulado dentro de un paquete IPv4?

- [ ] A. Tunneling.
- [ ] B. Multicast.
- [ ] C. NAT64.
- [ ] D. Broadcast.

## PREGUNTA 5

¿Cuál es la función principal de NAT64?

- [ ] A. Convertir señales eléctricas en ópticas.
- [ ] B. Permitir comunicación mediante traducción entre IPv6 e IPv4.
- [ ] C. Asignar nombres a redes Wi-Fi.
- [ ] D. Aumentar el ancho de banda de Ethernet.

## PREGUNTA 6

¿Cuántos hextetos contiene una dirección IPv6 completa?

- [ ] A. 4.
- [ ] B. 6.
- [ ] C. 8.
- [ ] D. 16.

## PREGUNTA 7

¿Cuál es la abreviación correcta del hexteto 00ab?

- [ ] A. 0ab0
- [ ] B. ab
- [ ] C. a
- [ ] D. ab0

## PREGUNTA 8

¿Cuál es la representación comprimida recomendada de la siguiente dirección?

2001:0db8:0000:0000:0000:0000:0000:0001

- [ ] A. 2001:db8::1
- [ ] B. 2001::db8::1
- [ ] C. 2001:db8:1
- [ ] D. 2001:db8::0::1

## PREGUNTA 9

¿Cuántas veces puede utilizarse la abreviación :: dentro de una dirección IPv6?

- [ ] A. Una sola vez.
- [ ] B. Dos veces.
- [ ] C. Cuatro veces.
- [ ] D. Ocho veces.

## PREGUNTA 10

Si una dirección IPv6 contiene dos secuencias de hextetos de ceros de la misma longitud, ¿cuál debe comprimirse según la recomendación presentada por Cisco?

- [ ] A. La última.
- [ ] B. La primera.
- [ ] C. Ambas mediante dos apariciones de ::.
- [ ] D. Ninguna, porque no se permite comprimir.

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
**Respuesta: B. Resolver el agotamiento de direcciones IPv4.**

IPv6 se desarrolló principalmente para proporcionar un espacio de direccionamiento mucho mayor.

### PREGUNTA 2
**Respuesta: C. 128 bits.**

Una dirección IPv6 contiene 128 bits organizados en ocho hextetos.

### PREGUNTA 3
**Respuesta: C. Dual Stack.**

Dual Stack permite que IPv4 e IPv6 funcionen simultáneamente en un dispositivo.

### PREGUNTA 4
**Respuesta: A. Tunneling.**

La tunelización encapsula paquetes IPv6 dentro de paquetes IPv4 para transportarlos por una infraestructura IPv4.

### PREGUNTA 5
**Respuesta: B. Permitir comunicación mediante traducción entre IPv6 e IPv4.**

NAT64 permite que dispositivos IPv6 se comuniquen con servicios IPv4 mediante traducción.

### PREGUNTA 6
**Respuesta: C. 8.**

Una dirección IPv6 completa contiene ocho hextetos, cada uno de 16 bits.

### PREGUNTA 7
**Respuesta: B. ab.**

La regla 1 permite eliminar los ceros iniciales:

00ab → ab

### PREGUNTA 8
**Respuesta: A. 2001:db8::1.**

Primero se eliminan los ceros iniciales y luego se comprime la secuencia continua de hextetos con valor cero.

### PREGUNTA 9
**Respuesta: A. Una sola vez.**

Utilizar :: más de una vez generaría ambigüedad al reconstruir la dirección original.

### PREGUNTA 10
**Respuesta: B. La primera.**

Si las secuencias de ceros tienen igual longitud, la representación recomendada utiliza :: en la primera secuencia.

---

**PUNTAJE FINAL: ____ / 10**

# CONCEPTOS QUE DEBES DOMINAR ANTES DEL MÓDULO 11

- Diferencias entre IPv4 e IPv6.
- Razones de la transición hacia IPv6.
- Dual Stack, Tunneling y NAT64.
- Sistema hexadecimal.
- Longitud de 128 bits.
- Hextetos de 16 bits.
- Formato completo de una dirección IPv6.
- Regla de omitir ceros iniciales.
- Regla de compresión con ::.
- Identificación de direcciones IPv6 válidas e inválidas.
- Expansión y compresión de direcciones IPv6.
