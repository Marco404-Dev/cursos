
# Módulo 3: Sistemas de Numeración

**Curso:** Cisco Networking Academy — Dispositivos de Red y Configuración Inicial

## 1. Sistemas de numeración

Los dispositivos de red utilizan números binarios para representar y procesar direcciones IP.

Existen tres sistemas importantes en redes:

| Sistema | Base | Símbolos | Uso en redes |
|---|---|---|---|
| Decimal | 10 | 0 al 9 | Representación habitual de IPv4. |
| Binario | 2 | 0 y 1 | Representación interna de direcciones y datos. |
| Hexadecimal | 16 | 0 al 9 y A al F | Representación de IPv6 y direcciones MAC. |

### Conceptos importantes

- **Bit:** unidad de información que puede valer 0 o 1.
- **Byte:** conjunto de 8 bits.
- **Octeto:** grupo de 8 bits.
- **IPv4:** dirección de 32 bits.
- **IPv6:** dirección de 128 bits.

## 2. Sistema binario

El sistema binario utiliza solamente dos valores:

- `0`: cero.
- `1`: uno.

Cada posición representa una potencia de 2.

### Tabla de valores binarios

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|---|---|---|---|---|---|---|---|
| 2⁷ | 2⁶ | 2⁵ | 2⁴ | 2³ | 2² | 2¹ | 2⁰ |

**Importante:** Un octeto contiene 8 bits y puede representar valores decimales desde 0 hasta 255.

## 3. Conversión de binario a decimal

Para convertir un número binario a decimal, sumamos los valores de las posiciones que contienen un `1`.

### Ejemplo: 11000000

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|---|---|---|---|---|---|---|---|
| 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |

Sumamos:

128 + 64 = **192**

Por lo tanto:

`11000000₂ = 192₁₀`

### Otro ejemplo: 00001011

Las posiciones que contienen 1 son:

8 + 2 + 1 = **11**

Por lo tanto:

`00001011₂ = 11₁₀`

## 4. Conversión de decimal a binario

Para convertir un número decimal a binario, comparamos su valor con las posiciones:

`128 - 64 - 32 - 16 - 8 - 4 - 2 - 1`

**Regla:**

- Si el número es mayor o igual al valor de la posición, colocamos `1` y restamos ese valor.
- Si es menor, colocamos `0`.
- Continuamos hasta completar los 8 bits.

### Ejemplo: convertir 168 a binario

| Posición | Comparación | Bit | Resto |
|---|---|---|---|
| 128 | 168 >= 128 | 1 | 40 |
| 64 | 40 < 64 | 0 | 40 |
| 32 | 40 >= 32 | 1 | 8 |
| 16 | 8 < 16 | 0 | 8 |
| 8 | 8 >= 8 | 1 | 0 |
| 4 | 0 < 4 | 0 | 0 |
| 2 | 0 < 2 | 0 | 0 |
| 1 | 0 < 1 | 0 | 0 |

Resultado:

`168₁₀ = 10101000₂`

**Comprobación:**

128 + 32 + 8 = 168

## 5. Direcciones IPv4 en binario

Una dirección IPv4 tiene:

- 32 bits.
- 4 octetos.
- 8 bits por octeto.
- Valores decimales de 0 a 255 en cada octeto.

### Ejemplo: 192.168.10.11

Convertimos cada octeto:

| Decimal | Operación | Binario |
|---|---|---|
| 192 | 128 + 64 | 11000000 |
| 168 | 128 + 32 + 8 | 10101000 |
| 10 | 8 + 2 | 00001010 |
| 11 | 8 + 2 + 1 | 00001011 |

**Resultado completo:**

Decimal:

`192.168.10.11`

Binario:

`11000000.10101000.00001010.00001011`

### Otro ejemplo

IPv4 de una PC:

`192.168.10.10`

Representación binaria:

`11000000.10101000.00001010.00001010`

Gateway predeterminado:

`192.168.10.1`

Representación binaria:

`11000000.10101000.00001010.00000001`

**Importante:** Los puntos separan los octetos. No forman parte de los 32 bits.

## 6. Sistema hexadecimal

El sistema hexadecimal utiliza base 16.

Está formado por:

- Números del 0 al 9.
- Letras de la A a la F.

Las letras representan valores del 10 al 15.

### Tabla de equivalencias

| Decimal | Binario | Hexadecimal |
|---|---|---|
| 0 | 0000 | 0 |
| 1 | 0001 | 1 |
| 2 | 0010 | 2 |
| 3 | 0011 | 3 |
| 4 | 0100 | 4 |
| 5 | 0101 | 5 |
| 6 | 0110 | 6 |
| 7 | 0111 | 7 |
| 8 | 1000 | 8 |
| 9 | 1001 | 9 |
| 10 | 1010 | A |
| 11 | 1011 | B |
| 12 | 1100 | C |
| 13 | 1101 | D |
| 14 | 1110 | E |
| 15 | 1111 | F |

**Regla fundamental:**

4 bits = 1 dígito hexadecimal.

### Ejemplo: binario a hexadecimal

Convertir:

`10101111`

Dividimos en grupos de cuatro bits:

`1010 1111`

- `1010` = A
- `1111` = F

Resultado:

`10101111₂ = AF₁₆`

### Ejemplo: hexadecimal a decimal

Convertir `2F`:

- 2 × 16 = 32
- F = 15

32 + 15 = **47**

Por lo tanto:

`2F₁₆ = 47₁₀`

## 7. Direcciones IPv6 y hexadecimal

