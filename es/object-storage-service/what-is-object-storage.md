---
title: "¿Qué es el almacenamiento de objetos?"
slug: que-es-almacenamiento-de-objetos
---


**Almacenamiento de objetos** es un servicio que permite acceder a un archivo almacenado a través de una URL. La [arquitectura de almacenamiento de objetos](https://es.wikipedia.org/wiki/Almacenamiento_de_objetos_(inform%C3%A1tica)) permite muchas posibilidades, incluido un acceso significativamente más rápido, facilidad para compartir archivos y muchos menos gastos generales que localizar un archivo a través de un sistema de archivos tradicional.

Un sistema de archivos tradicional requiere que un archivo se almacene en una ubicación específica en un disco, y ubica ese archivo dentro de una jerarquía de directorios (por ejemplo, **/data/shared/mi-archivo-grande.zip**). Esto tiene sentido para una persona que trabaja en una estación de trabajo local. El almacenamiento de objetos, por otro lado, trata un archivo como un *objeto*: algo que se recuperará usando su URL, similar a una página web o una imagen (por ejemplo, **https://objetos.acme.com/publico/mi-archivo-grando.zip**). Debido a que una URL hace referencia al archivo, es irrelevante si el archivo es local o remoto.

Este enfoque hace que el almacenamiento de objetos sea ideal para entornos de computación en la nube donde, por ejemplo, los datos de un archivo podrían distribuirse físicamente en múltiples ubicaciones. Por lo general, se accede a los archivos en el almacenamiento de objetos a través de aplicaciones que usan una API REST. Las aplicaciones pueden recuperar muy rápidamente un archivo requerido a través de la URL del objeto.

### Capacidades generales

- Proporciona almacenamiento de objetos escalable y redundante mediante clústeres de servidores estandarizados capaces de almacenar petabytes de datos.
- Sistema de almacenamiento distribuido para datos estáticos como imágenes de máquinas virtuales, almacenamiento de fotos, almacenamiento de correo electrónico, copias de seguridad y archivos. No tener un punto de control central proporciona una mayor escalabilidad, redundancia, y durabilidad.
- Los objetos y archivos se escriben en varias unidades de disco distribuidas en los servidores del centro de datos, y el software es responsable de garantizar la replicación y la integridad de los datos en todo el clúster.
- Los clústeres de almacenamiento se escalan horizontalmente simplemente agregando nuevos servidores. Si falla un disco o incluso un servidor completo, el sistema replica su contenido de otros nodos activos a nuevas ubicaciones en el clúster.

### Casos de uso

El almacenamiento de objetos tiene varios casos de uso potenciales. Estos son solo algunos ejemplos de las posibilidades:

- Archivado y respaldo de registros, datos de usuarios, volcados de bases de datos, etc.
- Contenido web como imágenes, videos, archivos estáticos, etc.
- Compartir documentos
- Almacenamiento a largo plazo para monitorear métricas
