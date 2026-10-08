p1 rta: lo que sucede con navegador /, luego /hola y luego /lo-que-sea. es que muestra el hola en todas por que el servidor no esta buscando mas rutas.

*p2 Abres UNA sola página en el navegador. ¿Cuántas líneas "Llegó una petición" van a aparecer en la*
*terminal? Cuando ejecutes, lee con atención qué URL aparece en cada línea.*

rta: lo que sucede es que llegan las lineas que dicen 'Llegó una petición: GET /actividades' esta la informacion extra que se añade en el navegador 

*p3¿Qué responde el servidor si pides /actividades/ (con slash al final)? ¿Y /ACTIVIDADES?*

rta: lo que sucede en los dos casos es que da un error 404 porque esas rutas no se encuentran habilitadas o con texto en ellas

**reflexion** 
*Enrutamiento manual:* Evaluar URLs y métodos HTTP con condicionales (if/else) es tedioso y propenso a errores.
*Lectura del body:* Procesar datos POST/PUT requiere concatenar eventos de stream y parsear JSON a mano.
*Manejo de respuestas:* Configurar manualmente cada Content-Type, estado HTTP y serializar con JSON.stringify().

*p4 No has programado ninguna ruta para /no-existe. ¿Qué crees que responde Express si la pides?*
*Ábrela en el navegador con las herramientas de desarrollador abiertas (F12 → pestaña*
*Red/Network) y mira el código de estado.*

rta: lo que sucede al buscar esto es que sale que el sitio no existe o esta bloqueado y al entrar al networw aparece esto:'/no-existe'


**reflexion**

Enrutamiento: Resuelto. Express lo simplifica con métodos claros (app.get(), app.post()) y parámetros dinámicos (:id).
Manejo de respuestas: Resuelto. Con res.json() y res.send() los headers y la conversión a JSON son automáticos.
Lectura del body: Sigue igual. Express sigue requiriendo configurar middlewares (app.use(express.json())), de lo contrario req.body es undefined

*p5 Comenta la línea next(); y pide / en el navegador. ¿Qué ves en el navegador? ¿Qué ves en la*
*terminal? Cuando termines, vuelve a activar next();.*
 rta: lo que sucede es que al quitar el next del codigo la pagina se queda cargando infinitamente y al añadirlo vuelve a la normalidad, tambien cuando se escribe una ruta nueva se muestra en el navegador cannot la peticion y la ruta que se escribio.

 *P6  escríbela en tu bitácora ANTES de ejecutar*
*Pides GET /actividades/1. La actividad con id 1 sí existe. ¿Qué código de estado y qué body vas a*
*recibir?*
*Pista para cuando ejecutes: mira lo que imprime console.log('params:', req.params). ¿El 1*
*aparece con comillas o sin comillas?*
rta: El 1 aparece con comillas (es decir, como un string o texto: '1'). Esto se debe a que Express siempre captura los parámetros de la URL como cadenas de texto. Por esa razón, en el código es estrictamente necesario hacer la conversión con Number(req.params.id) para que la comparación estricta (===) del .find() funcione correctamente con los números de tu arreglo.
*p7 En la versión corregida, borra la palabra return que está antes de res.status(404) y pide*
*/actividades/99. ¿Qué recibe el cliente? ¿Qué aparece en la terminal? Después vuelve a poner el*
*return.*
rta: lo que ve el cliente  "mensaje": "No existe la actividad con id 99" y en la terminal se ve  5:01:05 p. m. GET /actividades/99

*p8Predice el resultado de estas tres peticiones: ?tipo=agua, ?tipo=AGUA y ?tipo=fuego. Para la*
*última: ¿debería responder 404 o 200 con una lista vacía? Defiende tu respuesta.*
rta: lo que sucede es que se van a filtrar ahora tambien por el tipo de agua y el tipo de fuego sale error 404 en el caso de AGUA tampoco se va a encontrar.