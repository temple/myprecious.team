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
