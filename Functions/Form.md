# FUNCIONES PARA FORMULARIOS

ESTAS FUNCIONES LAS COLOCAMOS EN LA PROPIEDAD DE "ONSELECT" DE BOTONES E ICONOS

## FUNCIONES DE CAMBIO DE ESTADO:

   
  NewForm(frm_Request) ;; Navigate(src_FormRequests)

  ViewForm(frm_Request) ;; Navigate(src_FormRequests)

  EditForm(frm_Request) 

  


   * La primera función es para poner el formulario en modo "new" y luego navegar hacia el formulario.

   * La Segunda función para poner el formulario en modo "view" y luego navegar a el formulario.

   * La Tercera función para poner el formulario en modo "edit", que se dentro del modo "view" de dicho formulario

   * Es importante definir primero el estado del formulario antes de navegar hacia él.

   * Se suele realizar con los modos "new" y "view", ya que el modo "edit" lo cambiamos cuando estamos en el modo "view".

   * Los tres modos ponemos entre parentesis el nombre del formulario

   * En la navegacion ponemos entre parentesis el nombre del "screen" al que navegamos
  

  -----------------------------------------------------------------
