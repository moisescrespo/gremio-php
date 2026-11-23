# Memoria · Gremio de Aventureros

**Código de alumno/a:** ______  (no pongas tu nombre)

## 1. Mi aventurero
- Usuario que he añadido a la tabla: moises
- Comando o pasos que he usado para generar el hash: 
- Comando o pasos que he usado para generar el hash:

He utilizado la función password_hash() de PHP.

```php
echo password_hash('Moises2026', PASSWORD_DEFAULT);

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
En $_SESSION guardo los datos de la sesión actual del usuario, como:

- $_SESSION['aventurero']
- $_SESSION['zurron']
- $_SESSION['visitas']
- $_SESSION['entrada']

En las cookies guardo:

- COOKIE_TEMA
- COOKIE_USUARIO

## 5. Parte 3 · Seguridad del login
### ¿Qué pasa si en el usuario escribes `' OR '1'='1`? ¿Por qué?

No se puede iniciar sesión y aparece el mensaje "Usuario o contraseña incorrectos".

Esto ocurre porque la consulta utiliza sentencias preparadas con el marcador :usuario, por lo que el contenido introducido se trata como un dato y no como parte de la consulta SQL.

### ¿Para qué sirve `session_regenerate_id(true)`?

Sirve para generar un nuevo identificador de sesión después del login y evitar ataques de fijación de sesión.

### ¿Por qué el mensaje de error es el mismo si falla el usuario o la contraseña?

Porque así no se proporciona información adicional a un posible atacante. Si se mostraran mensajes diferentes, se podría averiguar qué usuarios existen en la base de datos.

## 6. Pruebas que he hecho

| Prueba | Resultado esperado | Resultado obtenido |
|---|---|---|
| Entrar en tablon.php sin login | Acceso como invitado | Correcto |
| Aceptar la misma misión dos veces | No duplicar la misión | Correcto |
| Login con contraseña mala | Usuario o contraseña incorrectos | Correcto |
| Cerrar sesión y volver al zurrón | El zurrón se vacía | Correcto |
| Cambiar el tema y cerrar sesión | El tema se mantiene | Correcto |

## 7. Dificultades y cómo las he resuelto

La principal dificultad fue comprender la estructura inicial del proyecto y adaptar las funciones a los nombres de los campos definidos en el array de misiones.

También fue necesario implementar correctamente los filtros de búsqueda por rango y recompensa mínima, validando los datos recibidos por URL para evitar errores.

Otra dificultad fue gestionar el zurrón de misiones sin duplicar elementos y aplicando el patrón Post/Redirect/Get para impedir que una misión se añadiera varias veces al actualizar la página.

Los problemas encontrados se resolvieron revisando la documentación de PHP y comprobando el funcionamiento de cada función mediante pruebas manuales realizadas en la aplicación.
