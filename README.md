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

## Uso como servicio

Para dejar corriendo el software como servicio se recomienda utilizar el software NSSM

1. Crear un script `startInfoWeb.bat` con el siguiente código:

```bash
E: & cd E:\AURA\APP\infoWeb & npm start
```

2. Abrir una consola desde la carpeta del ejecutabla del NSSM, y ejecutar `nssm install infoWeb`.
3. En el campo "Path" de la pestaña "Application" colocar la ruta al archivo `.bat`.
"E:\AURA\APP\startInfoWeb.bat"
4. Presionar install service.
5. Reiniciar el servidor.
6. Verificar que aplicación esté corriendo como servicio en las tareas programadas.

Nota: Otros comandos útiles.

```bash
nssm # ver lista de comandos disponibles
nssm install infoWeb # instalar un nuevo servicio
nssm status infoWeb # ver status
nssm start infoWeb # iniciar servicio
nssm stop infoWeb # detener servicio
```

## Configuración de informes a mostrar e informe inicial

La aplicación permite habilitar/deshabilitar los informes a mostrar al usuario, además del informe que se muestra en la página de inicio. Por ejemplo: en cliente A sólo se muestra informe de frecuencias, en cliente B sólo se muestra informe de eventos.

En el archivo package.json, asignar "true" al informe que se desea habilitar, y "false" en caso contrario. Además, se debe asignar el parámetro "inicio" el nombre del informe a mostrar en la página de inicio ("eventos", "frecuencias" o "estaciones")

```javascript
// Archivo package.json
// ...
  "config": {
    "inicio": "estaciones",
    "eventos": "false",
    "frecuencias": "false",
    "estaciones": "true",
// ...
```

## Links software:

- [nvm para Windows (proyecto)](https://github.com/coreybutler/nvm-windows)
- [nvm para Windows (descarga)](https://github.com/coreybutler/nvm-windows/releases)
- [nssm](https://nssm.cc)

