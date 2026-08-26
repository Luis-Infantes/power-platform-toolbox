# FUNCIONES PARA FILTROS

ESTAS FUNCIONES LAS COLOCAMOS EN LA PROPIEDAD DE "ITEMS" DE LA GALERIA

## FUNCION DE FILTRO DE CAMPO BUSQUEDA:

```
Filter(

   Requests;
   (IsBlank(txt_Search.Text) || StartsWith(Title; txt_Search.Text)) 
        
)
```


* Primero: creamos una tabla en Sharepoint o Dataverse, que en este caso tiene el nombre de Request donde se encuentran los datos.

* Segundo: ponemos esta función en la propiedad de "items" de la galería para que filtre la entrada de texto mediante en este caso la columna de "Title". 


--------------------------------------------------------

## FUNCION DE FILTRO DE LISTA DESPLEGABLE:


```
   Filter(

   Requests;
    (drp_Priority.Selected.Value = "Priority" || Priority.Value = drp_Priority.Selected.Value)
        && (dpr_Status.Selected.Value = "Status" || Status.Value = dpr_Status.Selected.Value)
)
```

* Primero: creamos una tabla en Sharepoint o Dataverse, que en este caso tiene el nombre de Request donde se encuentran los datos.

* Segundo: ponemos esta función en la propiedad de "items" de la galería para que filtre a través de dos desplegables que son, "Priority" y "Status".

--------------------------------------------------------


