```text
███████╗███╗   ██╗ ██████╗ ██████╗ ████████╗     ██╗██████╗ ███████╗
██╔════╝████╗  ██║██╔═══██╗██╔══██╗╚══██╔══╝     ██║██╔══██╗██╔════╝
███████╗██╔██╗ ██║██║   ██║██████╔╝   ██║        ██║██║  ██║███████╗
╚════██║██║╚██╗██║██║   ██║██╔══██╗   ██║        ██║██║  ██║╚════██║
███████║██║ ╚████║╚██████╔╝██║  ██║   ██║        ██║██████╔╝███████║
╚══════╝╚═╝  ╚═══╝ ╚═════╝ ╚═╝  ╚═╝   ╚═╝        ╚═╝╚═════╝ ╚══════╝

DMZ Security Lab · Snort IDS · Blue Team · Network Monitoring
```

# Snort IDS DMZ Security Lab

![Snort](https://img.shields.io/badge/Snort-IDS-red)
![Blue Team](https://img.shields.io/badge/Blue%20Team-Network%20Defense-blue)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-orange)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)
![Level](https://img.shields.io/badge/Level-Junior%20SOC-lightgrey)

Laboratorio de ciberseguridad defensiva basado en **Snort IDS**, segmentación de red y arquitectura con **DMZ**, orientado a monitorización de tráfico y detección de eventos sospechosos dentro de un entorno virtualizado.

---

> [!NOTE]
> Este proyecto fue desarrollado en un entorno completamente controlado y con fines educativos, enfocado en la parte defensiva de la ciberseguridad y monitorización de red.

---

# Descripción del proyecto

Este laboratorio simula una pequeña infraestructura segmentada donde diferentes zonas de red se encuentran separadas mediante una arquitectura básica con DMZ. El objetivo principal fue comprender cómo funciona la monitorización de tráfico en un entorno defensivo y cómo un IDS como Snort puede detectar actividad sospechosa dentro de la red.

Durante el desarrollo del proyecto se trabajó con conceptos relacionados con redes, segmentación, análisis de tráfico, monitorización y detección de eventos mediante reglas IDS. Además, se realizaron pruebas controladas desde una máquina Kali para generar tráfico y verificar el funcionamiento de las alertas.

El laboratorio está orientado principalmente a conceptos de Blue Team y análisis defensivo, reforzando conocimientos relacionados con Linux, redes TCP/IP y monitorización de seguridad.

---

# Objetivos del laboratorio

- Diseñar una arquitectura segmentada con DMZ
- Configurar Snort como sistema IDS
- Detectar tráfico ICMP, SSH y HTTP
- Analizar alertas generadas por el IDS
- Comprender el flujo de tráfico dentro de una red segmentada
- Reforzar conocimientos de monitorización defensiva y Blue Team

---

# Tecnologías utilizadas

| Tecnología | Función |
|---|---|
| Snort | Sistema IDS |
| Ubuntu Server | Máquina defensiva |
| Kali Linux | Generación de tráfico de prueba |
| Linux | Administración del entorno |
| VirtualBox | Virtualización |
| TCP/IP | Comunicación y análisis de red |
| Nmap | Pruebas de escaneo |
| Wireshark | Apoyo en análisis de tráfico |

---

# Arquitectura del laboratorio

| Zona | Máquina | Función |
|---|---|---|
| Red externa | Kali Linux | Generación de tráfico |
| DMZ | Ubuntu Server | Máquina monitorizada |
| IDS | Snort | Detección de eventos |
| Red interna | Cliente interno | Segmento protegido |

![Arquitectura del laboratorio](images/01-network-topology.png)

La arquitectura se diseñó separando las diferentes zonas de red para simular una infraestructura básica con segmentación y monitorización de tráfico mediante un IDS.

---

# Eventos detectados

| Evento | Descripción |
|---|---|
| ICMP | Detección de tráfico ping |
| SSH | Detección de conexiones SSH |
| HTTP | Monitorización de tráfico web |
| Escaneo de puertos | Detección básica de reconocimiento |

---

## Reglas IDS utilizadas

![Reglas Snort](images/03-snort-rules.png)

---

## Alertas generadas por Snort

![Alertas Snort](images/04-snort-alerts.png)

---

# Skills 

- Configuración básica de Snort IDS
- Segmentación de red
- Diseño de arquitectura con DMZ
- Monitorización de tráfico
- Análisis de eventos
- Administración Linux
- Detección de actividad sospechosa
- Fundamentos Blue Team
- Redes TCP/IP

---


# Documentación completa

La documentación técnica detallada del laboratorio se encuentra en:

[Ver documentación completa](docs/full-documentation.md)

---

> [!TIP]
> Este repositorio está orientado a demostrar conocimientos prácticos relacionados con IDS, redes, segmentación y monitorización defensiva dentro de un entorno controlado.

---

# Autor

Proyecto desarrollado como práctica de laboratorio orientada a monitorización de red, análisis de tráfico y detección de eventos utilizando Snort IDS.
