# Memoria · Gremio de Aventureros

**Código de alumno/a:** ______  (no pongas tu nombre)

## 1. Mi aventurero
- Usuario que he añadido a la tabla: ______
- Comando o pasos que he usado para generar el hash:

## 2. Parte 1 · match
¿Has puesto `default` en `etiquetaRango()`? ¿Qué pasa si llega el rango `'Z'`? ¿Por qué lo prefieres así?

Sí, he añadido default en etiquetaRango().

Si llegase un rango no contemplado como 'Z', la función devolvería "Desconocido" en lugar de provocar un error.

Lo prefiero así porque hace el código más robusto ante posibles datos incorrectos o manipulados y evita comportamientos inesperados.

## 3. Parte 2 · Validación de la URL
Escribe a mano en la barra `tablon.php?rango=Z&oro=hola`. ¿Qué ocurre y qué línea de tu código lo evita?

Al escribir manualmente tablon.php?rango=Z&oro=hola la aplicación muestra todas las misiones sin generar errores.

Esto ocurre porque leerRangoFiltro() devuelve null cuando el rango recibido no existe dentro de RANGOS y leerOroMinimo() devuelve 0 cuando el valor introducido no es un número entero válido entre 0 y 10000.

La validación se realiza utilizando in_array() para comprobar el rango y filter_var() con FILTER_VALIDATE_INT para validar la recompensa mínima.

## 4. Parte 3 · Sesión frente a cookie
Explica con tus palabras qué guardas en `$_SESSION` y qué guardas en cookies, y por qué no al revés.

## 5. Parte 3 · Seguridad del login
- ¿Qué pasa si en el usuario escribes `' OR '1'='1`? ¿Por qué?
- ¿Para qué sirve `session_regenerate_id(true)`?
- ¿Por qué el mensaje de error es el mismo si falla el usuario o la contraseña?

## 6. Pruebas que he hecho

| Prueba | Resultado esperado | Resultado obtenido |
|---|---|---|
| Entrar en tablon.php sin login | Acceso como invitado | Correcto |
| Login con contraseña mala | Pendiente de la Entrega 2 | Pendiente |
| Aceptar la misma misión dos veces | No duplicar la misión | Correcto |
| Cerrar sesión y volver al zurrón | Pendiente de la Entrega 2 | Pendiente |
| Cambiar el tema y cerrar sesión | Pendiente de la Entrega 2 | Pendiente |

## 7. Dificultades y cómo las he resuelto

La principal dificultad fue comprender la estructura inicial del proyecto y adaptar las funciones a los nombres de los campos definidos en el array de misiones.

También fue necesario implementar correctamente los filtros de búsqueda por rango y recompensa mínima, validando los datos recibidos por URL para evitar errores.

Otra dificultad fue gestionar el zurrón de misiones sin duplicar elementos y aplicando el patrón Post/Redirect/Get para impedir que una misión se añadiera varias veces al actualizar la página.

Los problemas encontrados se resolvieron revisando la documentación de PHP y comprobando el funcionamiento de cada función mediante pruebas manuales realizadas en la aplicación.
