# Despliegue Automatizado de Landing Page con Vagrant y Ansible

![Ansible](https://img.shields.io/badge/Ansible-2.9%2B-blue.svg)
![Vagrant](https://img.shields.io/badge/Vagrant-2.2%2B-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

Este proyecto automatiza la creación de una máquina virtual y el despliegue de una landing page genérica utilizando **Vagrant** para la virtualización y **Ansible** para la provisión y configuración del servidor.

El objetivo es tener un entorno de desarrollo y pruebas reproducible con un solo comando, demostrando prácticas de Infraestructura como Código (IaC).

---

## 🚀 Tecnologías Utilizadas

* **Vagrant**: Para crear y gestionar la máquina virtual de forma declarativa.
* **VirtualBox**: Como proveedor de virtualización por defecto para Vagrant.
* **Ansible**: Para automatizar la instalación y configuración del software en la máquina virtual (servidor web, firewall, etc.).
* **Nginx**: Como servidor web para servir la landing page.
* **Ubuntu 22.04**: Como sistema operativo base en la máquina virtual.

---

## ✅ Requisitos Previos

Antes de empezar, asegúrate de tener instalado el siguiente software en tu máquina local:

* [Vagrant](https://www.vagrantup.com/downloads)
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

---

## 🏁 Guía de Inicio Rápido

Lanzar el entorno completo es tan sencillo como ejecutar un solo comando.

1.  **Clona este repositorio:**
    ```bash
    git clone https://github.com/VicRoUnix/iac-landing-page-deployment.git
    cd iac-landing-page-deployment
    ```

2.  **Levanta la máquina virtual:**
    ```bash
    vagrant up
    ```
    Este comando leerá el `Vagrantfile`, creará una nueva máquina virtual, la encenderá y ejecutará automáticamente el playbook de Ansible (`playbook.yml`) para provisionarla.

3.  **¡Y listo! Accede a tu Landing Page:**
    Una vez que el proceso finalice, abre tu navegador web y visita la dirección IP privada configurada en el `Vagrantfile` (por defecto  sera `http://192.168.56.150`). Deberías ver la landing page funcionando.

---

## 📁 Estructura del Proyecto

```
iac-landing-page-deployment
├── .gitignore
├── Vagrantfile
├── playbook.yml
├── README.md
├── inventories/
│   └── vagrant/
│       └── hosts.ini
└── roles/
    ├── nginx/
    │   ├── tasks/
    │   │   └── main.yml
    │   ├── handlers/
    │   │   └── main.yml
    │   └── files/
    │       ├── nginx.conf
    │       └── landing_page/
    │           └── index.html
    ├── devops/
    │   └── tasks/
    │       └── main.yml
    └── firewall/
        └── tasks/
            └── main.yml
```
---

## 🔧 Personalización

### Cambiar la Landing Page

Para desplegar tu propia landing page, simplemente reemplaza el contenido del directorio `roles/nginx/files/landing_page/` con tus propios ficheros `index.html`, CSS, JavaScript e imágenes. Vagrant y Ansible se encargarán del resto en el próximo provisionamiento.

### Ajustar la Configuración del Servidor

Puedes modificar el comportamiento de los roles de Ansible editando las variables en `playbook.yml` o las tareas dentro de cada rol en `roles/*/tasks/main.yml`.

---

## 💣 Cómo Destruir el Entorno

Cuando hayas terminado de probar, puedes destruir completamente la máquina virtual y liberar los recursos de tu ordenador con un solo comando:

```bash
vagrant destroy -f
