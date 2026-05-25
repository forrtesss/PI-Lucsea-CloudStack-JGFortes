☁️ Implementación de una Nube Privada con Apache CloudStack para Lucsea

Proyecto Intermodular de 2º SMR basado en el diseño e implementación de una infraestructura base de nube privada utilizando Apache CloudStack.

El proyecto está orientado a la empresa Lucsea, ubicada en Punta Umbría (Huelva), dedicada a la venta de productos tecnológicos y a la prestación de servicios informáticos, reparación, soporte técnico, instalación, copistería, paquetería y telecomunicaciones.

📌 Información del proyecto
Campo	Información
Proyecto	Implementación de una nube privada con Apache CloudStack
Alumno	Javier González Fortes
Ciclo	2º SMR
Empresa	Lucsea
Ubicación	Punta Umbría, Huelva
Tipo de solución	Nube privada / IaaS
Entorno	Laboratorio virtualizado
Tecnología principal	Apache CloudStack
🎯 Objetivo del proyecto

El objetivo principal del proyecto es diseñar e implementar la base de una nube privada IaaS mediante Apache CloudStack, adaptada a una pequeña empresa de servicios informáticos como Lucsea.

La finalidad de esta solución es disponer de una plataforma que permita centralizar recursos, organizar entornos técnicos y facilitar la creación de máquinas virtuales para pruebas, configuraciones y trabajos internos.

El laboratorio se ha desarrollado como una simulación realista, permitiendo estudiar cómo podría implantarse una solución de este tipo en un entorno profesional.

🏢 Contexto de Lucsea

Lucsea es una empresa unipersonal situada en Punta Umbría, orientada a clientes particulares, pequeños comercios locales y profesionales autónomos.

Actualmente, la empresa trabaja principalmente con equipos físicos y herramientas básicas de almacenamiento o intercambio de archivos. Por este motivo, se detecta como mejora posible la implantación de una infraestructura centralizada que permita crear entornos de prueba y organizar mejor los recursos técnicos.

🧩 Necesidad detectada

La necesidad principal detectada es la falta de una plataforma propia para gestionar recursos virtualizados.

Con una nube privada, Lucsea podría beneficiarse de:

Creación de entornos de prueba.
Centralización de recursos técnicos.
Reducción de dependencia de equipos físicos.
Mayor organización del trabajo técnico.
Posibilidad de conservar estados de máquinas o servicios.
Base para futuras pruebas, formación o recuperación de servicios.
🛠️ Tecnologías utilizadas
Tecnología	Función
Ubuntu Server 22.04 LTS	Sistema operativo base del servidor
Apache CloudStack 4.18.2.5	Plataforma de gestión de nube privada
MariaDB	Base de datos de CloudStack
NFS	Almacenamiento compartido
KVM / libvirt	Hipervisor utilizado por CloudStack
cloudbr0	Bridge de red para integración con KVM
VirtualBox	Plataforma utilizada para el laboratorio
Windows	Sistema anfitrión desde el que se ejecuta el laboratorio
🧱 Arquitectura del laboratorio

El laboratorio se ha desplegado en un entorno virtualizado mediante VirtualBox.

La arquitectura utilizada ha sido:

Windows → VirtualBox → Ubuntu Server 22.04 LTS → KVM / libvirt → Apache CloudStack

La red principal del laboratorio se configuró como red host-only.

Elemento	Valor
Red del laboratorio	192.168.56.0/24
Servidor CloudStack	192.168.56.10
Panel web	http://192.168.56.10:8080/client
⚙️ Implementación realizada

Durante el desarrollo del proyecto se ha llevado a cabo la implementación progresiva de la infraestructura base de Apache CloudStack.

Las fases principales han sido:

Preparación del servidor Ubuntu Server.
Instalación del repositorio oficial de Apache CloudStack.
Instalación de CloudStack Management Server.
Configuración de MariaDB.
Inicialización de la base de datos de CloudStack.
Configuración del servidor de gestión.
Acceso al panel web de CloudStack.
Configuración del almacenamiento NFS.
Creación de la zona inicial.
Configuración del bridge cloudbr0.
Adición del anfitrión KVM.
Configuración del almacenamiento primario y secundario.
Verificación de la infraestructura base.
Comprobación de las máquinas virtuales de sistema.
Documentación de limitaciones técnicas del entorno de laboratorio.
🗂️ Elementos configurados en CloudStack
Elemento	Estado
Servidor de gestión	Instalado y accesible
Base de datos MariaDB	Configurada e inicializada
Panel web	Operativo
Servidor NFS	Configurado
Zona	Creada
Pod	Creado
Clúster	Configurado
Anfitrión KVM	Añadido
Almacenamiento primario	Añadido mediante NFS
Almacenamiento secundario	Añadido mediante NFS
Máquinas virtuales de sistema	Activas y en ejecución
💾 Almacenamiento

Para el almacenamiento compartido se utilizó NFS, configurado en el propio servidor Ubuntu Server.

Tipo	Función	Ruta
Almacenamiento primario	Alojar discos de máquinas virtuales	/mnt/cloudstack/primary
Almacenamiento secundario	Guardar plantillas, ISOs y snapshots	/mnt/cloudstack/secondary
🌐 Red y bridge cloudbr0

Para integrar CloudStack con KVM se configuró un bridge de red llamado cloudbr0.

Este bridge permitió preparar la conectividad necesaria entre el servidor Ubuntu Server, CloudStack y el hipervisor KVM.

