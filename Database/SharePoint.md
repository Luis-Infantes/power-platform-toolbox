
# PASOS PARA CREAR UNA TABLA EN DATAVERSE

1) En primer lugar creamos un sitio nuevo para crear dentro todo lo necesario para la solución con la que vamos a trabajar.
2) Dentro creamos las tablas necesarias y una biblioteca de documentos para almacenar todos esos archivos necesarios para analizar o simplemente archivar.
3) Un vez definido el nombre de la tabla, la creamos y pasamos a añadir y ocultar columnas.
4) No hace falta definir un ID ya que esa columna se crea automáticamente.
5) La columna de "Title" se puede usar si coincide con el nombre de una de las columnas sino es mejor ocultar ya que cambiarla de nombre puede confundir a la hora de definir las fórmulas.
6) Definimos los campos que necesitemos
7) Para crear una relación de 1 => N. En la tabla de N, añadimos una columna del tipo LookUp y la relacionamos con la tabla que necesitemos. La relación se hará de manera automática.

# BIBLIOTECA DE DOCUMENTOS

1) Se utiliza para almacenar todos esos archivos que iremos usando en las aplicaciones
2) Podremos usar agentes para que trabajen con dichos datos
