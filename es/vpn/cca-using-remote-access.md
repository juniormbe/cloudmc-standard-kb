---
title: "Conectar a una VPC mediante una VPN de acceso remoto (IKEv2)"
slug: conectar-a-una-vpc-con-vpn-ikev2
---

CloudMC brinda la capacidad de conectarte de forma segura desde tu hogar u oficina a tu VPC. Usando un cliente VPN basado en IKEv2 sobre IPSec en tu plataforma preferida (por ejemplo, Windows, macOS, Ubuntu...), podrás acceder a tus instancias sin tener que pasar por el reenvío de puertos en direcciones IP públicas.

## Configuración de VPC
**Nota:** Para realizar las siguientes operaciones, tu cuenta de usuario debe tener asignada la función de **Editor** o **Propietario** en el entorno de destino.

#### Habilitar acceso VPN
Antes de poder conectarte a tu VPC a través de una conexión VPN de cliente, debes habilitar el acceso VPN en la VPC.

1. Selecciona el entorno informático adecuado.
1. Selecciona la pestaña *Redes*.
1. Desde el elemento de la lista de la VPC de destino, haz clic en el botón *VPN de acceso remoto* para la VPC a la que deseas habilitar el acceso VPN.
1. Haz clic en el menú de acciones y selecciona *Activar* para habilitar el acceso VPN.
1. Después de unos segundos, aparecerá una ventana emergente para confirmar que la VPN ahora está habilitada y encontrarás un certificado que se muestra en la página.

#### Crear cuenta VPN
1. En la página de VPN de una VPC, también se muestra la lista de usuarios de VPN.
1. Haz clic en *Agregar usuario de VPN*.
1. Rellena el formulario *Agregar usuario de VPN*.
1. Haz clic en *Aplicar*.
1. Repite los pasos anteriores para cada usuario de VPN deseado.


## Conexión a VPN
Una vez que hayas configurado correctamente tu VPC para el acceso a VPN y hayas creado al menos un usuario de VPN, ahora estás listo para conectarte a esta VPN para acceder a tus instancias y aplicaciones. Cuando se conecta a una VPC a través de VPN, los clientes tienen acceso a todos sus niveles (hasta 4 subredes).

Se requiere la siguiente información para configurar el cliente VPN:

- **IP pública:** la dirección IP pública de la VPC con la etiqueta con el propósito de "VPN".
- **Certificado IKEv2:** El certificado utilizado para autenticar la VPN remota. Guarda este certificado en un archivo con la extensión **.crt**, por ejemplo `cloud-vpn.crt`. Asegúrete de mantener exactamente el mismo formato y contenido que se muestra en la página.
- **Nombre de usuario:** un nombre de usuario de cuenta VPN válido.
- **Contraseña:** una contraseña de cuenta VPN válida.
