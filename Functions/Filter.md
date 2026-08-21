# FUNCIONES PARA FILTROS

1) FILTRO DE CAMPO BUSQUEDA:

   Filter(

    Requests;
    (IsBlank(txt_Search.Text) || StartsWith(Title; txt_Search.Text)) 
        
)

/*
Request => es el nombre de la tabla de Sharepoint o Dataverse, donde se encuentran los datos.

La siguiente acción es para filtrar el campo por "Title", cuando se introduce un texto en el mismo. 
*/

--------------------------------------------------------

2) FILTRO DE LISTA DESPLEGABLE:

   Filter(

    Requests;
    (drp_Priority.Selected.Value = "Priority" || Priority.Value = drp_Priority.Selected.Value)
        && (dpr_Status.Selected.Value = "Status" || Status.Value = dpr_Status.Selected.Value)
)

/*
Request => es el nombre de la tabla de Sharepoint o Dataverse, donde se encuentran los datos.

En esta ocasión filtramos a través de dos desplegables que son, "Priority" y "Status".
Los filtros pueden actuar en conjunto.
*/
