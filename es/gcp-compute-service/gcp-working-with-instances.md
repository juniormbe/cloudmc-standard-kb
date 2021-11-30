---
title: "GCP: Trabajando con instancias"
slug: gcp-trabajando-con-instancias
---


Para crear, modificar o eliminar una instancia, una cuenta con la función *Usuario* debe ser miembro del entorno que contiene la instancia y también tener asignada la función de entorno *Editor* o *Propietario*. Una cuenta con el rol de *Administrador* o superior puede crear, modificar o eliminar instancias en un entorno.

Para acceder a las instancias, navega hasta tu entorno de GCP y haz clic en la pestaña **Cómputo**. Debe existir al menos una VPC antes de que se pueda crear una instancia.

### Agregar una instancia

1. Haz clic en *Agregar una instancia*.
1. En la página *Agregar una instancia*, ingresa los parámetros requeridos para la instancia deseada. Los costos estimados por hora y mes aparecerán en el lado derecho.
1. Puedes optar por permitir el tráfico HTTP (puerto 80) o HTTPS (puerto 443), o ambos. Esto creará una regla de firewall que permitirá el tráfico seleccionado a esta VM.
1. Puedes optar por adjuntar una IP pública a la instancia mediante el menú emergente **Adjuntar IP externa**.
    - **Ningún:** Tu instancia no tendrá una IP pública.
    - **Nueva IP efímera:** A tu instancia se le asignará una nueva IP pública cada vez que se inicie.
    - **Nueva IP estática:** Se reservará una IP pública específicamente para esta instancia, y será la misma cada vez que se inicie.
1. Puedes optar por especificar un script de inicio que se ejecutará cada vez que se inicie la instancia. Ingresa la secuencia de comandos de inicio deseada en el cuadro de texto etiquetado **Automatización - Secuencias de comandos de inicio**. Para las instancias que ejecutan sistemas operativos basados en Unix, esto puede ser un script de shell y para las instancias de Windows puede ser una clave de metadatos, donde el valor es los comandos batch deseados o los comandos de PowerShell.
1. Haga clic en *Aplicar*. La nueva instancia aparecerá en la lista y estará en el estado **Aprovisionamiento**. Una vez que se aprovisionó la instancia, pasará al estado **Funcionando**.

### Obtener detalles de la instancia

1. Desde la pestaña **Cómputo**, haz clic en la instancia. Esto te llevará a la página *Detalles de la instancia*.
    - En la pestaña **Cómputo**, al hacer clic en el nombre o la dirección IP de una instancia, se copiarán esos datos en el portapapeles y *no* te llevará a la página *Detalles de la instancia*.
1. En la página *Detalles de la instancia*, al hacer clic en cualquier cadena se copiará en tu portapapeles.
1. Al hacer clic en *Discos* te llevará a la página *Discos*, donde puedes agregar, cambiar el tamaño, desconectar o eliminar discos en esta instancia. Consulte [GCP: Trabajar con discos e instantáneas](gcp-working-with-disks.md) para obtener más información.

### Detener una instancia en ejecución

1. Desde la pestaña **Cómputo**, haz clic en el menú **Acción** a la derecha de la instancia y seleccione *Detener instancia*.
1. Aparecerá un cuadro de diálogo pidiendo confirmación para continuar. Haz clic en *Aplicar*.
1. La instancia entrará en el estado **Deteniendo**. Una vez que la instancia ha dejado de ejecutarse, entrará en el estado **Terminado**.

**Nota:** Si la instancia no se detiene en 90 segundos, se forzará la detención.

### Iniciar una instancia detenida

1. Desde la pestaña **Cómputo**, haz clic en el menú **Acción** a la derecha de la instancia y selecciona *Iniciar instancia*.
1. La instancia entrará en el estado **Aprovisionamiento**. Una vez que la instancia se está iniciando, entrará en el estado **Funcionando**.

### Eliminar una instancia

Se puede eliminar una instancia en cualquier estado.

**Nota:** Al eliminar una instancia, se eliminará el disco de arranque y también los discos que se adjuntaron a la instancia con la regla de eliminación *Eliminar disco* seleccionada.

1. Desde la pestaña **Cómputo**, haz clic en el menú **Acción** a la derecha de la instancia y seleccione *Eliminar*.
1. Aparecerá un cuadro de diálogo pidiendo confirmación para continuar. Haz clic en *Aplicar*.
1. Si la instancia se está ejecutando, entrará en el estado **Deteniendo**, después del cual se eliminará. Si la instancia ya está detenida, se eliminará de inmediato.

### Conectarse a través de SSH (para las instancias basadas en Linux)

Utiliza este comando para configurar el acceso SSH a la instancia. Se te pedirá que proporciones tu clave pública SSH o que selecciones una clave existente.

  1. En la pestaña **Cómputo**, haz clic en el menú **Acción** a la derecha de la instancia y selecciona **Obtener el comando SSH**.
  1. Aparecerá el cuadro de diálogo **Obtener el comando SSH**.
     - Si ya has configurado una o más claves públicas SSH, aparecerán en el menú emergente con la etiqueta **Clave SSH**.
     - Si no tienes una clave SSH configurada, o si deseas configurar una nueva, selecciona la opción *Nueva clave SSH* en el menú emergente **Clave SSH**, luego ingresa la clave pública deseada en el cuadro de texto etiquetado **Clave pública**.
  1. Haz clic en *Aplicar*.
  1. El cuadro de diálogo desaparecerá. Se creará una regla de cortafuegos que permitirá el tráfico SSH (puerto 22) a esta instancia. Aparecerá una notificación que proporciona el comando SSH que se puede usar para conectarte a la instancia.

**Nota:** Tu cliente SSH ya debería estar configurado con la clave privada para la clave pública que ha seleccionado.

### Conectarse a través de Escritorio Remoto (Remote Desktop, para las instancias basadas en Microsoft Windows)

Utiliza este comando para configurar el acceso de Escritorio Remoto (RDP) a la instancia.

1. En la pestaña **Cómputo**, haz clic en el menú **Acción** a la derecha de la instancia y selecciona *Configurar la contraseña*. Esta operación solo se puede realizar en una instancia en el estado **Funcionando**.
1. Aparecerá el cuadro de diálogo *Configurar la contraseña*. Ingresa su nombre de usuario y haz clic en *Aplicar*.
    **Nota:** Establecer la contraseña para una cuenta que ya existe puede causar la pérdida de los datos cifrados de la cuenta.
1. Momentáneamente, aparecerá una notificación, mostrando la dirección IP de la instancia y las credenciales para iniciar sesión.
1. Configura tu cliente de escritorio remoto con estos parámetros. Ahora puedes conectarte a la instancia.
