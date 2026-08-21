# FUNCIONES PARA FORMULARIOS

ESTAS FUNCIONES LAS COLOCAMOS EN LA PROPIEDAD DE "ONSELECT" DE BOTONES E ICONOS

1) FUNCIONES DE CAMBIO DE ESTADO:

   

  NewForm(frm_Request) ;; Navigate(src_FormRequests)

  ViewForm(frm_Request) ;; Navigate(src_FormRequests)

  EditForm(frm_Request) 

  

  /*
   Primera funciòn para poner el formulario en modo "new" y luego navegar hacia el

   Segunda función para poner el formulario en modo "view" y luego navegar a el

   Tercera función para poner el formulario en modo "edit"

   Importante definir primero el estado del formulario y luego navegar hacia el mismo

   Se suele realizar con los modos "new" y "view", ya que el modo "edit" lo cambiamos cuando estamos en el modo "view"

   En los tres modos ponemos entre parentesis el nombre del formulario

   En la navegacion ponemos entre parentesis el nombre del "screen" al que navegamos
  */

  -----------------------------------------------------------------
