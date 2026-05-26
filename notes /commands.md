# Configuración de la red y verificación

Comandos utilizados para comprobar interfaces de red, conectividad y direccionamiento IP dentro del laboratorio
---
```bash
ip a
```

Muestra todas las interfaces de red disponibles junto con sus direcciones IP asignadas.

---

```bash
ip route
```

Permite comprobar la tabla de rutas del sistema.

---

```bash
ping 192.168.56.20
```

Utilizado para verificar conectividad entre máquinas dentro de la red virtualizada.

---

```bash
ping 192.168.56.10
```

Comprobación de conectividad entre la máquina IDS y el resto de sistemas del laboratorio.

---

# Snort IDS

Comandos utilizados para verificar instalación, lanzar el IDS y revisar alertas generadas.

```bash
snort -V
```

Comprueba que Snort se encuentra correctamente instalado.

---

```bash
sudo systemctl status snort
```

Verifica el estado del servicio Snort.

---

```bash
sudo snort -A console -q -c /etc/snort/snort.conf -i enp0s3
```

Ejecución manual de Snort en modo IDS monitorizando la interfaz de red seleccionada.

Parámetros utilizados:

- `-A console` muestra alertas directamente en consola
- `-q` reduce mensajes innecesarios
- `-c` especifica el archivo de configuración
- `-i` indica la interfaz monitorizada

---

```bash
sudo tail -f /var/log/snort/alert
```

Permite visualizar alertas en tiempo real generadas por Snort.

---

```bash
sudo cat /var/log/snort/alert
```

Muestra el contenido completo del log de alertas.

---

# Nmap

Pruebas de reconocimiento y generación de tráfico realizadas desde Kali Linux.

```bash
nmap -sS 192.168.56.20
```

Escaneo TCP SYN utilizado para comprobar detección por parte del IDS.

---

```bash
nmap -sV 192.168.56.20
```

Detección de versiones de servicios expuestos.

---

```bash
nmap -Pn 192.168.56.20
```

Escaneo ignorando descubrimiento previo por ICMP.

---

# SSH

Pruebas de conexión SSH utilizadas para generar tráfico monitorizado.

```bash
ssh usuario@192.168.56.20
```

Intento de conexión SSH hacia la máquina monitorizada.

---

# Logs y análisis

Comandos utilizados para revisar logs y verificar eventos generados durante las pruebas.

```bash
sudo journalctl -xe
```

Consulta de logs generales del sistema.

---

```bash
sudo less /var/log/syslog
```

Revisión de logs del sistema operativo.

---

```bash
sudo tail -f /var/log/syslog
```

Monitorización en tiempo real de eventos del sistema.

---

# Verificación de servicios

Comandos utilizados para verificar servicios relacionados con el laboratorio.

```bash
sudo systemctl status networking
```

Comprobación del servicio de red.

---

```bash
sudo systemctl restart snort
```

Reinicio del servicio Snort tras modificar configuración o reglas.

---

```bash
sudo systemctl daemon-reload
```

Recarga de servicios systemd tras cambios en configuraciones.

---

# Comprobación de puertos y conectividad

```bash
sudo ss -tunlp
```

Muestra puertos abiertos y servicios asociados.

---

```bash
sudo netstat -tunlp
```

Verificación de conexiones y puertos activos dentro del laboratorio.

---

# Observaciones

Durante las pruebas se comprobó el funcionamiento correcto de Snort frente a diferentes tipos de tráfico generados desde Kali Linux. Las alertas obtenidas permitieron verificar que las reglas configuradas funcionaban correctamente y que la arquitectura segmentada del laboratorio permitía monitorizar eventos dentro de la red.
