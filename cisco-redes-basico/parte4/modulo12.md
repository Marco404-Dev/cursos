
# Módulo 12: Límites de la Red y NAT

## 1. Límites de la red

Una red local (LAN) permite que varios dispositivos se comuniquen entre sí. Sin embargo, para comunicarse con dispositivos de otras redes, necesitan un **router**.

El router conecta diferentes redes y permite que los paquetes de datos lleguen a su destino.

### 1.1 Puerta de enlace predeterminada (Default Gateway)

Es la dirección IP del router que los dispositivos utilizan para comunicarse con otras redes, como Internet.

**Ejemplo:**

| Dispositivo | Dirección IPv4 |
|---|---|
| Router (Gateway) | 192.168.1.1 |
| PC1 | 192.168.1.10 |
| PC2 | 192.168.1.20 |
| Máscara de subred | 255.255.255.0 |

- Si PC1 quiere comunicarse con PC2, puede hacerlo directamente dentro de la red local.
- Si PC1 quiere comunicarse con un servidor de Internet, enviará el paquete al gateway `192.168.1.1`.
- El router se encargará de reenviar el paquete hacia la red de destino.

**Importante:** El gateway predeterminado normalmente es la dirección IP de la interfaz del router conectada a nuestra red local.

### 1.2 ¿Cómo se configura el gateway?

Existen dos formas:

| Método | Explicación |
|---|---|
| Estático | Se configura manualmente la dirección IP del gateway en el dispositivo. |
| Dinámico (DHCP) | El servidor DHCP proporciona automáticamente la dirección del gateway. |

Un router doméstico normalmente funciona como servidor DHCP y proporciona:

- Dirección IPv4 privada.
- Máscara de subred.
- Puerta de enlace predeterminada.
- Dirección del servidor DNS.

### 1.3 Router como límite entre redes

El router inalámbrico normalmente tiene dos lados:

**Red interna (LAN):**
- Conecta dispositivos del hogar o empresa.
- Utiliza direcciones IPv4 privadas.
- El router puede actuar como servidor DHCP.

**Red externa (WAN):**
- Conecta el router con el proveedor de Internet (ISP).
- El router puede recibir su dirección IPv4 mediante DHCP del ISP.
- Esa dirección puede ser pública o privada, dependiendo del proveedor.

**Ejemplo:**

```text
PC (192.168.1.10)
       |
       v
Router
LAN: 192.168.1.1
WAN: IP asignada por el ISP
       |
       v
      ISP
       |
       v
    Internet
```

**Recuerda:** El router permite la comunicación entre redes diferentes.

---

## 2. Funcionamiento de NAT

### 2.1 ¿Qué es NAT?

**NAT (Network Address Translation)** significa Traducción de Direcciones de Red.

Es un mecanismo que permite traducir direcciones IP privadas a direcciones IP públicas y viceversa, según las traducciones configuradas.

Se utiliza principalmente para que los dispositivos de una red privada puedan comunicarse con Internet.

**Ejemplo:**

```text
PC
IP privada: 192.168.1.10
        |
        v
Router con NAT
IP pública: 200.10.10.5
        |
        v
     Internet
```

Cuando el paquete sale hacia Internet, el router traduce la dirección IP privada de origen por una dirección pública.

Cuando llega la respuesta, el router utiliza la información de la traducción para dirigirla al dispositivo correspondiente.

### 2.2 ¿Por qué necesitamos NAT?

Las direcciones IPv4 públicas son limitadas.

Por eso, NAT permite que los dispositivos que utilizan direcciones privadas puedan acceder a redes externas mediante direcciones públicas.

**Importante:** NAT no crea nuevas direcciones IPv4 públicas ni aumenta su cantidad. Permite aprovechar mejor las direcciones disponibles.

### 2.3 Diferencia entre NAT y PAT

| NAT | PAT |
|---|---|
| Traduce direcciones IP. | Traduce direcciones IP y números de puerto. |
| Puede realizar traducciones uno a uno. | Permite que muchos dispositivos compartan una misma IP pública. |
| Es el concepto general de traducción. | Es una modalidad de NAT. |

**Ejemplo de PAT:**

| Dispositivo | IP privada | IP pública compartida |
|---|---|---|
| PC1 | 192.168.1.10 | 200.10.10.5 |
| PC2 | 192.168.1.20 | 200.10.10.5 |
| Celular | 192.168.1.30 | 200.10.10.5 |

Todos pueden utilizar la misma IP pública porque PAT diferencia sus conexiones mediante los números de puerto.

**Recuerda:** Cuando varios dispositivos de una casa comparten una IP pública para acceder a Internet, normalmente se utiliza PAT.

---

## 3. ¿Cuándo se utiliza el gateway y cuándo NAT?

No son lo mismo.

| Concepto | Función |
|---|---|
| Gateway | Es la puerta de salida que utiliza un dispositivo para comunicarse con otras redes. |
| NAT | Traduce las direcciones IP de los paquetes cuando corresponde. |
| DHCP | Asigna automáticamente la configuración IP a los dispositivos. |
| ISP | Es el proveedor del servicio de Internet. |

