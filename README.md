# Laboratorio SSH con claves pública/privada en Kali Linux

Este repositorio contiene la documentación y pasos realizados para montar 
un servicio **cliente-servidor SSH** en **Kali Linux**, utilizando 
**autenticación con claves pública/privada**.

---

## 🔹 Objetivo
- Configurar un servidor SSH en la misma máquina (localhost).
- Crear un usuario "servidor" que actúe como host remoto.
- Generar claves pública/privada desde el usuario principal.
- Conectarse al servidor usando clave en lugar de contraseña.

---

## 🔹 Requisitos
- Kali Linux (o cualquier distro basada en Debian).
- Usuario con permisos `sudo`.
- Paquete `openssh-server` instalado.

---

## 🔹 Pasos realizados

### 1. Instalar y habilitar el servidor SSH
```bash
sudo apt update
sudo apt install openssh-server -y
sudo systemctl enable ssh
sudo systemctl start ssh
sudo systemctl status ssh
```
# Verificación, Configuración y Conexión SSH en Kali Linux



## 2. Verificar el puerto y las interfaces donde escucha SSH
```bash
sudo ss -tlnp | grep ssh
```
## 3. Crear un usuario "servidor"
```bash
sudo adduser servidor
```
Detalles del proceso
Se asigna una contraseña temporal
Se completan los datos opcionales (nombre completo, teléfono, etc.)
Resultado esperado: Usuario servidor creado exitosamente
## 4. Generar claves pública/privada en el cliente
```bash
ssh-keygen -t rsa -b 4096
```
Archivos generados
Clave privada: ~/.ssh/id_rsa
Clave pública: ~/.ssh/id_rsa.pub
## 5. Copiar la clave pública al servidor
```bash
ssh-copy-id servidor@localhost
```
Verificación de la clave
- cat /home/servidor/.ssh/authorized_keys
## 6. Conexión al servidor usando la clave
```bash
ssh servidor@localhost
```
Detalles de la conexión
Usuario activo: servidor
Máquina: localhost
Autenticación: mediante clave privada de daniel

## Observaciones
Este laboratorio puede replicarse usando otra máquina en la red reemplazando localhost por la IP real
Se recomienda deshabilitar la autenticación por contraseña en ambientes de producción para mejorar la seguridad
El usuario servidor se creó únicamente con fines educativos y puede eliminarse posteriormente
## Autor
Nombre: Joan Daniel Rivas Andrade
Materia: Seguridad / Redes
Profesor: Cristhian Iza
Fecha: Septiembre 2025
