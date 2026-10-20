
# Módulo 6: Estructura de la Dirección IPv4

**Curso:** Cisco Networking Academy — Dispositivos de Red y Configuración Inicial

## 1. Estructura de una dirección IPv4

Una dirección IPv4 tiene **32 bits**, divididos en cuatro octetos de 8 bits.

Está formada por dos partes:

- **Porción de red:** identifica la red a la que pertenece el dispositivo.
- **Porción de host:** identifica al dispositivo dentro de esa red.

### Ejemplo

Dirección: `192.168.10.10/24`

| Porción de red | Porción de host |
|---|---|
| 192.168.10 | 10 |

En este ejemplo:

- Dirección de red: `192.168.10.0`
- Dirección del host: `192.168.10.10`
- Máscara: `255.255.255.0`

**Importante:** Los dispositivos de la misma subred comparten los bits de red, pero deben tener direcciones de host diferentes.

## 2. Máscara de subred

La máscara de subred permite identificar qué bits de una dirección IPv4 corresponden a la red y cuáles al host.

### Ejemplo

IPv4: `192.168.10.10`

Máscara: `255.255.255.0`

| Octeto | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| IP | 192 | 168 | 10 | 10 |
| Máscara | 255 | 255 | 255 | 0 |

En binario:

```text
IP:       11000000.10101000.00001010.00001010
Máscara:  11111111.11111111.11111111.00000000
```

La máscara indica:

- Los bits en `1` corresponden a la red.
- Los bits en `0` corresponden al host.

**Recuerda:** La máscara no almacena la dirección de red; indica cuáles son sus bits.

## 3. Longitud del prefijo (CIDR)

La longitud del prefijo representa la cantidad de bits establecidos en `1` dentro de la máscara.

Se escribe utilizando una barra `/` seguida de un número.

### Ejemplo

`192.168.10.10/24`

Significa:

- 24 bits para la red.
- 8 bits para el host.
- Máscara: `255.255.255.0`.

### Máscaras frecuentes

| Prefijo | Máscara | Bits de host |
|---|---|---|
| /8 | 255.0.0.0 | 24 |
| /16 | 255.255.0.0 | 16 |
| /24 | 255.255.255.0 | 8 |
| /25 | 255.255.255.128 | 7 |
| /26 | 255.255.255.192 | 6 |
| /27 | 255.255.255.224 | 5 |
| /28 | 255.255.255.240 | 4 |
| /29 | 255.255.255.248 | 3 |
| /30 | 255.255.255.252 | 2 |

**Regla:**

`Bits de host = 32 - prefijo`

Ejemplo:

`/26 → 32 - 26 = 6 bits de host`

## 4. Operación lógica AND

La operación AND permite calcular la dirección de red utilizando una dirección IPv4 y su máscara.

### Tabla AND

| Bit A | Bit B | Resultado |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

**Regla fundamental:** Solo `1 AND 1` produce `1`. Las demás combinaciones producen `0`.

## 5. Calcular una dirección de red mediante AND

### Ejemplo: 192.168.10.10/24

Tenemos:

- IP: `192.168.10.10`
- Máscara: `255.255.255.0`

### Paso 1: Convertir a binario

```text
IP:       11000000.10101000.00001010.00001010
Máscara:  11111111.11111111.11111111.00000000
```

### Paso 2: Aplicar AND bit por bit

```text
IP:       11000000.10101000.00001010.00001010
Máscara:  11111111.11111111.11111111.00000000
          -----------------------------------
Red:      11000000.10101000.00001010.00000000
```

### Paso 3: Convertir el resultado a decimal

`192.168.10.0`

**Resultado:**

La dirección de red es `192.168.10.0/24`.

## 6. Ejemplo con máscara /26

Supongamos:

- IP: `192.168.1.70`
- Máscara: `255.255.255.192`
- Prefijo: `/26`

### Paso 1: Convertir el último octeto

```text
70  = 01000110
192 = 11000000
```

### Paso 2: Aplicar AND

```text
IP:       01000110
Máscara:  11000000
          --------
Red:      01000000
```

`01000000` equivale a 64.

### Resultado

- Dirección de red: `192.168.1.64/26`
- Máscara: `255.255.255.192`
- Broadcast: `192.168.1.127`
- Hosts utilizables: `192.168.1.65` a `192.168.1.126`

**Importante:** En una subred /26 tradicional hay 64 direcciones totales y 62 direcciones de host utilizables.

## 7. Fórmulas importantes

### Bits de red y host

```text
Bits de host = 32 - prefijo
```

### Direcciones totales

```text
Direcciones totales = 2^(bits de host)
```

### Hosts utilizables

```text
Hosts utilizables = 2^(bits de host) - 2
```

La última fórmula se aplica a subredes IPv4 convencionales. Las subredes `/31` y `/32` tienen usos especiales.

### Ejemplos

| Prefijo | Direcciones totales | Hosts utilizables |
|---|---|---|
| /24 | 256 | 254 |
| /25 | 128 | 126 |
| /26 | 64 | 62 |
| /27 | 32 | 30 |
| /28 | 16 | 14 |
| /29 | 8 | 6 |
| /30 | 4 | 2 |

