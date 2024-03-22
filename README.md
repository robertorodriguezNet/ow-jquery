# jQuery

## Instalación de jQuery

### En local

Página de descarga: [https://jquery.com/download/](https://jquery.com/download/)\
Se descarga la versión comprimida (min.js) y se guarda en un directorio accesible desde la web.\
El enlace al archivo js desde la cabecera de la web se coloca en el `head`.

```html
<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instalación local</title>
    <script src="js/jquery-3.7.1.min.js"></script>
</head>

<body>
    <h1>Instalación de jQuery en local</h1>

    <script>
        $(function(){

        });
    </script>
</body>

</html>
```

### En remoto

Se hace uso de los **cdn** de **Google** como librería, no como servicio.\
[https://developers.google.com/speed/libraries?hl=es-419](https://developers.google.com/speed/libraries?hl=es-419)

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>jQuery remoto</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
</head>
<body>    
    <h1>Instalación de jQuery en remoto</h1>

    <script>
        $(function(){

        });
    </script>
</body>
</html>
```

### Comprobar si jQuery se ha cargado

Ejecutar en la consola:

```js
$();
```

o

```js
jQuery
```

### Ejecución de las funciones con jQuery

Al final del body se carga el script

```js
<scrip>
    $(document).ready(function(){
        ...
    });
</script>
```

o

```js
<script>
    $(function(){
        ...
    });
</script>
```

## SELECTORES

```js
<script>
    $(function(){
        
        // $("selector").accion()
        $("*").hide();     // Selector universal. Esconde todo.
        $("img").hide();         // Oculta los elementos <img>.
        $("img").eq(1).hide();     // El primer elemento <img>.
        $("th#ejemplo").hide();  // Oculta th con id "ejemplo".
        $(".card").hide();           // Oculta la clase "card".
        $("h1,h2,h3").hide(); // Selección de varios elementos.
        $("input[type='text']").hide(); // Input de tipo texto.

    });
</script>
```

### PSEUDO-SELECTORES

```js
<script>
    $(function(){
        
        // :hover
        // :visited
        // :first-of-type / :first-child
        // :last-of-type / :last-child
        // :nth-of-type / :nth-child
        // :required
        $("ul.iconos .li:first-child").hide();
        $("ul.iconos .li:nth-child(3)").hide();

    });
</script>
```

### SELECTORES CSS

```js
<script>

    $(function(){
        
        // seleccionar la primera columna del cuerpo de una tabla
        $("tbody tr td:first-child");
        $("tbody tr rd:fist-of-type");

        // El primer elemento de una lista
        $(".iconized li:nth-child(1)");
        $(".iconized li").eq(0);

        // El campo de un formulario anterior al submit
        $("input:last-of-type");

        // El último elemnento de una lista poner en rojo
        $(".iconized li-last-cild").css("color","red");

        // La última imagen de una página
        $("body img:last-of-type");

        // La primera letra de un hx
        $("h1:first-letter").css("transform","upper");

    });
</script>
```
