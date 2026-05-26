# Troubleshooting y Problemas encontrados durante el laboratorio

# Problemas relacionados con interfaces de red

Uno de los problemas más frecuentes durante el laboratorio fue identificar correctamente la interfaz de red utilizada por Snort. Dependiendo de la configuración de VirtualBox, el nombre de la interfaz podía variar entre diferentes máquinas virtuales.

Para solucionarlo se utilizó:

```bash
ip a
```

Esto permitió identificar la interfaz correcta antes de ejecutar Snort.

---

# Problemas de conectividad entre máquinas

En algunos momentos las máquinas virtuales no podían comunicarse correctamente debido a errores en la configuración de red interna o adaptadores virtuales mal configurados.

Las comprobaciones realizadas fueron:

- Verificar IPs asignadas
- Revisar configuración de adaptadores en VirtualBox
- Comprobar conectividad mediante ping
- Revisar máscaras de red

También se revisó la tabla de rutas utilizando:

```bash
ip route
```

---

# Snort no detectaba tráfico

Inicialmente algunas reglas no generaban alertas porque el tráfico no coincidía exactamente con las condiciones definidas en las reglas IDS.

Para solucionarlo se realizaron diferentes pruebas modificando:

- Puertos monitorizados
- Tipo de protocolo
- Dirección origen/destino
- Sintaxis de reglas

También se comprobó que las reglas locales estuvieran correctamente incluidas dentro de:

```bash
/etc/snort/snort.conf
```

---

# Logs vacíos o sin alertas

En algunas pruebas el archivo de alertas permanecía vacío aunque se generaba tráfico desde Kali.

Las principales causas encontradas fueron:

- Interfaz incorrecta
- Reglas mal configuradas
- Snort ejecutándose sin permisos adecuados
- Tráfico fuera de la red monitorizada

Para verificarlo se revisaron logs y se ejecutó Snort manualmente en consola para observar alertas en tiempo real.

---

# Problemas relacionados con permisos

Algunos archivos de configuración y logs requerían permisos elevados para poder modificarse o visualizarse.

Por ello la mayoría de comandos relacionados con Snort y logs se ejecutaron utilizando `sudo`.

---

# Dificultades durante la segmentación de red

La parte relacionada con DMZ y segmentación fue una de las más importantes del laboratorio, ya que cualquier error en la configuración de red podía impedir completamente la comunicación entre zonas.

Durante las pruebas se revisó varias veces:

- Direccionamiento IP
- Redes internas
- Configuración NAT
- Adaptadores virtuales
- Reglas de comunicación

Esto permitió entender mejor cómo funciona una arquitectura segmentada y cómo influye en la monitorización de tráfico.

---

# Conclusiones técnicas

La resolución de problemas durante el laboratorio permitió reforzar conocimientos relacionados con:

- Redes virtualizadas
- Linux
- IDS
- Logs
- Configuración de servicios
- Segmentación
- Monitorización de tráfico
- Troubleshooting básico en entornos defensivos

Además, ayudó a comprender que gran parte del trabajo relacionado con Blue Team y monitorización consiste en identificar errores de configuración, revisar logs y validar continuamente el flujo de tráfico dentro de la infraestructura.
