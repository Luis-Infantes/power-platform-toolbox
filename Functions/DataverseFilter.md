# FUNCIONES PARA FILTROS

## 1) - USANDO BOTONES PARA FILTRAR UNA GALERÍA

1) En la propiedad "OnVisible" de "Screen", definimos una variable para cada caso

   ```
     Set(varStatusFilter; "All Status");; Set(varPriorityFilter; "All Priority")
   ```

2) En la propiedad "OnSelect" de cada botón añadimos la siguiente función

   ```
    Set(varStatusFilter; "All Status")
   ```
   ```
   Set(varStatusFilter; "In Process")
   ```
   ...

3) En la propiedad de "Items" de la Galería, añadimos este conjunto de funciones

   ```
     Sort(
      Filter(
          pp_Requests;
          (varStatusFilter = "All Status" || Text(Status) = varStatusFilter)
          && (varPriorityFilter = "All Priority" || Text(Priority) = varPriorityFilter)
      );
      RequestID;
      SortOrder.Ascending
    )
   ```

4) Dentro de una función "Sort()" para tener los registros ordenador, nombramos la lista con la que trabajamos, seguido de las funciones que se encargan de funcionen los botones de filtrado.


## Notas:

- La formula de filtrado da unos mensajes de advertencia pero funciona bien. Por ahora mantengo esta forma hasta que descubra una manera de filtrar mucho mejora para evitar este tipo de mensajes.

------------------------------------------

## 2) - LOS BOTONES DE FILRO CAMBIAN DE COLOR MIENTRAS SE EJECUTA DICHO FILTRO

1) Definimos una condicional en la propiedad "Fill" de cada botón. Usando la variable en cada caso en función del estado del filtro

   ```

      If(
    varStatusFilter = "All Status";
    ColorValue("#4c97a1");
    ColorValue("#2a4e54")
   )
   
   ```

   ```

      If(
    varPriorityFilter = "High";
    ColorValue("#4c97a1");
    ColorValue("#2a4e54")
   )
   
   ```

## Notas:

- La condicional se ejecuta de la siguiente forma. Si la variables es igual al valor definido tendrá el primer color sino tendrá el segundo color.
