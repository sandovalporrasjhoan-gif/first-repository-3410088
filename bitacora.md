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