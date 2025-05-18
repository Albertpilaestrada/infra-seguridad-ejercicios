
# 🛡️ Ejercicios Prácticos - Seguridad en Infraestructura

Este repositorio contiene una colección de ejercicios prácticos con resolución, enfocados en la preparación para roles técnicos en ciberseguridad defensiva e infraestructura.

## 📘 Contenido

### 1. Administración de Servidores (Linux)
**Ejercicio:**  
Configura un servidor Ubuntu para:  
- Acceso por SSH solo con llave pública.  
- Deshabilita el acceso del usuario root por SSH.  
- Asegura el servidor con firewall UFW permitiendo solo SSH y HTTP.  

**Solución:**  
```bash
# Crear usuario y llave pública
adduser nuevo_usuario
mkdir -p /home/nuevo_usuario/.ssh
echo "LLAVE_PUBLICA" > /home/nuevo_usuario/.ssh/authorized_keys

# Configurar SSH
sudo nano /etc/ssh/sshd_config
# Cambiar:
# PasswordAuthentication no
# PermitRootLogin no

# Activar UFW
sudo ufw allow ssh
sudo ufw allow http
sudo ufw enable
```

---

### 2. DNS y DHCP
**Ejercicio:**  
Simula una mala configuración de DNS que afecte la resolución de dominios internos. Diagnósticala.

**Solución:**  
```bash
# Editar /etc/resolv.conf con DNS inválido
nameserver 8.8.8.9

# Probar con dig
dig dominio.local

# Solucionar:
nameserver 192.168.1.1
```

---

### 3. Protocolos de Red
**Ejercicio:**  
Captura y analiza tráfico HTTP con Wireshark. Identifica si la conexión es insegura.

**Solución:**  
1. Filtrar en Wireshark por `http`.  
2. Revisar si hay credenciales en texto plano.  
3. Concluir la necesidad de usar HTTPS (TLS).

---

### 4. Segmentación de Red y Firewalls
**Ejercicio:**  
Configura dos VLANs simuladas y un firewall que bloquee tráfico entre ellas.

**Solución:**  
1. Simula VLANs con GNS3 o Packet Tracer.  
2. Crea reglas ACL para bloquear tráfico entre segmentos.  
3. Verifica aislamiento con ping.

---

### 5. Normativas de Seguridad
**Ejercicio:**  
Estás ante una base de datos con datos personales. Aplica medidas para cumplir con GDPR.

**Solución:**  
- Cifrado en reposo (TDE, LUKS).  
- Control de acceso RBAC.  
- Logs de acceso.  
- Enmascaramiento de datos sensibles.

---

### 6. Monitorización (Zabbix/Grafana)
**Ejercicio:**  
Monitoriza uso de CPU y RAM de un servidor. Alerta si CPU > 80%.

**Solución:**  
1. Instala agente Zabbix.  
2. Configura ítems para CPU/RAM.  
3. Crea trigger para CPU alta.  
4. Visualiza en Grafana.

---

### 7. Comunicaciones Seguras y VPN
**Ejercicio:**  
Configura una VPN con IPsec entre dos puntos y verifica que todo el tráfico esté cifrado.

**Solución:**  
1. Usar StrongSwan/Libreswan.  
2. Autenticación por PSK.  
3. Verifica cifrado con tcpdump.

---

### 8. IDS/IPS y Anti-DDoS
**Ejercicio:**  
Detecta un escaneo de puertos con Snort.

**Solución:**  
```bash
# Regla básica de Snort
alert tcp any any -> any any (msg:"Escaneo de puertos detectado"; flags:S; threshold:type both, track by_src, count 20, seconds 60; sid:1000001;)
```
1. Ejecuta un `nmap` y observa alerta.

---

## 📂 Licencia
Uso libre con atribución. Contribuciones son bienvenidas.

