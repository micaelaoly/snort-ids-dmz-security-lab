# Notas sobre la configuración de la red

# Configuración general de red

El laboratorio se desarrolló utilizando varias máquinas virtuales conectadas mediante redes internas configuradas desde VirtualBox.

La comunicación entre sistemas se realizó utilizando direccionamiento IP estático para facilitar las pruebas y la monitorización de tráfico.

---

# Direccionamiento IP utilizado

| Máquina | Dirección IP | Función |
|---|---|---|
| Kali Linux | 192.168.56.30 | Generación de tráfico |
| Ubuntu Server | 192.168.56.20 | Máquina monitorizada |
| Snort IDS | 192.168.56.10 | Detección y monitorización |

---

# Redes utilizadas

La infraestructura del laboratorio se organizó utilizando diferentes segmentos virtualizados para simular una pequeña arquitectura empresarial con separación entre zonas.

El uso de redes internas permitió:

- Controlar el tráfico generado
- Aislar las máquinas virtuales
- Simular una arquitectura segmentada
- Realizar pruebas de monitorización de forma segura

---

# Interfaces de red

Las interfaces utilizadas variaban dependiendo de la máquina virtual y la configuración de VirtualBox.

Para identificarlas se utilizó:

```bash
ip a
```

Esto permitió comprobar:

- Interfaces activas
- Direcciones IP asignadas
- Estado de conectividad

---

# Conectividad entre máquinas

Se realizaron pruebas de conectividad utilizando:

```bash
ping
```

y diferentes herramientas de análisis y escaneo desde Kali Linux.

Las pruebas permitieron verificar:

- Comunicación entre zonas
- Acceso hacia la DMZ
- Funcionamiento de Snort
- Detección de tráfico por parte del IDS

---

# Objetivo de la configuración

La configuración de red del laboratorio estaba orientada principalmente a comprender cómo se comporta el tráfico dentro de una arquitectura segmentada y cómo un IDS puede analizar eventos generados entre diferentes zonas.

Además, ayudó a reforzar conceptos relacionados con:

- TCP/IP
- Redes Linux
- Segmentación
- Direccionamiento IP
- Monitorización de tráfico
- Seguridad defensiva
