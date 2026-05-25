# ☁️ Implementación de una Nube Privada con Apache CloudStack para Lucsea

Proyecto Intermodular de **2º SMR** basado en el diseño e implementación de una infraestructura base de nube privada utilizando **Apache CloudStack**.

El proyecto está orientado a la empresa **Lucsea**, ubicada en **Punta Umbría (Huelva)**, dedicada a la venta de productos tecnológicos y a la prestación de servicios informáticos, reparación, soporte técnico, instalación, copistería, paquetería y telecomunicaciones.

---

## 📌 Información del proyecto

| Campo | Información |
|---|---|
| Proyecto | Implementación de una nube privada con Apache CloudStack |
| Alumno | Javier González Fortes |
| Ciclo | 2º SMR |
| Empresa | Lucsea |
| Ubicación | Punta Umbría, Huelva |
| Tipo de solución | Nube privada / IaaS |
| Entorno | Laboratorio virtualizado |
| Tecnología principal | Apache CloudStack |

---

## 🎯 Objetivo del proyecto

El objetivo principal del proyecto es **diseñar e implementar la base de una nube privada IaaS** mediante Apache CloudStack, adaptada a una pequeña empresa de servicios informáticos como Lucsea.

La finalidad de esta solución es disponer de una plataforma que permita centralizar recursos, organizar entornos técnicos y facilitar la creación de máquinas virtuales para pruebas, configuraciones y trabajos internos.

El laboratorio se ha desarrollado como una simulación realista, permitiendo estudiar cómo podría implantarse una solución de este tipo en un entorno profesional.

---

## 🏢 Contexto de Lucsea

Lucsea es una empresa unipersonal situada en Punta Umbría, orientada a clientes particulares, pequeños comercios locales y profesionales autónomos.

Actualmente, la empresa trabaja principalmente con equipos físicos y herramientas básicas de almacenamiento o intercambio de archivos. Por este motivo, se detecta como mejora posible la implantación de una infraestructura centralizada que permita crear entornos de prueba y organizar mejor los recursos técnicos.

---

## 🧩 Necesidad detectada

La necesidad principal detectada es la falta de una plataforma propia para gestionar recursos virtualizados.

Con una nube privada, Lucsea podría beneficiarse de:

- Creación de entornos de prueba.
- Centralización de recursos técnicos.
- Reducción de dependencia de equipos físicos.
- Mayor organización del trabajo técnico.
- Posibilidad de conservar estados de máquinas o servicios.
- Base para futuras pruebas, formación o recuperación de servicios.

---

## 🛠️ Tecnologías utilizadas

| Tecnología | Función |
|---|---|
| Ubuntu Server 22.04 LTS | Sistema operativo base del servidor |
| Apache CloudStack 4.18.2.5 | Plataforma de gestión de nube privada |
| MariaDB | Base de datos de CloudStack |
| NFS | Almacenamiento compartido |
| KVM / libvirt | Hipervisor utilizado por CloudStack |
| cloudbr0 | Bridge de red para integración con KVM |
| VirtualBox | Plataforma utilizada para el laboratorio |
| Windows | Sistema anfitrión desde el que se ejecuta el laboratorio |

---

## 🧱 Arquitectura del laboratorio

El laboratorio se ha desplegado en un entorno virtualizado mediante VirtualBox.

La arquitectura utilizada ha sido:

```text
Windows
└── VirtualBox
    └── Ubuntu Server 22.04 LTS
        └── KVM / libvirt
            └── Apache CloudStack