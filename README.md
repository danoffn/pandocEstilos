# Estilos para uso con Pandoc

Contiene los estilos e instrucciones de uso para generar documentos docx a partir de markdown con pandoc.

## Cómo funciona?

Primero se debe generar un documento con markdown, y luego usar pandoc con una referencia a estilo docx predefinido. Para generar documentos docx con estilos personalizados se debe usar un template de estilos. Se creó un template a partir del template por defecto de pandoc.

``` {.bash}
pandoc -o custom-reference.docx --print-default-data-file reference.docx
```

Los templates predefinidos se almacenan en la carpeta estilos. Se deben mover al directorio `$HOME/.local/share/pandoc/` para que pandoc los encuentre por defecto.

### Modificar los estilos del template

Para modificar un estilo en particular del template, se debe seleccionar la palabra que indica el tipo de párrafo, el tipo de carácter, o tabla y aplicar las características que se deseen (negrita, tamaño letra, etc.), luego se debe actualizar el estilo desde el menú estilo ("Update 'estylo' to Match Selection").

También se pueden modificar directamente en el template las características del header y footer.

### Etiquetas YAML

Se pueden insertar (en el footer o header) en el docx las variables almacenadas en las etiquetas de YAML utilizando los "Quick parts". Para ello se debe:

1. Crear las propiedades en el template del docx. Ir a File > Properties > Advances Properties > Custom, y completar los campos "Name" con el nombre de la propiedad y "Value" con el valor temporal y presionar el botón Add.
2. Insertar los quick parts en el template. Para ello ir a:
    - Insert > Quick parts > Fields > DocProperty.
    - Insert > Quick parts > Document Property, en el caso de algunas propiedades como Title y Subject.
3. Crear las etiquetas con el mismo nombre de las propiedades en YAML y agregar su valor/texto.
4. Generar el archivo docx usando Pandoc.
5. Las etiquetas agregados a través de YAML aparecerán en el docx de salida en los Quick parts y en las propiedades en: 
    - En la sección "Document properties" (DP), o. 
    - En la sección "Custom" (CP) de la opción "Advanced Properties".

## Requisitos

-   pandoc \>= 2.7
-   Microsoft Office 2016

## Uso

Navegar a la carpeta donde se encuentra el archivo markdown y ejecutar:

``` {.bash}
pandoc -s ejemplo.md -o salida/kyber.docx --reference-doc=$HOME/App/pandocEstilos/estilos/kyber.docx 
```

## Links interesantes:

-   [Workflow con pandoc](https://github.com/piero-g/markdown-workflow)
-   [Definiendo estilos personalizados para docx/odt](https://github.com/jgm/pandoc/wiki/Defining-custom-DOCX-styles-in-LibreOffice-(and-Word))
-   [Manual pandoc (ver --reference-doc=)](https://pandoc.org/MANUAL.html#options-affecting-specific-writers)
