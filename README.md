# Informatica Intelligent Cloud Services - Cloud Data Integration

## Acerca del curso

Este es un curso que ha sido desarrollado como parte del programa de capacitación interna de Axity.

Está orientado a todos aquellos colaboradores o consultores cuyas actividades están enfocadas en:

- Integración de datos

- Soluciones de gestión de datos en la nube

- Desarrollo de procesos de ETL


## Objetivos del curso

En este curso aprenderás:

- Sobre el conjunto de soluciones de Informatica

- Sobre la plataforma de gestión de datos de Informatica Intelligent Cloud Services (IICS)

- La arquitectura tecnológica de IICS

- A interactuar con la plataforma

- A desarrollar, implementar y monitorear procesos de integración de datos 

## Contenido del curso

- [Lección 01 - Introducción](Lecci%C3%B3n%2001%20-%20Introducci%C3%B3n.md)

- [Lección 02 - Portafolio de soluciones de Informatica](www.a.com)

- [Lección 03 - ¿Qué es IICS?](www.a.com)

- [Lección 04 - Arquitectura de IICS](www.a.com)

- [Lección 05 - Instalar Agente Seguro](www.a.com)

- [Lección 06 - Crear una nueva conexión](www.a.com)

- [Lección 07 - Mappings](www.a.com)

- [Lección 08 - Mapplets](www.a.com)

- [Lección 09 - Tasks & Taskflows](www.a.com)

- [Lección 10 - Monitoreo](www.a.com)

- [Lección 11 - Calendarización de procesos](www.a.com)

- [Lección 12 - Aceleradores](www.a.com)

- [Lección 13 - Ejemplo de integración de XML](www.a.com)

- [Lección 14 - Ejemplo de integración mediante Web Service](www.a.com)

- [Lección 15 - Ejemplo de integración con AWS](www.a.com)

- [Lección 16 - Los diferentes módulos de IICS](www.a.com)

- [Lección 17 - Seguridad y cumplimiento](www.a.com)

- [Lección 18 - De PowerCenter a IICS](www.a.com)

- [Lección 19 - ¿Qué viene para IICS?](www.a.com)

## Pre-requisitos

- Conocimiento sobre desarrollo de procesos de integración de datos (ETL)

- Conocimiento en al menos una herramienta de ETL

- Conocimientos básicos de programación

- Laptop con:

    - Mínimo 8 Gb de RAM

    - Mínimo 25 GB disponibles en disco

- Tener habilitado en el BIOS las opciones de virtualización. Si no se tienen los permisos de administrador para habilitar estas opciones, acercarse con el área de soporte para que los habiliten.

- Descargar e instalar [VMware Player 15](https://www.vmware.com/go/downloadworkstationplayer)

- Descargar la VM para el curso (solicitar al instructor)

- Para validar, iniciar la VM con el usuario: **axity** y contraseña: **Welcome1**.

**Nota**: La VM viene configurada con 4 GB de memoria y 2 Cores/Procesadores. Ajustar si es necesario.

## Para el instructor

Para habilitar el ambiente para este curso se deben considerar los siguientes puntos:

- En IICS, importar el archivo `_pro_cap_iics.zip` que se encuentra en el directorio `resources/iics/assets`. Este archivo contiene el proyecto con todos los objetos utilizados durante la capacitación, principalmente las conexiones. Los objetos como mappings, tasks solo son de referencia para la solución a los ejercicios realizados durante la capacitación.

- Para habilitar el ambiente se debe contar con la máquina virtual (VM) ubicada en el directorio `resources/vm`. Esta VM solo es para el instructor. Si no se cuenta con la VM, véase el archivo [INSTALL Environment](INSTALL_Environment.md) para crearla.

- La VM de este curso tiene una base de datos Postgres instalada. Por lo que todos los ejercicios de este curso deberán apuntar a esta base de datos. Esta opción tiene el inconveniente de que los participantes no podrán acceder o consultar la base de datos y sus tablas.

- Una alternativa al punto anterior es utilizar una base de datos Postgres en Amazon Web Services (AWS). Para habilitar Postgres en AWS, véase el archivo [INSTALL Environment](INSTALL_Environment.md) en la sección **Install Postgres in Cloud (Optional)**. En IICS las conexiones a utilizar son:
    - _conn_Postgres_AWS_course
    - _conn_Postgres_AWS_dvdrental

> En las conexiones, se debe actualizar el **Host Name** con el nombre de la instancia generada en AWS.

- Antes de iniciar el curso, el instructor deberá crear los usuarios necesarios en [IICS](https://dm-us.informaticacloud.com/). Los usuarios a crear deberán tener el siguiente estándar de nombrado:

    - `axity_user_<seq>`. Donde `<seq>` es un número consecutivo de dos dígitos. Ejemplo: **axity_user_01**, **axity_user_02**.

    - La contraseña de los usuarios será: **Welcome123**

- Utilizar el repositorio `axity-iics-internal-training` para compartir con el grupo de asistentes. Este repositorio puede estar en [GitHub](https://github.com) o en algún otro servicio de gestión de repositorios de **Git** Para publicar el contenido del curso en GitHub. Véase en archivo [INSTALL Repository](INSTALL_Repository.md).

- Todo el contenido del directorio `resources` se encuentra incluido en el archivo `.gitignore`, por lo que al ser publicado en **GitHub** no estará disponible para los asistentes.

- De forma predeterminada todas las lecciones se encuentran incluidas en el archivo `.gitignore`. Como recomendación, el instructor deberá ir comentando (`#`) cada línea asociada a la lección de acuerdo al avance en la capacitación.

- Dentro del repositorio `axity-iics-internal-training` se encuentra el directorio `solutions` el cual contiene las soluciones a cada uno de los ejercicios planteados en este curso. Este directorio se encuentra incluido en el archivo `.gitignore` ya que es para uso exclusivo del instructor como apoyo a la solución de los ejercicios de este curso.
