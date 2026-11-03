# POWER AUTOMATE + POWER APPS + AZURE + SHAREPOINT

## Diseño de dos flujos de Power Automate cuya función es el borrado de un archivo en Azure Blob Storage para su posterior reemplazo por el nuevo. Gestionado con Power apps y finalmente añadimos en nuevo enlace en Sahrepoint.

## DeleteBlobFile

### When Power Apps calls a flow:

- BlobPatch (Text) => Variable encargada de capturar el nombre del archivo

- FolderPath (Text) => Variable encargada de capturar el nombre del directorio en donde se encuentra el archivo


### Delete Blob:

- Storage account name or blob endpoint => Conectamos con el nombre de la cuenta de almacenamiento que hemos dado en Azure. Tendremos que dar los permisos necesarios si es la primera vez.

- Blob => conectamos con el nombre del contenedor y añadimos las variables de manera dinámica

```
  /NOMBRESTORAGE/FolderPath/BlobPath

```

----------------------

## UploadFileBlob

### When Power Apps calls a flow:

- FileName (Text) => Variable encargada de capturar el nombre del archivo

- FileContent (File) => Variable encargada de recibir el contenido del archivo

- FolderPath (Text) => Variable encargada de capturar el nombre del directorio  donde se almacenará el archivo


### Create Blob:

- Storage account name or blob endpoint => Conectamos con el nombre de la cuenta de almacenamiento que hemos dado en Azure. Tendremos que dar los permisos necesarios si es la primera vez.

- Folder Path => conectamos con el nombre del contenedor y añadimos la variable "FolderPath" de manera dinámica.

- Blob name => FileName

- Blob Content => File Content contentbytes

### Respond to a Power App or flow:

- UrlResult (Text) => Variable encargada de devolver la URL que posteriormente almacenaremos en Sharepoint.

--------------------

## Con estos dos flujos creados ya tenemos la parte de automatización entre Power Automate y Azure. Ahora como siguiente paso vamos a usarlos en Power Apps.

1) En la Power App añadimos los flujos
2) En el botón de Save o Upload del formulario donde vamos a realizar la actualización de esos datos junto con imágenes añadimos estas funciones en la propiedad "OnSelect"

```

   If(
    !IsBlank(cert_AddMedia.Media);

       // Borra la imagen anterior del Blob antes de subir la nueva. Extrae el nombre del archivo de la url guardada en el campo para poder eliminarlo
    If(
        !IsBlank(cert_img_DataAddMedia.Text);
        DeleteBlobFile.Run(
            Last(Split(cert_img_DataAddMedia.Text; "/")).Value;
            "certifications-documents"
        )
    );;

    Set(
        VarCertImageUrl;
        UploadFileToBlob.Run(
            cert_AddMedia.FileName;
            {
                contentBytes: cert_AddMedia.Media;
                name: cert_AddMedia.FileName
            };
            "certifications-documents"
        ).urlresult
    )
);;

SubmitForm(Form_List_Certificates);;

Notify(
    "Request update successfully";
    NotificationType.Success
);;

Refresh(Certifications);;
Navigate(Certificates_Screen)

```

### Descripción del método:

1) Definimos una condicional de que en caso de que el campo este ocupado, se ejecute lo siguiente
2) Ejecutamos el flujo de eliminación del archivo pasando todos esos parámetros necesarios en este caso.
3) Luego ejecutamos el siguiente flujo para que actualice el archivo y nos devuelva esa URL necesaria
4) Con submitForm añadimos todos los datos a la lista de Sharepoint
5) En caso de que todo haya salido correctamente lo notificamos con Notify
6) Refrescamos la base de datos para que se vean los nuevos cambios
7) Y navegamos hacia la galería para visualizar todos esos cambios





