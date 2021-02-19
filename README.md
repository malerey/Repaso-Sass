# Repaso Sass

## Introducción

### Ejercicio 1 - Creando un módulo

### Parte I - Primeros pasos

**Contexto:**
Para nuestro proyecto queremos hacer un botón funcional. Para empezar, creamos un archivo `"index.html"` y otro llamado `"main.scss"`. Luego vamos a ejecutar Sass para que nos cree el archivo dé `"style.css"`.

**Pasos:**

1. Creamos el archivo `index.html` y lo completamos con el contenido mínimo y colocamos un botón con la clase `button` y el texto `"Nuevo boton"`.
2. Creamos el archivo `main.scss` y le damos estilos siguientes estilos:

```scss
padding: 0.35rem;
background-color: #007bff;
color: #fff;
border-radius: 0.25rem;
border: solid 1px #007bff;
```

3. Ahora con la consola compilamos el sass para convertirlo en css, para esto ejecutamos desde la misma carpeta de nuestro proyecto:
   > sass main.scss style.css
4. Si nos fijamos se creó un archivo `style.css`, lo vamos a importar en el html
5. Revisamos que el botón se ve de forma correcta
6. Modificamos el padding a 0.25rem y volvemos a ejecutar el comando sass en la consola.
7. Revisamos que se efectuó el cambio.

### Parte II - Modo observador

**Contexto:**
Se vuelve tedioso ejecutar el comando en la consola por cada modificación.
Para evitar esto vamos a ejecutar sass en modo observador para que cada cambio cuando guardamos me modifique el archivo de css.

**Pasos:**

1. Vamos a ejecutar sass en modo observador
   > sass --watch main.scss style.css
2. Cambiamos el color de fondo y el de borde por el siguiente valor #17a2b8
3. Actualizamos la página en el navegador para ver los cambio realizados.
4. Ahora vamos a cambiar el border-radius por 0.3rem
5. Volvemos a repetir el paso 3.


### Parte III - Conceptos básicos de Sass

### Variables: Ejercicio 1

**Contexto:**

Vamos a crear un título, un párrafo y un span aleatorio. Luego asignaremos algunas propiedades con variables y veremos cómo funcionan.

**Pasos:**

1. Creamos el archivo `index.html`, colocamos las etiquetas con texto aleatorio. Por último importamos el archivo `style.css`, este se genera cuando compilemos el sass.
2. Creamos un archivo `main.scss` y dentro colocamos selectores de tipo para cada parte de los textos.
3. Creamos dos variables que van a ser `$margin:15px` y `$color: blue` en el archivo main.scss;
4. Asignamos las siguientes propiedades a cada etiqueta:

```css
h1{
  color: $color;
  margin:$ margin;
}

p{
  background-color: $color
}

span{
  color: $color
}
```

5. Compilamos el archivo sass a un archivo `style.css` y observamos en el navegador los resultados
6. Cambiamos las variables por lo siguiente `$margin:5px` y `$color: red`
7. Repetimos el paso 5.

### Ejercicio 2

**Contexto:**
Vamos a crear un [badge](https://getbootstrap.com/docs/4.5/components/badge/#contextual-variations), un [button](https://getbootstrap.com/docs/4.5/components/buttons/) y una [card](https://getbootstrap.com/docs/4.5/components/card/#card-styles)

### Parte 1 - Creación de componentes y colores

**Ejercicio**

Crear los componentes card, button y badge. Asigarle una variable de color y luego cambiarla.

**Pasos:**

1. Creamos el archivo `index.html`, colocamos una card con un button y un badge.
2. Creamos los archivos sass que necesitamos.
3. Dentro de la carpeta de sass creamos la carpeta `utils` y dentro el archivo `_variables.scss`
4. Lo importamos en el archivo `main.scss`
5. Le damos estilos a todos los elementos mencionados
6. En el archivo de `variables` creamos 4 variables para los colores
   ```scss
   $primary: #007bff;
   $secondary:#6c757d;
   $background: #f8f9fa;
   $white: #fff;
   ```
7. Ahora asignamos las variables a cada elemento de la siguiente forma:
   a. A la card le colocamos como background-color la variable `$background`
   b. Al button le colocamos de background-color la variable `$primary` y el color `$white`
   c. Al badge le colocamos de background-color la variable `$secondary`
8. Agregamos un título dentro de la card, le asignamos una clase y en el archivo de `card` le asignamos la variable `$primary`
9. Vamos a cambiar los colores, para esto modificamos las variables y las cambiamos por las siguientes:

```scss
	$primary: #ffc107;
	$secondary:#fd7e14;
	$background: #17a2b8;
	$white: #fff;
```

10. Verificamos que los cambios se efectuaron.

### Parte 2 - Box shadow

**Ejercicio:**

Agregar 2 dos variables más para los box shadow, con los siguientes valores:

- shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
- shadow-xl: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);

