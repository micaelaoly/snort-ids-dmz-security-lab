# Full Documentation - Snort IDS DMZ Security Lab

# Introducción

Este laboratorio fue desarrollado con el objetivo de simular una pequeña infraestructura segmentada orientada a monitorización defensiva y detección de tráfico sospechoso utilizando Snort como sistema IDS.

El entorno se diseñó utilizando varias máquinas virtuales conectadas mediante redes internas, separando diferentes zonas para recrear una arquitectura básica con DMZ. A través de esta segmentación fue posible generar tráfico desde una máquina Kali Linux y monitorizar los eventos producidos mediante reglas configuradas en Snort.

Además de la parte relacionada con IDS, el proyecto permitió reforzar conocimientos relacionados con Linux, redes TCP/IP, análisis de tráfico y fundamentos de Blue Team.

---

> [!NOTE]
> Todas las pruebas realizadas en este laboratorio se ejecutaron en un entorno virtualizado y completamente controlado con fines educativos y de aprendizaje.

---

# Objetivos del laboratorio

- Diseñar una arquitectura segmentada con DMZ
- Configurar Snort como IDS
- Detectar tráfico ICMP, SSH y HTTP
- Analizar alertas generadas por el IDS
- Comprender cómo fluye el tráfico entre diferentes zonas
- Reforzar conocimientos relacionados con monitorización defensiva y análisis de eventos

---

# Arquitectura del laboratorio

La infraestructura utilizada estuvo formada por varias máquinas virtuales conectadas mediante redes internas configuradas desde VirtualBox.

| Máquina | Función | Dirección IP |
|---|---|---|
| Kali Linux | Generación de tráfico y pruebas | 192.168.56.30 |
| Ubuntu Server | Máquina monitorizada | 192.168.56.20 |
| Snort IDS | Detección y monitorización | 192.168.56.10 |

La separación entre zonas permitió trabajar con conceptos relacionados con segmentación de red y monitorización de tráfico entre diferentes segmentos.

![Topología del laboratorio](../images/01-network-topology.png)

---

> [!TIP]
> La utilización de una DMZ permite aislar determinados servicios o sistemas más expuestos del resto de la red interna, reduciendo así el impacto de posibles incidentes o accesos no autorizados.

---

# 1. Preparación del entorno

## 1.1 Actualización del sistema

Lo primero realizado fue actualizar completamente las máquinas utilizadas dentro del laboratorio para evitar posibles problemas de compatibilidad y asegurar que todos los paquetes estuvieran actualizados.

```bash
sudo apt update
sudo apt upgrade -y
```

- `apt update` actualiza la lista de repositorios disponibles
- `apt upgrade -y` instala automáticamente las últimas versiones disponibles

---

## 1.2 Verificación de conectividad

Antes de comenzar con la instalación de Snort se realizaron pruebas básicas de conectividad entre las máquinas del entorno.

```bash
ping 192.168.56.20
```

Estas pruebas permitieron verificar:

- Comunicación entre máquinas
- Correcta configuración IP
- Funcionamiento de la red interna
- Conectividad hacia la DMZ

---

# 2. Instalación de Snort

## 2.1 Instalación del IDS

Snort se instaló en la máquina encargada de monitorizar el tráfico de red dentro del laboratorio.

```bash
sudo apt install snort -y
```

Durante la instalación se configuró la red utilizada para monitorización.

---

## 2.2 Verificación de instalación

Una vez finalizada la instalación se comprobó que Snort estuviera correctamente instalado:

```bash
snort -V
```

Esto permitió verificar la versión instalada y confirmar que el IDS estaba disponible en el sistema.

---

> [!IMPORTANT]
> Antes de ejecutar Snort es importante identificar correctamente la interfaz de red utilizada dentro de la máquina virtual.  
> Un error en la interfaz provocará que Snort no detecte tráfico aunque las reglas estén correctamente configuradas.

---

# 3. Configuración de reglas IDS

## 3.1 Archivo local.rules

Las reglas personalizadas se almacenaron en:

```bash
/etc/snort/rules/local.rules
```

En este archivo se añadieron reglas básicas para detectar diferentes tipos de tráfico dentro de la red.

Ejemplos de reglas utilizadas:

