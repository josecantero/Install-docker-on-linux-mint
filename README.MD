<div align="center">

# 🐳 Instalación de Docker en Linux Mint 22 (Zena)

[![Docker](https://shields.io)](https://docker.com)
[![Linux Mint](https://shields.io)](https://linuxmint.com)

Guía paso a paso para configurar el repositorio oficial e instalar el motor de Docker de forma correcta en distribuciones basadas en Ubuntu 24.04 (Noble), evitando conflictos de sustitución de URLs en la terminal.

</div>

---

## 📝 Descripción

Esta guía resuelve los problemas comunes de configuración y sincronización de claves PGP al instalar Docker en **Linux Mint 22 (Zena)**. Utiliza el servidor seguro de claves de Ubuntu y un método de codificación limpia para asegurar que el gestor de paquetes `apt` localice el repositorio adecuado de manera infalible.

## 🚀 Pasos para la Instalación

Sigue las siguientes instrucciones ejecutando los bloques de comandos en tu terminal:

### 1. Descargar la Clave de Seguridad Oficial
Crea el directorio seguro e importa la firma criptográfica original de Docker desde el servidor de llaves de Ubuntu:

```bash
sudo mkdir -p /etc/apt/keyrings
sudo gpg --homedir /tmp --no-default-keyring --keyring /etc/apt/keyrings/docker.gpg --keyserver hkps://://ubuntu.com --recv-keys 7EA0A9C3F273FCD8
```

### 2. Registrar el Repositorio de Docker
Añade la fuente de descarga oficial adaptada a la base de tu sistema operativo (`noble stable`):

```bash
echo "ZGViIFthcmNoPWFtZDY0IHNpZ25lZC1ieT0vZXRjL2FwdC9rZXlyaW5ncy9kb2NrZXIuZ3BnXSBodHRwczovL2Rvd25sb2FkLmRvY2tlci5jb20vbGludXgvdWJ1bnR1IG5vYmxlIHN0YWJsZQo=" | base64 -d | sudo tee /etc/apt/sources.list.d/docker.list
```

### 3. Actualizar el Índice de Paquetes
Sincroniza los repositorios de tu máquina para registrar las nuevas herramientas disponibles:

```bash
sudo apt update
```

### 4. Instalar Docker y Docker Compose
Descarga e instala el motor de Docker junto con sus complementos esenciales:

```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

---

## 🔍 Verificación

Para comprobar que la instalación se realizó con éxito y el servicio se encuentra activo, ejecuta:

```bash
sudo systemctl status docker
```




Install docker on linux mint is not easy and there is not official documentation by docker.com. That is why I create this repository where you can find the way to install Docker on linux mint.

# Install required packages
sudo apt-get update

sudo apt-get install ca-certificates curl gnupg

# Add Docker's official GPG key
sudo install -m 0755 -d /etc/apt/keyrings

sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc

sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the Docker repository with the correct Ubuntu code name
echo \\
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  jammy stable" | \\
  
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update the package index
sudo apt-get update

# Install Docker
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Install Docker Desktop
Download docker for Ubuntu deb package from [https://www.odoo.com/es_ES/page/download]

# Check the Docker status
sudo systemctl status docker

# Run Docker
sudo systemctl start docker



