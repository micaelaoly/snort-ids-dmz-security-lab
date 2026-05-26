# DMZ Topologia

# Objetivo de la arquitectura

La arquitectura del laboratorio fue diseñada para simular un entorno segmentado donde diferentes zonas de red se encuentran separadas para mejorar la seguridad y el control del tráfico.

El objetivo principal de utilizar una DMZ fue entender cómo se puede aislar una máquina o servicio más expuesto del resto de la red interna, reduciendo así el impacto que podría tener un posible compromiso sobre otros sistemas del entorno.

Además, esta segmentación permitió monitorizar de forma más clara el tráfico que entra y sale de determinadas zonas mediante el uso de Snort como IDS.

---

# Zonas de red utilizadas

| Zona | Función |
|---|---|
| Red externa | Generación de tráfico y pruebas |
| DMZ | Máquina monitorizada o servicio expuesto |
| Red interna | Segmento protegido |
| IDS | Monitorización y detección |

---

# Flujo de tráfico

La máquina Kali se utilizó para generar tráfico controlado hacia la DMZ y realizar diferentes pruebas relacionadas con conectividad, escaneo y detección de eventos.

Snort monitorizaba continuamente el tráfico circulando por la interfaz configurada, permitiendo detectar eventos relacionados con conexiones ICMP, SSH y otros protocolos definidos mediante reglas.

El objetivo no era únicamente generar alertas, sino comprender cómo fluye el tráfico dentro de una arquitectura segmentada y cómo un IDS puede aportar visibilidad sobre la actividad de red.

---

# Segmentación de red

La separación entre redes permitió trabajar con conceptos básicos relacionados con:

- Segmentación
- Monitorización
- Control de tráfico
- Visibilidad de red
- Seguridad defensiva

Este tipo de arquitectura es habitual en entornos reales donde ciertos servicios necesitan estar más expuestos que otros y resulta importante limitar la comunicación directa con la red interna.

---

# Arquitectura visual

La topología utilizada en el laboratorio puede verse en la siguiente imagen:

![Topología DMZ](../images/01-network-topology.png)

---

# Conclusiones

La utilización de una DMZ dentro del laboratorio permitió entender mejor la importancia de separar diferentes zonas de red y cómo esta segmentación ayuda a mejorar tanto la seguridad como la monitorización del tráfico.

Además, el laboratorio ayudó a reforzar conocimientos relacionados con redes TCP/IP, Linux, IDS y análisis básico de eventos desde un enfoque orientado a Blue Team.
