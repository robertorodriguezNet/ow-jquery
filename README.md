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

### SELECTORES JQUERY

- `:eq(index)(eq() actual)`
- `:has("")`
- `:contains("")`
- `:even / :odd`
- `:input` (inputs, textarea, select, buttons)
- `:gt(index) / :lt(index)` mayor/menor que
- `:first / :last` (.first(), .last() actual)
- `:button, :file, :radio, :reset`
- `:submit, :text, :checkbox`
- `:password, :image`
- `:header` (hx)
- `:hidden, :visible`
- `:parent` selecciona aquello que tiene algo dentro

```js
<script>

    $(function(){
                
        $(":password");                  // seleccionar passwords
        $(":text");            // seleccionar inputs de tipo text
        $(":h1");                     // seleccionar cabeceras h1
        $(":header");           // selecciona todas las cabeceras

        $("img:visible").hide(); // ocultar las imágenes visibles
        $("img:hidden").show();   // mostrar las imágenes ocultas

    });
</script>
```

## Each() and $(this)

![Each and $(this)](img/each-this.png)

### Recorrer una lista

```js
<script>

    $(function(){

        // Muestra el texto de cada elemento y lo cambia posteriormente
        $("li")each(function(index)){
            console.log("El elemento " + index + " contiene " + $(this).text());
            $(this).text("HOLA");
        }

    });

</script>
```

## CSS

```js
<script>

    $(function(){

        let valor = $("algun-selector").css("propiedad");
        $("algun-selector").css("propiedad","valor");

        // Establecer el valor de una propiedad para todos los elementos 
        // (una función para cada elemento devuelto por el selector).
        // En index está la posición en la lista de elementos devuelta por
        // el selector,y en value, el antiguo valor.
        $("algun-selector").css("propiedad",function(index,value){
            // $(this)
        });

        let color = $("li").css("color");  // Se devuelve el primer elemento encontrado
        $("img").css("width","+=50");

        // OBTENER el valor de varias propiedades DEL PRIMER ELEMENTO
        // que se obtiene del selector (array)
        let props = $("algun-selector").css([
            "propiedad1",
            "propiedad2",
            "propiedadn"
        ]);

        let colores = $("li").css(["color","background-color"]);

        // ESTABLECER el valor de varias propiedades para los
        // elementos seleccionados.
        // Entre las llaves se escribe el CSS con su propia sintaxis.
        $("algun-selector").css({
            prop1 : valor, // o expresión
            prop2 : valor, // o expresión
            propn : valor, // o expresión
        });

        $("li").css({
            color: #fff,
            background-color: #000;
        });


    });

</script>
```

### Funciones CSS adicionales

```js
<script>
    $(function(){

        // Getter y setter para algunos valores
        // $("...").width(); $("...").width(value);
        // $("...").height(); / $("...").height(value);
        $("img").eq(4).width("20px");
        $("img").width("20px");

        let size = $("img").eq(0).height();



    });
</script>
```

### Clases CSS

Para los elementos seleccionados:\
`.addClass()`\
`.removeClass()`\
`.toggleClass()` pone o quita la clase dependiendo de si la tiene o no.\
`.hasClass()`

```js
<script>
    $(function(){

        // Añadir varias clases
        $("button").addClass("btn btn-error");

        // Le pasamos una función que se aplica a cada elemento (con una
        // posición) y cuyo valor srá el nombre de la clase que se añade ($(this)).
        // Devuelve el nombre de la clase que se quiere añadir.
        $("section").addClass(funtion(index){
            return "section-" + index;
        });

        let has = $("tbody tr:first td").hasClass("una-clase");

    })
</script>
```

### Atributos CSS

- **Atributo**: nos da información adicional sobre un elemento HTML, con la forma nombre="valor".
- **Propiedad**: es información de la instancia concreta de una etiqueta, dentro de un DOM determinado.

