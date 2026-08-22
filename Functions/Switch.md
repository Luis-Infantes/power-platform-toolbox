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

## FUNCION PARA CAMBIAR UN TEXTO EN BASE AL MODO DE ESTADO DEL FORMULARIO

```
  Switch(
    frm_Request.Mode;
    FormMode.New; "New Request";
    FormMode.Edit; "Edit Request";
    FormMode.View; "Request Details"
)
```

* Definimos en base a que vamos a realizar las condicionales, que en este caso es al modo del formulario

* Según el modo en el que se encuentre el formulario aparece un texto u otro
