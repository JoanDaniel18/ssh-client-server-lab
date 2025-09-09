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
sudo ss -tlnp | grep ssh
```

## 2. Crear un usuario “servidor”

```bash
sudo adduser servidor
```
