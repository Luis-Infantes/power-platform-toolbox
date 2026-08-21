# FUNCIONES DENTRO DE UN SWITCH

## FUNCION QUE SEGUN EL MODO DE ESTADO DEL FORM REALIZA UNA ACCION U OTRA

```
Switch(
  frm_Request.Mode;

  FormMode.New;
        Navigate(src_Requests);

  FormMode.Edit;  
      ViewForm(frm_Request)
)
```

* Si el formulario esta modo "New", navegamos a la otra página definida

* Si el formulario esta en modo "Edit", pasamos el mismo formulario al modo "View"

---------------------------------------------------------------
