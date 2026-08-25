# FUNCIONES PARA FORMULARIOS

ESTAS FUNCIONES LAS COLOCAMOS EN LA PROPIEDAD DE "ONSELECT" DE BOTONES E ICONOS

## FUNCIONES DE CAMBIO DE ESTADO:

   
  ```NewForm(frm_Request)```

  ```ViewForm(frm_Request)```

  ```EditForm(frm_Request)``` 

  


   * La primera función es para poner el formulario en modo "new" y luego navegar hacia el formulario.

   * La Segunda función para poner el formulario en modo "view" y luego navegar a el formulario.

   * La Tercera función para poner el formulario en modo "edit", que se dentro del modo "view" de dicho formulario

   * Es importante definir primero el estado del formulario antes de navegar hacia él o realizar otra acción.

   * Se suele realizar con los modos "new" y "view", ya que el modo "edit" lo cambiamos cuando estamos en el modo "view".

   * Los tres modos ponemos entre parentesis el nombre del formulario

  -----------------------------------------------------------------
  ## FUNCION PARA DEFINIR UN ELEMENTO SELECCIONADO

  ```
  LookUp(
    Requests;
    ID = Gal_Requests.Selected.ID
  )

  ```

   * Necesitamos añadir una función en el formulario para que a la hora de seleccionar un elemento por su ID podemos manejarlo para editarlo o eliminarlo

   * Con esta función que añadimos en la propiedad de "Item" del formulario, buscamos en la tabla que en esta ocasión se llama Requests y la fila cuyo ID sea igual al ID seleccionado


  -----------------------------------------------------------------

  ## FUNCION PARA AÑADIR UN NUEVO REGISTRO O ACTUALIZARLO

  ```
   SubmitForm(frm_Request)
  ```

   * Esta función se coloca en el OnSelect del botón de "Save"

   * Dentro de los paréntesis colocamos el nombre del formulario

  -----------------------------------------------------------------

  ## FUNCION PARA RECTIFICAR EL TEXTO DE UN CAMPO DEL FORMULARIO

  ```
   Choices([@Requests].User)
  ```

* Normalmente todos los campos aparecen con sus nombres de manera correcta, pero si no es así con esta formula lo podemos corregir colocándola en "Items" del campo correspondiente

* En este caso el campo del usuario nos muestra una dirección de correo junto con más símbolos y de esta forma nos muestra sólo el nombre

  -----------------------------------------------------------------

  ## FUNCION ORDENAR POR ID DE MANERA ASCENDENTE

  ```
   Sort(
    pp_Requests;
    RequestID;
    SortOrder.Ascending
   )
  
  ```

* Seleccionamos la galería y en la propiedad de "Items" añadimos esta función.

* Dentro de la función de Sort, ponemos el nombre de la tabla, seguido de la columna por la cual vamos a ordenar y finalmente la manera en la cual vamos a ordenar
   