Ahora asignamos la variable shadow al button y shadow-xl a la card.Luego cambiamos el valor de shadow-xl a `box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);`



## Anidado

### Ejercicio 1

1. Crear un archivo html y pegar el siguiente segmento de código en el body

```html
   <div class="btn-group">
      <button type="button" class="btn">Left</button>
      <button type="button" class="btn">Middle</button>
      <button type="button" class="btn"><span>Right<span></button>
   </div>
   <button type="button" class="btn">Right</button>
```

2. Usando combinadores de espacio vamos hacer que los botones dentro de la clase `btn-group` tengan un color de fondo rojo

```scss
.btn-group {
   .btn {
      background-color: red;
   }
}
```

3. Ahora usando combinadores de hijo directo vamos hacer que el span dentro de un boton tengan un color de fondo azul

```scss
.btn {
   > span {
      background-color: blue;
   }
}
```

4. Ahora usando combinadores de hermanos adyacentes vamos hacer que la etiqueta `button` la letra sea de 36px cuando este seguida de un `div`

``` scss
div {
   + button {
      font-size:36px
   }
}
```

5. Si revisamos el css generado nos quedara algo como lo siguiente:

```scss
.btn-group .btn {
  background-color: red;
}

.btn > span {
  background-color: blue;
}

div + button {
  font-size: 36px;
}
```

### Ejercicio 2

#### Base

Crear un archivo html y pegar el siguiente segmento de código en el body

```html
<div>
  <p><span>Lorem ipsum dolor sit amet.</span></p>
  <p>Lorem ipsum dolor sit amet.</p>
  <p>Impedit quod sit dignissimos ratione.</p>
  <p>Esse suscipit pariatur quibusdam illum.</p>
  <p><span>Lorem ipsum dolor sit amet.</span></p>
</div>
<p><span>Lorem ipsum dolor sit amet.<span>Lorem ipsum dolor sit amet.</span></span></p>
<p><span>A voluptatem nihil deleniti modi!<span>Ut distinctio iusto placeat nisi.</span></span></p>
<h1>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Esse, dolor!</h1>
<p><span>Lorem ipsum dolor sit amet.<span>Lorem ipsum dolor sit amet.</span></span></p>
<p><span>Dolor sapiente dolores earum repellendus.<span>Laudantium rem quia nobis neque?</span></span></p>
```

#### Parte 1

Usando combinadores de espacio en Sass darle los siguientes estilos:

- A las `p` que están dentro del div dar un color de fondo `blue`
- A los `span` que están dentro del div darle un color de fondo `red`

#### Parte 2

Usando combinadores de hijo(>) en Sass dar los siguientes estilos:

- A los `span` que son hijos directos del una etiqueta `p` cambiar el color a un `green`.

#### Parte 3

Usando combinadores de hermanos adyacentes(+) en Sass dar los siguientes estilos:

- A los `p` que son hermanos adyacentes del `h1` cambiar el tamaño de letra por `24px`

#### Parte 4

Usando combinadores generales de hermanos(~) en Sass dar los siguientes estilos:

- A los `p` que son hermanos generales del `div` cambiar el fondo de color por `silver`

## Selector padre

### Ejercicio 1

1. Crean un archivo html y pegar el siguiente segmento de código en el body
```html
   <div class="btn-group">
      <button type="button" class="btn">Left</button>
      <button type="button" class="btn">Middle</button>
      <button type="button" class="btn"><span>Right<span></button>
   </div>
   <button type="button" class="btn btn--primary">Right</button>
```
2. Usando selector padre vamos hacer que los elemento con la clase `btn` tengan el fondo de color rojo dentro del `btn-group`

```scss
.btn-group{
   & .btn{
      background-color: red;
   }
}
```
3. Ahora queremos que `btn` tenga un color verde y cuando le hagamos `hover` cambie el color a violeta

```scss
.btn{
      background-color: green;
      &:hover{
            background-color: violet;
      }
}
```

4. Por ultimo queremos tener una variante de esta con el color azul de fondo. Cambiamos el codigo a:

```scss
.btn{
      background-color: green;
      &:hover{
            background-color: violet;
      }
       &--primary{
          background-color: blue;
      }
}
```
5. Si revisamos el css generado nos quedara algo como lo siguiente:

