
# TABLAS DE DATAVERSE

1) En la opción "Tablas" de Power Apps, crear desde cero si es que la vamos a crear vacía
2) En el la interfaz de añadir nombre, solo añadimos el nombre y le damos a guardar y salir. Después iremos añadiendo sus columnas y ocultando las que no sean necesarias
3) Definimos una columna de ID del tipo texto para usarlo como referencia de cada registro
4) Definimos los campos que necesitemos

## RELACIONES ENTRE TABLAS

## RELACION 1 => N 

1) La tabla 1 se denomina como maestra y la tabla N como dependiente

2) Primero añadimos a la tabla N una columna del tipo "LookUp" y conectamos con la tabla que deseamos. Dataverse crea la relación de manera automática.

3) Después en la tabla 1 usamos la columna que viene por defecto como "New Column (Principal)", para definir el nombre de la columna que queremos mostrar y sus los datos para que aparezcan en la columna  LookUp de la tabla 1

## RELACION N => N

1) Una tabla tiene una relación de 1 => N con otra y esta otra tiene la misma con la anterior N => 1
  
2) Crearemos una tabla intermedia que conecte ambas tablas y así la relación será de N <=> N

## RELACION 1 => 1

1) No suelen ser frecuentes ya que puedes plantearlo de otra forma para que llegue a ser una relación de 1 => N
