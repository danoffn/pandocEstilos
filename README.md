# Estilos para uso con Pandoc

Contiene los estilos, instrucciones de uso y detalle de pruebas para generar documentos
docx a partir de markdown con pandoc.

## Cómo funciona?

Primero se debe generar un documento con markdown, y luego usar pandoc con una referencia a estilo docx predefinido. Para generar documentos docx con estilos personalizados se debe usar un template de estilos. Se creó un template a partir del template por defecto de pandoc.

```bash
pandoc -o custom-reference.docx --print-default-data-file reference.docx
```

Los templates prdefinidos se alamacenan en la carpeta estilos.

### Modificar los estilos del template

Para modificar un estilo en particular del template, se debe seleccionar la palabra que indica el tipo de párrafo, el tipo de carácter, o tabla y aplicar las características que se deseen (negrita, tamaño letra, etc.), luego se debe actualizar el estilo desde el menú estilo ("Update 'estylo' to Match Selection").

También se pueden modificar directamente en el template las características del header y footer. 

Es útil insertar "Quick parts" para insertar textos en lugares que sería imposible (o difícil) para pandoc modificar. Hasta ahora los Quick parts probados son:

- Title.
- ...


## Requisitos

- pandoc >= 2.7
- Microsoft Office 2016

## Uso

Navegar a carpeta infoWeb y ejecutar aplicación

```bash
pandoc -s ejemplo.md -o salida/ejemplo.docx --reference-doc=estilo/kyber.docx 
```

## Links interesantes:

- [Workflow con pandoc](https://github.com/piero-g/markdown-workflow)
- [Definiendo estilos personalizados para docx/odt](https://github.com/jgm/pandoc/wiki/Defining-custom-DOCX-styles-in-LibreOffice-(and-Word))
- [Manual pandoc (ver --reference-doc=)](https://pandoc.org/MANUAL.html#options-affecting-specific-writers)

