
# FUNCIONES PARA VARIABLES

ESTA FUNCION EN ESTE CASO LA COLOCAMOS EN LA PROPIEDAD DE "ONSELECT" DE UN BOTON O ICONO

ESTA FUNCION ES PARA QUE SALGA UNA VENTANA EMERGENTE CUANDO INTENTAMOS HACEMOS CLICK EN UN BOTÓN. EN ESTE CASO PARA ELIMINAR UN ARCHIVO

## FUNCIONES DE CAMBIO DE ESTADO DE VISIBILIDAD:

  UpdateContext(
    {
        locShowDeletePopup: true
    }
)

/*
  Primero: creamos un contenedor "vertical" y en la propiedad de "Visible" creamos en este caso la variable locShowDeletePopup (como false por defecto)

  Segundo: en el interior del contener creamos una "label" para el mensaje de alerta y otro contenedor "horizontal" para añadir los botones de "Confirm" & "Cancel"

  Tercero: añadimos esta función en el botón de "Delete", con ese cambio de estado a "true" para que aparezca la ventana

  Cuarto:  en el botón de "Confirm" añadimos la función Remove y en el botón de Cancel añadimos un Switch (Mirar los archivos Remove.md & Switch.md)
*/

--------------------------------------------------------------------------