Elemento	Función
enp0s3	Interfaz NAT con salida a Internet
enp0s8	Interfaz host-only asociada al bridge
cloudbr0	Bridge principal usado por CloudStack y KVM
192.168.56.10	IP del servidor y del panel web
🖥️ Máquinas virtuales de sistema

Apache CloudStack desplegó automáticamente dos máquinas virtuales de sistema:

Máquina	Función
Console Proxy VM	Permite el acceso a consola de máquinas virtuales desde el panel web
Secondary Storage VM	Gestiona operaciones relacionadas con almacenamiento secundario, plantillas, ISOs y snapshots

Estas máquinas confirmaron que CloudStack fue capaz de utilizar el anfitrión KVM y el almacenamiento configurado para desplegar componentes internos de la plataforma.

✅ Pruebas realizadas

Durante la fase de validación se comprobó:

Servicio MariaDB activo.
Base de datos CloudStack inicializada correctamente.
CloudStack Management Server configurado.
Acceso al panel web desde navegador.
Servidor NFS operativo.
Zona creada y activa.
Anfitrión KVM añadido correctamente.
Almacenamiento primario reconocido.
Almacenamiento secundario reconocido.
Máquinas virtuales de sistema activas.

Estas pruebas permitieron confirmar que la infraestructura base de CloudStack quedó desplegada y documentada correctamente.

⚠️ Limitación técnica detectada

Durante las pruebas finales se intentó avanzar hacia el despliegue de instancias finales dentro de CloudStack.

Sin embargo, el entorno utilizado presentaba una limitación importante: el laboratorio estaba montado sobre VirtualBox y requería ejecutar KVM dentro de una máquina virtual.

Esto implicaba virtualización anidada:

Windows → VirtualBox → Ubuntu Server → KVM → Apache CloudStack

Durante esta fase se detectaron problemas como:

Pérdida intermitente de /dev/kvm.
Bloqueos de Ubuntu Server.
Errores críticos de VirtualBox.
Problemas de estabilidad al intentar levantar máquinas virtuales internas.

Esta limitación afecta al entorno de laboratorio, no al diseño ni a la configuración principal de CloudStack.

🏗️ Propuesta de implantación real

Para una implantación real en Lucsea, no se recomienda utilizar VirtualBox como base de ejecución de Apache CloudStack con KVM.

La propuesta recomendada sería utilizar:

Servidor físico dedicado.
Procesador compatible con VT-x/AMD-V.
KVM nativo o Proxmox VE.
Almacenamiento interno, NAS o NFS.
Red cableada estable con direccionamiento fijo.
Sistema de copias de seguridad periódicas.

De esta forma, CloudStack podría trabajar sobre un entorno de virtualización real, evitando los problemas derivados de la virtualización anidada.

📁 Estructura del repositorio
Carpeta	Contenido
01-Documentacion	Memoria final del proyecto en PDF y ODT
02-Capturas	Capturas oficiales de la implementación y recursos de presentación
03-BackUps	Capturas de instantáneas del laboratorio
04-Presentacion	Presentación final del proyecto
05-Ficheros-Fuente	Información sobre ficheros fuente utilizados
06-Diagrama	Diagrama de arquitectura del laboratorio
README.md	Descripción general del repositorio
📄 Documentación

La memoria completa del proyecto se encuentra en la carpeta 01-Documentacion.

Incluye:

Documento editable ODT.
Documento final PDF.

En la memoria se documenta todo el proceso de análisis, diseño, implementación, pruebas, limitaciones y conclusiones del proyecto.

🖼️ Capturas

Las capturas oficiales del proyecto se encuentran en la carpeta 02-Capturas.

Se incluyen capturas desde la preparación inicial del servidor hasta la verificación final de la infraestructura base de Apache CloudStack.

Las capturas están organizadas mediante el formato:

CAP-XX – Descripción de la captura

💽 Backups e instantáneas

Durante el desarrollo se utilizaron instantáneas de VirtualBox como puntos de restauración.

Estas instantáneas se usaron antes y después de fases críticas como:

Acceso inicial al panel web.
Configuración de NFS.
Configuración del bridge cloudbr0.
Adición del anfitrión KVM.
Verificación de la infraestructura base.
Recuperación de KVM y System VMs.

No se incluyen máquinas virtuales completas ni archivos pesados de VirtualBox debido a su tamaño.

🎞️ Presentación

La presentación utilizada para la exposición se encuentra en la carpeta 04-Presentacion.

La presentación resume el proyecto de forma visual, incluyendo:

Contexto de Lucsea.
Necesidad detectada.
Objetivo del proyecto.
Arquitectura del laboratorio.
Tecnologías utilizadas.
Implementación realizada.
Pruebas.
Limitación técnica.
Propuesta real.
Conclusiones.
📌 Resultado final

El proyecto ha conseguido desplegar y documentar la infraestructura base de una nube privada con Apache CloudStack en entorno de laboratorio.

Aunque el despliegue de instancias finales quedó limitado por el uso de VirtualBox con virtualización anidada, el proyecto permitió identificar una limitación técnica real y definir una propuesta de implantación más adecuada para un entorno profesional.

🧠 Conclusión

Este proyecto demuestra cómo una pequeña empresa como Lucsea podría beneficiarse de una infraestructura de nube privada para organizar recursos técnicos, crear entornos de prueba y mejorar la gestión de sistemas.

La solución desarrollada en laboratorio sirve como base inicial, mientras que una implantación real debería realizarse sobre hardware físico con KVM nativo o Proxmox VE para garantizar estabilidad, seguridad y rendimiento.

👤 Autor

Javier González Fortes
Proyecto Intermodular
2º SMR
Empresa: Lucsea