IPv6 utiliza direcciones de 128 bits representadas mediante hexadecimal.

### Características

- IPv6 contiene 128 bits.
- Utiliza 8 grupos de 16 bits.
- Cada grupo contiene 4 dígitos hexadecimales en su formato completo.
- Cada grupo se denomina informalmente **hexteto**.
- Los grupos se separan mediante dos puntos (`:`).
- Las letras pueden escribirse en mayúsculas o minúsculas.

### Ejemplo de IPv6

`2001:0DB8:0000:0000:0000:0000:0000:0001`

Esta dirección contiene:

- 8 hextetos.
- 16 bits por hexteto.
- 128 bits en total.

### Forma abreviada

La dirección anterior puede escribirse como:

`2001:DB8::1`

Los ceros consecutivos pueden comprimirse utilizando `::` una sola vez por dirección.

**Importante:**

- IPv4 se representa habitualmente en decimal.
- IPv6 se representa en hexadecimal.
- Las direcciones MAC Ethernet también se representan en hexadecimal.

## 8. Comparación entre IPv4 e IPv6

| Característica | IPv4 | IPv6 |
|---|---|---|
| Longitud | 32 bits | 128 bits |
| Representación habitual | Decimal | Hexadecimal |
| Grupos | 4 octetos | 8 hextetos |
| Separador | Punto (`.`) | Dos puntos (`:`) |
| Ejemplo | 192.168.1.10 | 2001:DB8::1 |

## 9. Fórmulas importantes

- 1 byte = 8 bits.
- 1 octeto = 8 bits.
- 1 dígito hexadecimal = 4 bits.
- IPv4 = 4 × 8 = 32 bits.
- IPv6 = 8 × 16 = 128 bits.
- Valor máximo de un octeto = 2⁸ - 1 = 255.
- Cantidad de combinaciones de un octeto = 2⁸ = 256.

---

# 10 preguntas de repaso — Módulo 3

### 1. ¿Qué sistema de numeración utilizan los dispositivos de red para representar internamente la información?

A) Decimal.  
B) Hexadecimal exclusivamente.  
C) Binario.  
D) Octal.

<details>
<summary>Ver respuesta</summary>

✅ **C) Binario.**

Los dispositivos utilizan bits, representados mediante 0 y 1.

</details>

### 2. ¿Cuántos bits tiene una dirección IPv4?

A) 16 bits.  
B) 32 bits.  
C) 64 bits.  
D) 128 bits.

<details>
<summary>Ver respuesta</summary>

✅ **B) 32 bits.**

IPv4 contiene cuatro octetos de ocho bits cada uno.

4 × 8 = 32 bits.

</details>

### 3. ¿Cuál es el valor decimal del número binario 11000000?

A) 128.  
B) 168.  
C) 224.  
D) 192.

<details>
<summary>Ver respuesta</summary>

✅ **D) 192.**

Los bits activos representan:

128 + 64 = 192.

</details>

### 4. ¿Cuál es la representación binaria de 168?

A) 10101000.  
B) 11000000.  
C) 10001000.  
D) 11101000.

<details>
<summary>Ver respuesta</summary>

✅ **A) 10101000.**

168 = 128 + 32 + 8.

Las posiciones correspondientes contienen 1.

</details>

### 5. ¿Cuál es el valor decimal del binario 00001011?

A) 10.  
B) 9.  
C) 11.  
D) 12.

<details>
<summary>Ver respuesta</summary>

✅ **C) 11.**

8 + 2 + 1 = 11.

</details>

### 6. ¿Cuál es la representación binaria de la dirección IPv4 192.168.10.11?

A) 11000000.10101000.00001010.00001010  
B) 11000000.10101000.00001010.00001011  
C) 11000000.10100000.00001010.00001011  
D) 11000000.10101000.00001011.00001010

<details>
<summary>Ver respuesta</summary>

✅ **B) 11000000.10101000.00001010.00001011**

Cada octeto convertido:

- 192 = 11000000
- 168 = 10101000
- 10 = 00001010
- 11 = 00001011

</details>

### 7. ¿Qué valor hexadecimal corresponde al número decimal 15?

A) A.  
B) D.  
C) E.  
D) F.

<details>
<summary>Ver respuesta</summary>

✅ **D) F.**

En hexadecimal:

A = 10, B = 11, C = 12, D = 13, E = 14 y F = 15.

</details>

### 8. ¿Cuántos bits representa un dígito hexadecimal?

A) 4 bits.  
B) 8 bits.  
C) 16 bits.  
D) 32 bits.

<details>
<summary>Ver respuesta</summary>

✅ **A) 4 bits.**

Cuatro bits permiten representar 16 combinaciones, desde 0000 hasta 1111.

</details>

### 9. ¿Cuántos hextetos tiene una dirección IPv6 en su representación completa?

A) 4 hextetos.  
B) 6 hextetos.  
C) 8 hextetos.  
D) 16 hextetos.

<details>
<summary>Ver respuesta</summary>

✅ **C) 8 hextetos.**

Cada hexteto tiene 16 bits.

8 × 16 = 128 bits.

</details>

### 10. ¿Cuál es la representación hexadecimal del número binario 10101111?

A) A1.  
B) AF.  
C) BF.  
D) FA.

<details>
<summary>Ver respuesta</summary>

✅ **B) AF.**

Dividimos en grupos de cuatro bits:

1010 = A

1111 = F

Resultado: AF.

</details>

---

**Fin del Módulo 3 — Sistemas de Numeración**
