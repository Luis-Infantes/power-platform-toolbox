# FUNCIONES DENTRO DE UN SWITCH

## FUNCIONES QUE SE EJECUTAN SEGUN EL ESTADO DE UN "FORM" Y PARA UN BOTON DEL TIPO "CANCEL"

```
Switch(
  frm_Request.Mode;

  FormMode.New;
        Navigate(src_Requests);

  FormMode.Edit;  
      ViewForm(frm_Request)
)
```


* En este caso el uso  de este Switch será para depende del estado del formulario.

* Si el formulario esta modo "New", navegamos a la otra página definida

* Si el formulario esta en modo "Edit", pasamos el mismo formulario al modo "View"

---------------------------------------------------------------
