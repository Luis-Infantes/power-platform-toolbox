
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

-------------------------------------------------------------------------------

# REGLAS PARA DISEÑAR UNA ESTRUCTURA DE TABLAS EN DATAVERSE

## REGLA 1 - MODELADO DE DATAVERSE

1) Del enunciado sacas las tablas y de esas tablas sacas nuevas que te puedan hacer falta para hacer una primera estructura.

2) Primero pensar en una primera estructura base y luego de poco en poco ampliar el negocio para poder creando o modificando lo que ya tienes.

-----  

## REGLA 2 - DONDE COLOCAR EL CAMPO LOOKUP Y DONDE LA PRIMARY NAME COLUMN

1) Definir bien las relaciones entre las tablas

2) En la tabla N pondremos el LookUp y en la tabla 1 la Primary Name Column (Solo una por cada tabla)

----

## REGLA 3 - TABLAS MAESTRAS Y DEPENDIENTES

1) Una tabla dependiente es una del tipo N donde creamos una columna del tipo LookUp para crear una relación interna con otra tabla

2) La otra tabla pasara a ser la maestra de la tabla N.

3) Una tabla maestra puede ser de varias dependientes, pero a su vez esta puede depender de otra tabla maestra que este por encima de ella.

----

## REGLA 4 - EVITAR DUPLICADO DE LOS DATOS

1) Si en una tabla tienes una columna que quieres que salga en una vista de una app junto con los datos de otra tabla. Con una relación entre tablas es suficiente para que se vea.

2) Replicar estos datos en otra columna de la tabla es una mala practica ya que se intenta evitar duplicados.

----

## REGLA 5 - ANTES DE CREAR UNA TABLA NUEVA. PREGUNTARTE POR QUE ES IMPORTANTE

1) El planteamiento antes de crear una tabla es lo más importante

2) Imagina que relación tendrá y para que se usará.

3) Se suelen crear tablas nuevas para relaciones N <=> N o para ampliar la estructura de la base de datos

----

## REGLA 6 - RELACIONES N <=> N QUE NECESITAN UNA TABLA NUEVA SOLO PARA ESO

1) Para crear una relación del tipo N <=> N se suele crear una nueva tabla que una dos tablas

2) Hay casos en las que una tabla genérica nos servirá para hacer dicha relación, lo cual sería una entidad de negocio.

----

## REGLA 7 - TABLAS PARA RELACIONES N <=> N QUE AL AÑADIR NUEVOS CAMPOS SE CONVIERTEN EN ENTIDADES DE NEGOCIO

1) Como hemos hablado en la regla anterior una tabla ya creada que se use para una relación del tipo N <=> N es una entidad de negocio

2) Una tabla que se crea solo para dicha relación, si en algún momento añadimos nuevas columnas pasará a ser una entidad de negocio también.

----

## REGLA 8 - LOS HISTORIALES PERTENECEN A UNA ENTIDAD

1) Tablas creadas para historiales sobre una serie de datos siempre estarán relacionadas con la entidad que queremos guardar dichos historiales

----

## REGLA 9 - MODELAR SIEMPRE CASOS REALES. LOS RAROS SE PUEDEN SOLVENTAR DE OTRA MANERA

1) Siempre se modelan casos reales, pero si piensas que en una relación puede cambiar de 1 => N a N <=> N por una pequeña posibilidad de cambio. Es mejor mantener la relación 1 => N y resolver ese pequeño porcentaje de otra manera para tener posibilidad de resolverlo por si pasa y también evitar crear una tabla extra solo por esos casos.

