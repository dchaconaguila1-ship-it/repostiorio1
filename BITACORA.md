## P0
- Mi predicción: El cliente es el navegador, el servidor es el compuatador que espera peticiones y las responde, en la entrada Viaja la solicitud del cliente hacia el servidor y en la salida Viaja la respuesta del servidor hacia el cliente. 
- Lo que pasó:
- Por qué pasó:

## P1
- Mi predicció: en cada ruta veo información distinta según la ruta
- Lo que pasó:en las tres rutas vi "Hola desde el servidor"
- Por qué pasó: el código no revisa req.url, responde lo mismo a todo

## P2
- Mi predicción:Aparecerá solo una línea en la terminal que diga Llegó una petición
- Lo que pasó: Aparecieron dos líneas en la terminal en lugar de una. Una decía GET / y la otra decía GET /favicon.ico.
- Por qué pasó: Pasó porque el navegador hace dos peticiones automáticamente: la primera para pedir la página (/) y la segunda, en segundo plano, para buscar el favicon.ico (el mini logo que sale en la pestaña de la pantalla). Como tu servidor responde a todo, registró ambas solicitudes.

## P3
- Mi predicción: en los dos url botaran error por estar mal escritos 
- Lo que pasó:/actividades/ dio "Ruta no encontrada". Para /ACTIVIDADES: (lo confirmo con la terminal)
- Por que pasó:=== compara el texto exacto, así que un slash de más ya no es igual

## Reflexion 
- El JSON a mano: hubo que escribir setHeader('Content-Type', 'application/json') y JSON.stringify(...) 
- El 404 a mano: tuviste que programar el else con res.statusCode = 404.
- El if/else que crece: cada ruta nueva es otra rama comparando req.method y req.url.

## P4
- Mi predicción: se cae y no responde nada
- Lo que pasó:Express no se cayó, respondió, y me dice Cannot GET /no-existe, que quiere decir “no tengo ninguna ruta para GET /no-existe”.
- Por qué pasó:Express responde 404 por defecto cuando no hay ninguna ruta que coincida con el método y la URL

## Reflexión 2
- Responder JSON: antes setHeader + JSON.stringify se haci a mano, ahora con express  automatizó este proceso con el método res.json()
- El if/else que crece: Express lo resolvió con app.get(), una línea por ruta en vez de una rama comparando req.method y req.url.
- Responder 404: antes yo lo programaba, ahora viene por defecto. 

## P5
- Mi predicción: pueden aparecer errores que afectan al servidor
- Lo que pasó:Lo que pasó: no hubo ningún error ni el servidor se apagó. El navegador se quedó cargando sin mostrar nada, y en la terminal solo salió la línea con la hora y GET /
- Por qué pasó: el middleware no llamó a next(), así que la petición nunca llegó a la ruta, y como el middleware tampoco respondió, la petición quedó sin respuesta
 