```conf
alert icmp any any -> any any (msg:"ICMP Packet Detected"; sid:1000001; rev:1;)

alert tcp any any -> any 22 (msg:"SSH Connection Detected"; sid:1000002; rev:1;)

alert tcp any any -> any 80 (msg:"HTTP Traffic Detected"; sid:1000003; rev:1;)
```

Estas reglas permitieron detectar:

- Paquetes ICMP
- Conexiones SSH
- Tráfico HTTP

---

## 3.2 Inclusión de reglas

Posteriormente se verificó que el archivo `local.rules` estuviera incluido dentro de la configuración principal de Snort.

```conf
include $RULE_PATH/local.rules
```

Esto permitió que las reglas personalizadas fueran cargadas automáticamente al iniciar el IDS.

---

![Reglas Snort](../images/03-snort-rules.png)

---

# 4. Ejecución de Snort

## 4.1 Inicio del IDS

Snort se ejecutó en modo consola para observar las alertas generadas en tiempo real.

```bash
sudo snort -A console -q -c /etc/snort/snort.conf -i enp0s3
```

Parámetros utilizados:

| Parámetro | Función |
|---|---|
| `-A console` | Muestra alertas en consola |
| `-q` | Reduce mensajes innecesarios |
| `-c` | Indica el archivo de configuración |
| `-i` | Especifica la interfaz monitorizada |

---

## 4.2 Generación de tráfico

Desde Kali Linux se realizaron diferentes pruebas para generar tráfico y comprobar la detección de eventos.

Pruebas realizadas:

### Ping ICMP

```bash
ping 192.168.56.20
```

### Escaneo básico con Nmap

```bash
nmap -sS 192.168.56.20
```

### Conexión SSH

```bash
ssh usuario@192.168.56.20
```

---

> [!TIP]
> El objetivo de estas pruebas no era comprometer sistemas, sino generar tráfico controlado para verificar el funcionamiento del IDS y observar cómo se producen las alertas dentro del laboratorio.

---

# 5. Monitorización y análisis de alertas

Una vez generado el tráfico desde Kali Linux, Snort comenzó a detectar diferentes eventos relacionados con las reglas configuradas previamente.

Las alertas podían visualizarse directamente desde consola o revisando los logs generados por el IDS.

```bash
sudo tail -f /var/log/snort/alert
```

También fue posible revisar el contenido completo de las alertas:

```bash
sudo cat /var/log/snort/alert
```

---

![Alertas generadas por Snort](../images/04-snort-alerts.png)

---

# 6. Problemas encontrados durante el laboratorio

Durante el desarrollo del laboratorio aparecieron diferentes problemas relacionados principalmente con:

- Interfaces de red incorrectas
- Errores de conectividad
- Reglas mal configuradas
- Logs vacíos
- Problemas de permisos

La mayoría de incidencias se solucionaron revisando:

- Direccionamiento IP
- Interfaces activas
- Configuración de reglas
- Logs del sistema
- Configuración de VirtualBox

---

> [!CAUTION]
> Un error muy frecuente fue ejecutar Snort sobre una interfaz equivocada.  
> Aunque las reglas estuvieran bien configuradas, el IDS no detectaba tráfico porque monitorizaba una interfaz sin actividad.

---

# 7. Resultados obtenidos

El laboratorio permitió desplegar un entorno funcional de monitorización defensiva utilizando Snort como sistema IDS dentro de una arquitectura segmentada.

Durante las pruebas se consiguió detectar correctamente:

- Tráfico ICMP
- Conexiones SSH
- Tráfico HTTP
- Escaneos básicos realizados desde Kali Linux

Además, el proyecto ayudó a comprender mejor:

- Funcionamiento básico de un IDS
- Importancia de la segmentación
- Flujo de tráfico entre redes
- Monitorización de eventos
- Análisis de alertas
- Fundamentos Blue Team

---

# 8. Conclusiones

Este laboratorio permitió trabajar de forma práctica conceptos relacionados con detección de intrusiones, análisis de tráfico y segmentación de red dentro de un entorno controlado.

Además de la parte técnica relacionada con Snort, el proyecto reforzó conocimientos importantes relacionados con Linux, redes TCP/IP y monitorización defensiva.

La utilización de una arquitectura con DMZ ayudó especialmente a comprender cómo puede organizarse una infraestructura segmentada y cómo un IDS aporta visibilidad sobre el tráfico que circula entre diferentes zonas.