**Recuerda:** En las subredes convencionales se reservan la primera dirección para identificar la red y la última para broadcast.

## 8. Conceptos importantes

| Concepto | Significado |
|---|---|
| Dirección IPv4 | Identifica una interfaz dentro de una red IP. |
| Porción de red | Identifica la subred. |
| Porción de host | Identifica un host dentro de la subred. |
| Máscara de subred | Permite distinguir los bits de red y host. |
| Prefijo | Cantidad de bits de red establecidos en 1 en la máscara. |
| AND lógico | Operación utilizada para calcular la dirección de red. |
| Dirección de red | Identifica una subred. |
| Broadcast | Dirección utilizada para enviar tráfico a todos los hosts de una subred IPv4. |

---

# 10 preguntas de repaso — Módulo 6

### 1. ¿Cuántos bits tiene una dirección IPv4?

A) 16 bits.  
B) 32 bits.  
C) 64 bits.  
D) 128 bits.

<details>
<summary>Ver respuesta</summary>

✅ **B) 32 bits.**

Una dirección IPv4 está formada por cuatro octetos de 8 bits.

4 × 8 = 32 bits.

</details>

### 2. ¿Cuál es la función principal de la máscara de subred?

A) Asignar direcciones MAC.  
B) Determinar la velocidad de conexión.  
C) Identificar los bits correspondientes a la red y al host.  
D) Traducir nombres de dominio.

<details>
<summary>Ver respuesta</summary>

✅ **C) Identificar los bits correspondientes a la red y al host.**

Los bits en 1 representan la porción de red y los bits en 0 representan la porción de host.

</details>

### 3. ¿Qué significa el prefijo /24?

A) Que existen 24 bits de red.  
B) Que existen 24 bits de host.  
C) Que la dirección tiene 24 bits en total.  
D) Que existen 24 dispositivos conectados.

<details>
<summary>Ver respuesta</summary>

✅ **A) Que existen 24 bits de red.**

Una dirección IPv4 tiene 32 bits.

32 - 24 = 8 bits de host.

</details>

### 4. ¿Cuál es la máscara correspondiente al prefijo /26?

A) 255.255.255.0  
B) 255.255.255.128  
C) 255.255.255.224  
D) 255.255.255.192

<details>
<summary>Ver respuesta</summary>

✅ **D) 255.255.255.192**

La máscara /26 contiene 26 bits establecidos en 1.

Los últimos dos bits de red del cuarto octeto corresponden a:

128 + 64 = 192.

</details>

### 5. ¿Cuál es el resultado de aplicar AND entre los bits 1 y 0?

A) 1.  
B) 0.  
C) 10.  
D) 11.

<details>
<summary>Ver respuesta</summary>

✅ **B) 0.**

En una operación AND, solamente 1 AND 1 produce 1.

</details>

### 6. ¿Cuál es la dirección de red de 192.168.10.10/24?

A) 192.168.10.255  
B) 192.168.10.1  
C) 192.168.10.0  
D) 192.168.0.0

<details>
<summary>Ver respuesta</summary>

✅ **C) 192.168.10.0**

La máscara /24 mantiene los primeros 24 bits y pone en cero los 8 bits de host.

</details>

### 7. ¿Cuántos bits de host tiene una dirección con prefijo /27?

A) 5 bits.  
B) 6 bits.  
C) 8 bits.  
D) 27 bits.

<details>
<summary>Ver respuesta</summary>

✅ **A) 5 bits.**

32 - 27 = 5 bits de host.

</details>

### 8. ¿Cuántas direcciones totales contiene una subred /28?

A) 8.  
B) 14.  
C) 32.  
D) 16.

<details>
<summary>Ver respuesta</summary>

✅ **D) 16.**

32 - 28 = 4 bits de host.

2⁴ = 16 direcciones totales.

De ellas, 14 son utilizables por hosts en una subred convencional.

</details>

### 9. ¿Cuál es la dirección de red de 192.168.1.70/26?

A) 192.168.1.0  
B) 192.168.1.64  
C) 192.168.1.70  
D) 192.168.1.128

<details>
<summary>Ver respuesta</summary>

✅ **B) 192.168.1.64**

Una máscara /26 genera bloques de 64 direcciones:

- 192.168.1.0 a 192.168.1.63
- 192.168.1.64 a 192.168.1.127
- 192.168.1.128 a 192.168.1.191
- 192.168.1.192 a 192.168.1.255

La IP .70 pertenece a la red 192.168.1.64/26.

</details>

### 10. ¿Cuántos hosts utilizables tiene una subred /30 convencional?

A) 4.  
B) 6.  
C) 2.  
D) 8.

<details>
<summary>Ver respuesta</summary>

✅ **C) 2.**

Una máscara /30 deja 2 bits de host.

2² = 4 direcciones totales.

4 - 2 = 2 hosts utilizables.

</details>

---

**Fin del Módulo 6 — Estructura de la Dirección IPv4**
