# SOLUCIÓN A LA PRÁCTICA A1

## ENUNCIADO
El enunciado pide cumplir con 6 puntos, tras crear con una carpeta correspondiente a un dominio, en la que habrá que crear una aplicación backend.

- - - 

### PRIMER PUNTO
El primer punto habla de un _Front Controller_ (controlador frontal) y dice de él

> ..deberá **utilizar información del servidor** para determinar la ruta solicitada por el usuario en una **petición HTTP**..

#### TEORÍA DEL PRIMER PUNTO
Es importante recordar que el controlador frontal es aquél "ente" de la aplicación backend que atiende al servicio web.  
El controlador frontal es el archivo de la aplicación backend que el servicio web pide ejecutar al servicio de aplicaciones.  
Por lo tanto, el controlador frontal es quien atiende al servicio web cuando este último ha recibido una **petición HTTP**, a la que hemos venido llamando _request_.

#### PLANTEANDO EL PRIMER PUNTO
Si el controlador frontal de las aplicaciones desarrolladas en clase, en un primer inicio usaban un código como 

```
$ruta = $_SERVER['REQUEST_URI'];
```

y ahora nos encontramos con que usan en su lugar 

```
$ruta = $request->getPathInfo();
```

**podemos asumir** sin objeciones que se está obteniendo una información que visiblemente venía del servidor (`$_SERVER`) y que además guarda relación con la _request_ (`$request`).

#### SOLUCIÓN AL PRIMER PUNTO
El primer punto, se resuelve usando cualquiera de los dos códigos vistos en clase que se usaban para obtener el valor que se guardaba en la variable (`$ruta`), ya que ambos utilizan **seguro** información que conocía originalmente el servidor web.

- - - 

### SEGUNDO PUNTO
El segundo punto habla del mismo _Front Controller_ y dice de él

> ..determine **el controlador responsable** de atender una petición como la anterior..

También se explica que
> ..mediante **un componente de enrutamiento**, determine el controlador responsable ..

Y finalmente se dice
> ..determine (..) **la acción a invocar** en dicho controlador.

#### TEORÍA DEL SEGUNDO PUNTO
Sabemos a priori que **de controlador frontal únicamente hay uno**, porque es el "punto de entrada" a la aplicación backend.  

Sabemos también que **la misión de los controladores es la de crear una respuesta a las peticiones** del usuario (_requests_).  

De los componentes de enrutamiento sabemos bien poca cosa, de momento sabemos que **en las aplicaciones backend hay "especialistas" en labores concretas**.  

En estas labores concretas, sabemos que **cada controller se encarga de una página de la aplicación**, y también sabemos que **las páginas tienen una ruta** cada una.  

Finalmente sabemos que **los controladores tienen una acción llamada `indexAction` que muestra la página en su estado por defecto**, y que **las otras acciones muestran la página en otros estados** que atienden a la petición del usuario. 

#### PLANTEANDO EL SEGUNDO PUNTO
Si de controlador frontal solo hay uno, entonces forzosamente se está hablando del mismo que en el primer punto.

No nos extraña que se hable de que habrá un controlador responsable de atender una petición como la del primer punto (una _request_). Es lógico dado que las aplicaciones backend siguen la estructura MVC, y **los controladores son los que crean respuestas** a las _requests_ que se hayan recibido, usando las vistas.

Sobre el componente, habría que aclarar qué significa "**componente**" en términos de programación, y concretamente de programación backend.

Finalmente es lógico pensar que la `$ruta` que aparecía en la solución al primer punto es la guia hacia una página.  
Por ende, la **ruta es la guia hacia el controlador de esa página**.

**Todo esto le da un sentido al _componente de enrutamiento_, que puede ser el especialista en guiar hacia el controlador de la página correspondiente a la ruta**.

Adicionalmente, podemos pensar que el _componente de enrutamiento_ también puede ser el especialista en determinar la acción del controlador que mostrará la página en un estado en concreto. 

#### SOLUCIÓN AL SEGUNDO PUNTO
Partiendo de las anteriores conclusiones sabemos ya que existe una variable `$request` dentro del _front controller_ que representa la petición HTTP dentro de la aplicación.

Por otro lado, carecemos de conocimiento sobre cómo se determinará el _controlador delegado_ pero sabemos que será un _controller_ y también sabemos que quien lo determinará será este "misterioso" componente.

El componente de enrutamiento es un concepto extraño, pero no deja de ser un concepto, por lo tanto, lo podemos representar usando un objeto.

En resumen, partiremos de que **conseguiremos un controlador** gracias al _componente de enrutamiento_ y a la `$ruta`.  
Y en consecuencia, podemos expresar la conclusión alcanzada usando variables que guarden objetos con funciones, y ejecutando estas funciones a nuestra conveniencia.

La solución quedaría:

```
$controlador = $componente_enrutamiento->determinarControlador($ruta);
$accion = $componente_enrutamiento->determinarAccion($ruta, $controlador);
```