**Ejemplo completo:**

1. La PC recibe mediante DHCP la dirección `192.168.1.10`.
2. También recibe el gateway `192.168.1.1`.
3. La PC quiere comunicarse con un servidor de Internet.
4. Envía el paquete al router utilizando su gateway.
5. El router realiza NAT/PAT para traducir la dirección privada a la pública.
6. El paquete sale hacia Internet.
7. Cuando llega la respuesta, el router identifica la traducción correspondiente y la entrega a la PC.

**Nota:** NAT no es obligatorio para toda comunicación entre redes. Se utiliza cuando es necesario traducir direcciones.

---

## 4. Puntos clave para el examen

- El **gateway predeterminado** permite acceder a otras redes.
- El gateway normalmente corresponde a la IP de la interfaz LAN del router.
- Cada interfaz de un router puede conectar una red diferente.
- **DHCP** proporciona automáticamente la configuración IP.
- El router doméstico normalmente actúa como servidor DHCP.
- La interfaz WAN conecta el router con el ISP.
- **NAT** traduce direcciones IP.
- **PAT** permite compartir una IP pública utilizando números de puerto.
- NAT no aumenta la cantidad de IPv4 públicas disponibles.
- Para comunicarse dentro de una misma red local, normalmente no se necesita pasar por el gateway.

---

## 5. Preguntas de repaso

**1. ¿Cuál es la función principal de la puerta de enlace predeterminada?**

- A) Asignar direcciones IP automáticamente.
- B) Permitir la comunicación con otras redes.
- C) Traducir nombres de dominio.
- D) Almacenar direcciones MAC.

**2. ¿Qué dirección IP debe configurarse normalmente como gateway predeterminado de una PC?**

- A) La dirección IP del servidor DNS.
- B) La dirección IP pública del ISP.
- C) La dirección IP de la interfaz del router conectada a su LAN.
- D) La dirección de broadcast de la red.

**3. ¿Qué protocolo permite obtener automáticamente una dirección IPv4 y un gateway predeterminado?**

- A) DNS
- B) HTTP
- C) NAT
- D) DHCP

**4. ¿Qué sucede cuando una PC envía un paquete a otra PC de su misma red local?**

- A) Siempre debe pasar por el gateway.
- B) Normalmente puede comunicarse directamente sin pasar por el router.
- C) Necesita una dirección IP pública.
- D) Debe utilizar NAT obligatoriamente.

**5. ¿Qué interfaz de un router doméstico se conecta normalmente con el ISP?**

- A) LAN
- B) VLAN
- C) WAN
- D) Loopback

**6. ¿Qué significa NAT?**

- A) Network Access Technology.
- B) Network Address Translation.
- C) Network Automatic Transfer.
- D) Network Address Transmission.

**7. ¿Cuál es una función de NAT en una red doméstica?**

- A) Crear nuevas direcciones IPv4 públicas.
- B) Reemplazar completamente al protocolo DHCP.
- C) Traducir direcciones IPv4 privadas a públicas.
- D) Asignar direcciones MAC a los dispositivos.

**8. ¿Qué característica diferencia a PAT de una traducción NAT uno a uno?**

- A) Utiliza números de puerto para distinguir conexiones.
- B) Elimina la necesidad de utilizar un router.
- C) Funciona únicamente con IPv6.
- D) Asigna direcciones IP privadas mediante DHCP.

**9. Una PC tiene la IP 192.168.1.10/24 y su gateway es 192.168.1.1. ¿A dónde envía un paquete destinado a Internet?**

- A) A 192.168.1.255.
- B) A 127.0.0.1.
- C) A 192.168.1.1.
- D) A 192.168.1.10.

**10. ¿Cómo pueden varios dispositivos domésticos compartir una única dirección IPv4 pública para navegar por Internet?**

- A) Utilizando exclusivamente DNS.
- B) Configurando la misma IP privada en todos los dispositivos.
- C) Desactivando el gateway predeterminado.
- D) Utilizando PAT para diferenciar las conexiones mediante puertos.

---

## 6. Respuestas correctas

| Pregunta | Respuesta | Explicación |
|---|---|---|
| 1 | B | El gateway permite acceder a otras redes. |
| 2 | C | El gateway normalmente es la IP de la interfaz LAN del router. |
| 3 | D | DHCP proporciona automáticamente la configuración IP. |
| 4 | B | Los dispositivos de la misma LAN pueden comunicarse directamente. |
| 5 | C | La interfaz WAN conecta el router con el ISP. |
| 6 | B | NAT significa Network Address Translation. |
| 7 | C | NAT permite traducir direcciones privadas a públicas. |
| 8 | A | PAT utiliza números de puerto para diferenciar conexiones. |
| 9 | C | La PC envía el paquete al gateway 192.168.1.1. |
| 10 | D | PAT permite compartir una IP pública entre varios dispositivos. |