!["ropiedades y atributos](/img/prop-vs-attr.png)

#### Funciones para trabajar con atributos y propiedades

- No usar versiones anteriores a jQuery 1.6.
- Usar siempre que sea posible las funciones que hacen referencia a las propiedades.
- Usar .attr() únicamente cuando sean atributos *_custom*, es decir que no van a tener propiedades asociadas.

`.attr()`\
`.removeAttr()`\
`.prop()`\
`.removeProp()`

```js
<script>
    $(funtion(){
        // Obtener el valor del un atributo del primer elemento
        // let valor = $("algun-selector").attr("algun-atributo");
        let url = $("a").attr("href");

        // Fijar el valor de un atributo concreto en todos los
        // elementos seleccionados
        // $("algun-selector").attr("algun-atributo","nuevo-valor");
        $("a").attr("targe","_blank");

        // Fijar el valor de varios atributos a la vez en todos
        // los elementos seleccionados
        // $("algun-selector").attr({
        //     atr1 : value1,
        //     atr2 : value2,

        //     atrn : valuen,
        // });
        $("#miprofile").attr({
            alt   : "Foto de mi cara",
            title : "Foto hecha por mí"
        });

    });
</script>
```

### Modificar el DOM

- `.empty() / .html() / .text()`
- `.append() / .preprend() / .appendTo() / .prependTo()` añaden nuevos elementos HTML, al principio y al final.
- `.addClass() / .removeClass()`
- `.wrap() / .unwrap() / .wrapAll() / .wrapInner()` envuelve el contenido entre etiquetas
- `.val() ->` obtener y fijar campos de formulario

```js
<script>
    $(function(){

        // Borra todos los hijos (y su contenido) de los elementos seleccionados
        $(".article li:nth-child(3)").empty();

        // OBTIENE el HTML del primer elemento de los seleccionados.
        // Es decir, TODO lo que va entre la apertura y cierre del elemeto.
        let content = $("li").html();

        // SUSTITUYE el contenido de todos los elementos seleccionados
        $("ul").html("<li>UNO</li>");

        // Posición y antiguo texto si se pasa una función
        $("ul").html(function(index,oldtext){
            // Añadir un elemento al contenido
            $(this).html(oldtext + "<li>Nuevo elemento</li>");
        });

        // .text() y .html() son parecidos: .text() obvia las etiquetas.

        $("ul").append("<li>Nuevo elemento</li>");
        $("<li>Nuevo elemento</li>").appendTo("ul");

        // Envolver el contenido entre etiquetas
        $("article").wrap("<div class="article_outer"></div>");

        let valor = $("algun-selector").val();
        $("algun-selector").val("valor");
        $("input[type=text ]").val(function(index,valor){
            $(this)val(valor + "->" + index);
        });
        let nombre = $("input").eq(0).val(function(index,valor){
            return valor + "...";
        });

    });
</script>
```

## EVENTOS

- Eventos de navegador
- Eventos de usuario

|              | Eventos      |               |               |
|--------------|--------------|---------------|---------------|
| .focusout()  | .hover()     | .keypress()   | .keydown()    |
| .keyup()     | .mousedown() | .mouseenter() | .mouseleave() |
| .mousemove() | .mouseout()  | .mouseover()  | .resize()     |
| .scroll()    | .select()    | .submit()     |               |  

### Objeto Event

- `e.delegatedTarget` si se ha producido asocición delegada.
- `e.currentTarget` objeto que lanza el evento.
- `e.pageX` posición X en la que se ha producido el evento.
- `e.pageY` posición Y en la que se ha producido el evento.
- `e.preventDefault()` evita el comportamiento por defecto.
- `e.stopPropagation()` detiene la propagación del evento.
- `e.Target` donde se ha producido el evento.
- `e.timeStamp` momento en el que se ha producido.
- `e.type`
- `e.which` tecla presionada o clic del ratón.
- `e.metaKey` teclas especiales (por ejemplo en Mac).

![Event bubbling](/img/event-bubbling.png)

En la imagen:

- `li` y `body` tienen un `handle`.
- El evento lo captura `li` y se propaga hacia arriba.
- El evento es ejecutado por cada elemento que tiene su `handle`.

```js
<script>
    $(function(){

        let count = 0;

        // Asociación directa
        $("li#ejemplo").on("click mouseenter",function(event){
            $(this).html("Contador: " + (++count);)
        });

        // Asociación delegada
        // Eventos, elemento hijo al que se aplica el evento
        $("ul").on("click mouseenter","li#ejemplo",function(event){
            $(this).html("Contador: " + (++conut));
        })

        // Funciones con nombre, solo asociación directa
        $("li#ejemplo").click(function(event){
            $(this).html("Contador: " + (++count));
        });

    })
</script>
```

## Control de propagación de eventos

- `event.preventDefault()` evita el comportamiento por defecto.
- `event.stopPropagation()` para la propagación hacia arriba.
- `event.stopImmediatePropagation`  para el resto de los handlers y la propagación hacia arriba.\
  Por ej.: se captura un `mouseover` y entonces se deshabiliata el `mouseclic`.

### Disparar eventos

```js
<script>
    $(function(){

        // HAY PROPAGACIÓN
        // Simular que se ha producido un evento en los elementos del selector
        $("alugun-selector").trigger("algun-evento");

        // El argumento puede ser un Evento
        $("algun-selector").trigger(event);

        // NO HAY PROPAGACIÓN
        // El evento debe tener handler asociado
        // Se ejecutan todos los handlers asociados al evento
        $("algun-selector").triggerHandler("algun-evento");
        
        // Se ejecutan los handlers asociados a un objeto del tipo evento
        $("algun-selector").triggerHandler(event);
    });
</script>
```

### Eventos propios

```js
<script>
    $(funtion(){
        $("algun-selector").on("mi_evento"...);

        // Usado como trigger
        $("algun-selector").trigger("mi_evento");
        $("algun-selector").triggerHandler("mi_evento");
    });
</script>
```

## AJAX

## Algunas funcione AJAX y su equivalencia en jQuery

- `$.ajax()` / `$jQuery.ajax()`
- `$.ajaxgetJSON()` / `$jQuery.getJSON()`
- `$.ajaxSetup()` / `$jQuery.$ajaxSetutp()`
- `$.ajaxget()` / `$jQuery.ajaxget()`
- `$.ajaxpost()` / `$jQuery.post()`

```js
<script>
    $(function(){

        // settings (opcional)
        // {
        //      async: true; --> especifica que la carga sea asíncrona.
        //      contentType: 'application/x-www-urlencoded; charset=UTF-8';
        //      data: ... ; --> argumentos para petición / url qery / json.
        //      dataType: "xml" / "html" / "json";
        //      header: ... ; --> argumentos de la cabecera / json.
        //      method: "get" | "post";
        //      statusCode: lista de funciones dependiendo del estado (objeto json).
        //      success: function(data, textStatus, jqXHR); --> en caso éxito.
        //      error: function(jqXHR, textStatus, error); --> en caso de error.
        //      complete: function(jqXHR)
        // }

        // Estructura general simplificada.
        // Se pasa la url y un json con todas las funciones necesarias.
        
        // Al hacer click en un componente de la clase users
        $(".users").on("click", function(event){

            // Vaciar la lista de usuarios
            $("ul.lista_usuarios").empty(); 

            // Iniciar AJAX
            $.ajax("https://jsonplaceholder.typicode.com/users",{
                dataType: 'json',
                success: function (data){  // data contiene todos los datos devueltos
                    data.forEach(function(valor){
                        $("ul.lista_usuarios")
                            .append("<li><span class="oculto">" + 
                                valor.id + "</span>" + valor.name + "</li>")
                    });
                },
                error: function(jqHXR, textStatus, error){
                    alert("Error: " + textStatus + " " + error);
                }

            }); // Fin de iniciar AJAX
        });  // Fin del evento onClick
    });
</script>
```

## jQuery UI

### Instalación

- Instalación de la librería por defecto (local|remota).
  - local
    - Descargar jQuery UI desde [https://jqueryui.com](https://jqueryui.com)
    - Enlazar tanto los estilos como el *js* descargado (quedarse con los **min**).
  - remota
    - Copiar CDN: [https://developers.google.com/speed/libraries?hl=es-419#jquery-ui](https://developers.google.com/speed/libraries?hl=es-419#jquery-ui)
- Instalación personalizada.
  - Desde la página de descarga, seleccinar **Custom download**.
- Temas de jQuery.
  - En la página de **jqueryui** ir a la pestaña **Themes** [https://jqueryui.com/themeroller/](https://jqueryui.com/themeroller/) y descargar el tema elegido.

### Componentes

Son elelmentos que son comunes y constan de estructura, estilos y comportamiento.\
Están documentados y preparados para ser reutilizados.\
Son *plantillas* de elementos web.

| Algunos   | Componentes    |         |               |              |
|-----------|----------------|---------|---------------|--------------|
| Acordeón  | Autocompletado | Botones | Checkboxradio | Controlgroup |
| DatePicker| Dialog         | menu    | ProgressBar   | SelectMenu   |
| Slider    | Spinner        | Tabs    | ToolTips      |              |

### Efectos

| Algunas        | Funciones      |           |                |
|----------------|----------------|-----------|----------------|
| .addClass      | .removeClass() | .hide()   | .toggleClass() |
| Color anination| .show()        | .toggle() | .easing()      |
| .effect        | .switchClass() |           |                |

### Interacciones

- **Draggable**: mover elementos.
- **Dropable**: soltar los elementos.
- **Resizable**: redimensionar los elementos.
- **Selectable**: seleccionar uno o varios elementos.
- **Sortable**: reordenar los elementos.
