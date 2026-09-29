# Linux Infrastructure & Security Lab

![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)
![Debian](https://img.shields.io/badge/Debian-A81D33?style=flat&logo=debian&logoColor=white)
![VirtualBox](https://img.shields.io/badge/VirtualBox-183A61?style=flat&logo=virtualbox&logoColor=white)
![Termius](https://img.shields.io/badge/Termius-000000?style=flat&logo=termius&logoColor=white)

Laboratorio virtualizado (*homelab*) orientado a la **administración de sistemas, redes Linux y seguridad defensiva**, construido sobre Debian y VirtualBox.

El proyecto simula una pequeña infraestructura de red compuesta por un gateway, un servidor de servicios y un equipo cliente. Cada componente se configura, prueba y documenta siguiendo una progresión desde la administración básica hasta la aplicación de controles de seguridad.

## 🎯 Objetivos

- Practicar administración de sistemas Linux.
- Diseñar y configurar una pequeña red interna.
- Implementar servicios de infraestructura y compartición de recursos.
- Gestionar usuarios, grupos, permisos y acceso remoto.
- Aplicar controles de seguridad y hardening.
- Documentar configuraciones y verificar su funcionamiento.

## 🖥️ Arquitectura

| Máquina | Rol | Recursos |
|---|---|---|
| **Debian-GW** | Gateway, DHCP, NAT y firewall | 1.5 GB RAM · 2 vCPU · 20 GB |
| **Debian-SRV** | Servicios de red y archivos | 3 GB RAM · 2 vCPU · 30 GB |
| **Debian-CLI** | Cliente de pruebas | 2 GB RAM · 2 vCPU · 20 GB |

La red utiliza una **Internal Network** para la comunicación entre las máquinas, mientras que `Debian-GW` proporciona salida a Internet mediante NAT.

```text
                    Internet
                       │
                    NAT/WAN
                       │
                 ┌─────┴─────┐
                 │ Debian-GW │
                 │ Gateway   │
                 │ DHCP/NAT  │
                 │ Firewall  │
                 └─────┬─────┘
                       │
               Internal Network
                 intnet-lab1  
                       │
             ┌─────────┴─────────┐
             │                   │
       ┌─────┴──────┐      ┌─────┴──────┐
       │ Debian-SRV │      │ Debian-CLI │
       │ Servicios  │      │  Cliente   │
       └────────────┘      └────────────┘
```

## 🧩 Módulos

### [00 — Preparación del entorno](./00-preparacion-entorno/)

Creación de las máquinas virtuales, red interna aislada y salida a Internet mediante NAT en el gateway.

### [01 — Usuarios y permisos](./01-usuarios-permisos/)

Gestión de usuarios, grupos, permisos y privilegios administrativos mediante un escenario de trabajo simulado.

### [02 — Red](./02-red/)

Implementación y configuración de los servicios **DHCP y DNS** para proporcionar direccionamiento y resolución de nombres dentro de la red.

### [03 — Acceso y archivos](./03-acceso-y-archivos/)

Configuración de **SSH, SFTP, NFS y Samba**, incluyendo autenticación, permisos y acceso a recursos compartidos.

### [04 — Servicios](./04-servicios/)

Implementación de un **servidor web Apache** y configuración básica del servicio.

### [05 — Seguridad](./05-seguridad/)

Aplicación de controles de seguridad mediante **firewall y Squid**, junto con una etapa de **hardening** sobre toda la infraestructura.

## 🔐 Seguridad

El proyecto incorpora controles orientados a reducir la superficie de ataque y limitar el acceso a los servicios:

- Filtrado de tráfico mediante firewall.
- Control de usuarios y privilegios.
- Configuración segura de servicios.
- Restricción de accesos según roles y necesidades.
- Hardening básico de los sistemas.
- Verificación desde el equipo cliente.

## 🧪 Verificación

Cada módulo incluye pruebas funcionales para comprobar la correcta implementación del servicio y su comportamiento desde otros equipos de la red.

Las evidencias y configuraciones relevantes se encuentran dentro de cada módulo.

## 🛠️ Tecnologías

**Debian · Linux · VirtualBox · DHCP · DNS · SSH · SFTP · NFS · Samba · Apache · Squid · iptables · UFW**

## 📂 Estructura

```text
netsec-defensive/
├── README.md
├── 00-preparacion-entorno/
├── 01-usuarios-permisos/
├── 02-red/
├── 03-acceso-y-archivos/
├── 04-servicios/
├── 05-seguridad/
└── recursos/
```
