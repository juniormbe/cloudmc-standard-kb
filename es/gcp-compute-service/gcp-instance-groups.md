---
title: "GCP: Grupos de instancias"
slug: gcp-grupos-de-instancias
---


Los **grupos de instancias** se utilizan para proporcionar servicios de backend, como el equilibrio de carga. Los grupos de instancias existen en una sola zona dentro de una región y pueden contener instancias solamente en esa zona.

Para crear, modificar o eliminar un grupo de instancias, una cuenta con la función *Usuario* debe ser miembro del entorno que contiene la instancia y también tener asignada la función de entorno *Editor* o *Propietario*. Una cuenta con el rol de *Administrador* o superior puede crear, modificar o eliminar grupos de instancias en un entorno.

Para administrar grupos de instancias, navega hasta el entorno de GCP deseado, haz clic en la pestaña **Cómputo** y luego haz clic en *Grupos de instancias*.

### Agregar un grupo de instancias

1. Desde la página *Grupos de instancias*, haz clic en *Agregar un grupo de instancias*. Aparecerá la página *Agregar un grupo de instancias*.
1. Ingresa un nombre o acepte el predeterminado e ingresa una descripción si lo deseas.
1. Selecciona la región y la zona donde se encuentran ubicadas las instancias a agrupar.
1. Si la subred seleccionada contiene instancias, aparecerá una lista emergente etiquetada **Instancias** debajo de la subred. Puedes elegir cero o más instancias de esta lista para convertirse en miembros de este grupo de instancias. Tenga en cuenta que cambiar una zona borrará la lista de instancias ya seleccionadas.
1. Haz clic en *Aplicar* para crear el grupo.
1. Volverás a la página *Grupos de instancias*, se creará el grupo de instancias y las instancias se agregarán al grupo.

**Nota:** Una vez que se crea un grupo de instancias, su región y zona no se pueden cambiar.

### Gestionar un grupo de instancias

1. En la página *Grupos de instancias*, haz clic en el menú **Acción** y selecciona *Administrar miembros del grupo de instancias*. Aparecerá el cuadro de diálogo *Administrar miembros del grupo de instancias*.
1. La lista emergente etiquetada **Instancias** contendrá una lista de las instancias que son miembros de este grupo.
    - Para eliminar una instancia del grupo, haz clic en la marca X a la derecha del nombre de una instancia.
    - Para agregar una instancia al grupo, haz clic en la lista emergente, luego haz clic en el nombre de la instancia que deseas agregar.
1. Haz clic en *Aplicar* cuando terminas de realizar los cambios.

### Eliminar un grupo de instancias

No se puede eliminar un grupo de instancias que está utilizado por un servicio de backend. Eliminar un grupo de instancias no elimina sus instancias miembro.

1. Desde la página *Grupos de instancias*, haz clic en el menú **Acción** y selecciona *Eliminar*.
1. Se te pedirá que confirmes la operación. Haz clic en *Aplicar* para confirmar.
