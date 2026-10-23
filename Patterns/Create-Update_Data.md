# POWER APPS - POWER AUTOMATE - SHAREPOINT - AZURE 

- Creamos una Power App para crear o actualizar datos en una lista de Sharepoint
- Las imágenes se van a almacenar en un Blob de Azure.
- Un flujo de Power Automate va almacenar las imagenes en el blob y nos devolverá una url seguido del nombre del archivo, la cual junto con el resto de datos almacenaremos en la lista de Sharepoint.

## CREACIÓN DE LA LISTA DE SHAREPOINT

1) Creamos un sitio para nuestro proyecto y las listas necesarias.
2) Para este ejemplo de proceso nos centramos en la lista de "Certificates"
3) Esta compuesta por varias columnas de texto y número
4) La columna donde guardaremos las imágenes son de tipo texto

-------------------------------------

## CREACIÓN DE CUENTA DE ALMACENAMIENTO EN AZURE

1) Entramos en nuestra cuenta de azure
2) Creamos una cuenta de almacenamiento con minúsculas y usando el grupo de recursos que ya tenemos creado o creamos uno nuevo si no lo tenemos
3) Servicio principal => Azure Blob
4) Rendimiento => Estandar
5) Redundancia => Local
6) Los creamos y después en configuración lo cambiamos a acceso publico
7) Creamos un contenedor con el nombre que queramos asignar pero en minúsculas también
8) Accedemos al contenedor para cargar los primeros archivos.
9) En avanzado podemos crear una carpeta virtual para poder organizar mejor las imágenes por secciones. Cargamos los archivos que queramos y creamos
10) Como son pocos archivos los he cargado a mano, pero se podrían cargar unos pocos luego dejar todo listo para hacerlo con la app.
11) Cada imagen cargada al pinchar sobre ella nos dará una URL que colocaremos en el campo de imagen de la lista de "Sharepoint".

----------------------------------------

## DISEÑO Y CREACIÓN DE LA POWER APP

1) Para esta parte solo voy a nombrar la parte de la app donde vamos a trabajar en la creación y actualización de los datos.
2) Para añadir un nuevo registro.
3) Tenemos un formulario conectado con la lista de sharepoint
4) Dentro de la "DataCard" donde va el campo de la imagen, añadimos un elemento de carga de imagenes
5) El elemento consta de un botón y una imagen temporal de lo que hemos seleccionado
6) En "DataCard" de la imagen del formulario. En la propiedad de "Update" ponemos el nombre de "VarUrl"
7) Si da error no pasa nada ya que es el nombre de una variable que vamos a crear en la siguiente fase
8) El botón de "Save", encargado de añadir los datos del nuevo registro deberá ir de la siguiente forma

```
  Set(
    VarUrl;
    AddImageCertifications.Run(
        cert_AddMedia.FileName;
        {
            contentBytes: cert_AddMedia.Media;
            name: cert_AddMedia.FileName
        }
    ).urlresultado
);;

SubmitForm(Form_List_Certificates);;

Navigate(Certificates_Screen)

```
1) Con "Set" creamos la variable que hemos añadido antes en "DataCard" antes.
2) Ejecutamos el nombre del flujo de Power Automate  con .Run()
3) Nos pide el flujo dos variables. Una de texto y otra de archivo
4) Pues la primera es el nombre de la viable de texto
5) La segunda un objeto donde incluimos el archivo seguido del nombre del archivo.
6) El .urlresultado es el nombre de la variable final que añadimos en el paso final del flujo
7) De esta forma añadimos la imagen al blob y nos devuelve el nombre que incluye en esa "URL" que añadimos en ese último paso
8) Con SubmitForm, lo que hacemos es que tras tener esa "URL", añadimos este datos junto con los demás campos a la lista de "Sharepoint".
9) Finalmente navegamos hacia otra pantalla, que en esta caso es la principal de "Certificates", para verificar que los datos aparecen igual que los demás registros.

----------------------------------------

## DISEÑO Y CREACIÓN DEL FLUJO DE POWER AUTOMATE

1) Se recomienda crear el flujo desde Power Automate y luego conectarlo con la app
2) Flujo instantáneo con un trigger de Power Apps cuando se llama al flujo
3) Definimos dos variables
4) De tipo texto llamada "FileName"
5) De tipo archivo llamada "FileConect"
6) Como siguiente paso añadimos "Crear Blob"
7) Nos pedirá el acceso con lo cual debemos hacer lo siguiente
8) Añadir el nombre de la cuenta de almacenamiento
9) Añadir la cadena conexión de esta cuenta que conseguiremos en Azure
10) De la key que nos dan debemos copiar después de "AccountKey=" y hasta justo después de "==" sin llegar a coger el ;
11) Le damos a confirmar y nos debería de conectar y llevar a otro menú donde lo rellenamos de la siguiente forma.
12) Nombre de la cuenta de almacenamiento
13) Ruta hacia la carpeta donde vamos a añadir los archivos
14) En nombre del blob ponemos de manera dinámica la variable de texto
15) En contenido del blob ponemos de manera dinámica la variable del archivo
16) Como siguiente y ultimo paso añadimos un conector que sea de Power App, cuando responde a un flujo
17) Creamos una variable de entorno de tipo text y la hemos llamado "UrlResultado"
18) En el contenido añadimos la "URL" estándar de cualquier imagen que hemos añadido a la carpeta anteriormente a mano pero quitamos el nombre del archivo para poner depues de "/" de manera dinámica la variable de texto creada en el primer conector. La cual es el nombre del archivo que vamos a agregar.
19) Finalmente guardamos el flujo. 


