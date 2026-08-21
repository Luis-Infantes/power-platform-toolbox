# FUNCIONES PARA REMOVE

## FUNCION PARA ELIMINAR UN REGISTRO A TRAVES DE SU ID

```
Remove(
    Requests;
    LookUp(
        Requests;
        ID = Gal_Requests.Selected.ID
    )
)
```

* Dentro de la función nombramos la tabla a la que nos dirigimos

* Escribimos una nueva función del tipo "LookUp", donde volvemos a nombrar a la tabla a la que nos dirigimos

* Seguido del ID del archivo seleccionado de la galería de la app.
