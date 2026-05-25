# ☁️ Implementación de una Nube Privada con Apache CloudStack para Lucsea

Proyecto Intermodular de **2º SMR** basado en el diseño e implementación de una infraestructura base de nube privada con **Apache CloudStack**.

El proyecto está orientado a la empresa **Lucsea**, ubicada en **Punta Umbría (Huelva)**, dedicada a la venta de productos tecnológicos y a la prestación de servicios informáticos.

---

## 📌 Datos del proyecto

| Campo | Información |
|---|---|
| Alumno | Javier González Fortes |
| Ciclo | 2º SMR |
| Empresa | Lucsea |
| Tipo de solución | Nube privada / IaaS |
| Plataforma principal | Apache CloudStack |
| Entorno utilizado | Laboratorio virtualizado |

---

## 🎯 Objetivo

El objetivo del proyecto es diseñar e implementar la base de una **nube privada IaaS** que permita centralizar recursos técnicos y preparar un entorno para la creación y gestión de máquinas virtuales.

El laboratorio simula una posible implantación real en Lucsea, permitiendo comprobar qué componentes serían necesarios y qué limitaciones aparecen al trabajar en un entorno virtualizado.

---

## 🏢 Contexto de Lucsea

Lucsea es una empresa unipersonal dedicada a servicios informáticos, soporte técnico, reparación, venta de productos tecnológicos, copistería, paquetería y telecomunicaciones.

La necesidad detectada es la falta de una plataforma centralizada para gestionar entornos virtuales, realizar pruebas técnicas y reducir la dependencia de equipos físicos.

---

## 🛠️ Tecnologías utilizadas

- Ubuntu Server 22.04 LTS
- Apache CloudStack 4.18.2.5
- MariaDB
- NFS
- KVM / libvirt
- Bridge `cloudbr0`
- VirtualBox
- Windows como sistema anfitrión

---

## 🧱 Arquitectura del laboratorio

El laboratorio se ha desplegado usando virtualización en capas:

**Windows → VirtualBox → Ubuntu Server 22.04 LTS → KVM / libvirt → Apache CloudStack**

Red utilizada:

| Elemento | Valor |
|---|---|
| Red host-only | 192.168.56.0/24 |
| Servidor CloudStack | 192.168.56.10 |
| Panel web | http://192.168.56.10:8080/client |

---

## ⚙️ Implementación realizada

Durante el proyecto se han realizado las siguientes fases:

1. Preparación del servidor Ubuntu Server.
2. Instalación de Apache CloudStack.
3. Configuración de MariaDB.
4. Inicialización de la base de datos.
5. Configuración del servidor de gestión.
6. Acceso al panel web.
7. Configuración del almacenamiento NFS.
8. Creación de zona, pod y clúster.
9. Configuración del bridge `cloudbr0`.
10. Adición del anfitrión KVM.
11. Configuración de almacenamiento primario y secundario.
12. Verificación de máquinas virtuales de sistema.
13. Documentación de limitaciones técnicas.

---

## ✅ Resultado conseguido

Se ha conseguido desplegar y documentar la infraestructura base de Apache CloudStack en laboratorio.

Componentes configurados:

- Servidor de gestión CloudStack.
- Base de datos MariaDB.
- Panel web operativo.
- Servidor NFS.
- Zona, pod y clúster.
- Anfitrión KVM.
- Almacenamiento primario y secundario.
- Máquinas virtuales de sistema activas.

---

## ⚠️ Limitación técnica detectada

Durante las pruebas finales se intentó avanzar hacia la creación de instancias finales, pero el entorno presentó limitaciones por el uso de **VirtualBox con virtualización anidada**.

La arquitectura real del laboratorio era:

**Windows → VirtualBox → Ubuntu Server → KVM → Apache CloudStack**

Esto provocó problemas de estabilidad, pérdida intermitente de `/dev/kvm` y bloqueos al intentar levantar máquinas virtuales internas.

Esta limitación afecta al entorno de laboratorio, no al diseño principal de CloudStack.

---

## 🏗️ Propuesta de implantación real

Para una implantación real en Lucsea, se recomienda utilizar:

- Servidor físico dedicado.
- Procesador compatible con VT-x/AMD-V.
- KVM nativo o Proxmox VE.
- Almacenamiento interno, NAS o NFS.
- Red cableada estable con direccionamiento fijo.
- Sistema de copias de seguridad.

De esta forma, CloudStack podría trabajar sobre virtualización real y no depender de VirtualBox.

---

## 📁 Estructura del repositorio

| Carpeta | Contenido |
|---|---|
| `01-Documentacion` | Memoria final del proyecto en PDF y ODT |
| `02-Capturas` | Capturas oficiales de la implementación |
| `03-BackUps` | Capturas de instantáneas del laboratorio |
| `04-Presentacion` | Presentación final del proyecto |
| `05-Ficheros-Fuente` | Información sobre recursos utilizados |
| `06-Diagrama` | Diagrama de arquitectura |
| `README.md` | Descripción general del proyecto |

---

## 📄 Documentación

La memoria completa se encuentra en:

`01-Documentacion/Proyecto-Lucsea-JGFortes.pdf`

En ella se desarrolla el análisis de la empresa, el anteproyecto, la implementación, las pruebas, las limitaciones y las conclusiones.

---

## 🎞️ Presentación

La presentación final se encuentra en:

`04-Presentacion/`

Resume el proyecto de forma visual para la exposición oral.

---

## 📌 Conclusión

El proyecto demuestra cómo una pequeña empresa como Lucsea podría beneficiarse de una infraestructura de nube privada para organizar recursos técnicos, crear entornos de prueba y mejorar la gestión de sistemas.

Aunque el laboratorio quedó limitado por VirtualBox y la virtualización anidada, se consiguió implementar la base funcional de CloudStack y definir una propuesta realista para llevar la solución a un entorno profesional.

---

## 👤 Autor

**Javier González Fortes**  
Proyecto Intermodular  
2º SMR  
Empresa: Lucsea