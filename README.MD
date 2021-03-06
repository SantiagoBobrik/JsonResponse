# JsonResponse

## Intro

JsonResponse es una clase utilitaria, la cual nos permite estandarizar las respuestas HTTP.

## Namespace:

En el namespace **Helper**  vamos a poder acceder a la clase 

```php
use Helper\JsonResponse;
```

## Metodo withJson

El metodo withJson es un metodo estatico de la clase que recibe 3 parametros, el objeto **$response**, el status code **HTTP** y como ultimo parametro el objeto data de la respuesta **HTTP,** siendo este ultimo un parametro opcional que esta atado a los estandares Axon respecto de los status code.

```php
//Empty response
JsonResponse::withJson($response, 400);

//Data Response
$data = ["users"=> [...] ];
JsonResponse::withJson($response, 400,$data);
```

## Response

La repuesta HTTP tiene dos formatos claros.

### Error

```json
//Status code 404
{
	"error" :  "Not Found",
	"timestamp" : "02:15:13am"
}
```

### Success

```json
//Status code 200
{
  "name": "Pepe",
  "lastName": "Pepito"
}
```

## Default Response

Para la mayoria de los status code la clase implementa mensajes de respuesta estandarizados, como por ejemplo:

```php
JsonResponse::withJson($response, 404);
//Not Found
```

## Custom Response

Tambien si en un determinado momento de la aplicacion queremos pisar el mensaje por default que tiene un determinado status code, lo podemos hacer mediante el tercer parametro de la funcion **withJson,** indicandole el nuevo mensaje.

```php
JsonResponse::withJson($response, 404, "Mensaje personalizado");
```

Teniendo como resultado:

```json
//Status code 404
{
	"error" :  "Mensaje personalizado",
	"timestamp" : "02:15:13am"
}
```

#