```css
.btn-group .btn {
  background-color: red;
}

.btn {
  background-color: green;
}
.btn:hover {
  background-color: violet;
}
.btn--primary {
  background-color: blue;
}
```


### Ejercicio 2

#### Base

Crean un archivo html y pegar el siguiente segmento de código en el body

```html
<div class="card">
  <div class="card__header">
    <h3>Soy un card</h3>
  </div>
  <div class="card__body">
    <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Rerum, sapiente.</p>
  </div>
  <div class="card__footer">
    <button class="button button--primary">Aceptar</button>
    <button class="button button--danger">Cancelar</button>
  </div>
</div>
```

# Enunciado

1. Usando el selector padre darle estilo a la card

- Para el `card__header` y el `card__footer` un color de fondo `f3f3f3`
- Para el `card__body` dar el color de fondo `fafbfd`

2. Usando el selector padre darle estilo a los botones

- Para el botón base dar un padding de `16px 8px`
- Dentro de este al `button--primary` dar los siguientes estilos:
  - Color del texto `#ffffff`
  - Color de fondo `#4299e1`
  - Cuando se le haga`hover` que el color de fondo cambie a `#2b6cb0`
  - Cuando está en estado de `active` que el color de fondo cambie a `#2a4365`
- Dentro de este al `button--danger` dar los siguientes estilos:
  - Color del texto `#ffffff`
  - Color de fondo `#f56565`
  - Cuando se le haga`hover` que el color de fondo cambie a `#c53030`
  - Cuando está en estado de `active` que el color de fondo cambie a `#742a2a`

## Integrador 

Utilizando todo lo visto realizar los siguientes maquetados:

![Success Toasts](https://uidesigndaily.com/uploads/1012/day_1012.png)

![Cards](https://uidesigndaily.com/uploads/1117/day_1117.png)

![Blog Cards](https://uidesigndaily.com/uploads/997/day_997.png)

![App List](https://uidesigndaily.com/uploads/1057/day_1057.png)

Recordá que tenes recursos como los siguientes:

* [Unsplah](https://unsplash.com/) para imagenes
* [Google Font](https://fonts.google.com/) para la familia de letras
* [Randomuser](https://randomuser.me/photos) para foto de perfil aleatorias



### Ejercicio 2 - El Patrón 7-1

### Parte 1 - Creación de básica de carpeta

**Contexto:**
Es muy útil usar una arquitectura para facilitar la creación y modificación de un proyecto.Para esto separamos por partes cada pieza y la clasificamos con el fin de que sean independientes y reutilizables. No es necesario que siempre sean 7 carpetas: adaptamos la arquitectura a la profundidad del proyecto. En este caso, nuestro proyecto es sencillo así que no las usaremos a todas. 

El desafío es crear una lista de cards([como esta](https://getbootstrap.com/docs/4.5/examples/album/)). 

**Pasos:**

1. Creamos un archivo `"index.html"`, adentro creamos la estructura base y las clases necesarias para las tarjetas.
2. Creamos una carpeta llamada `"sass"` con las siguientes archivos y carpetas:

```
├─ sass
│    ├─ base
│    │    ├── _typography.scss
│    ├─ components              # Carpeta con archivos parciales por componentes
│    │    ├── _card.scss
│    ├── layout                  # Carpeta con archivos parciales por layouts (secciones de páginas)
│    │   ├── _footer.scss
└── main.scss    # Archivo principal donde se importan los demás archivos parciales
```

### Parte 2 - Importación de archivos y estilos de card

**Contexto:**
Dado que cada archivo va a tener una sola responsabilidad, vamos a tener que importarlo para que se pueda unir al archivo principal.

**Pasos:**

1. En el archivo `"main.scss"` vamos a importar cada uno de los archivos

```scss
@import 'base/typography',
@import 'components/card',
@import 'layout/footer',
```

2. Ejecutamos sass en la consola y lo dejamos en modo observador
   > sass --watch sass/main.scss style.css
3. Importamos en el archivo de html la hoja de estilos.
4. Ahora modificamos el archivo de scss correspondientes a las cards y empezamos a darle estilos.
5. Cuando guardamos refrescamos el navegador y deberíamos ver los estilos aplicados

### Parte 3 - Finalización del modelado

**Contexto:**
Para terminar cambiar los estilos de la tipografía como pueden ser el color y la familia.Y por último agregar un Footer que sea de un color oscuro y que diga `"Creado por su nombre"`

**Pasos:**

1. Modificamos el archivo typography y realizamos lo cambio que creamos necesario
2. Agregamos un footer en el html y le damos las clases en el archivo de footer
