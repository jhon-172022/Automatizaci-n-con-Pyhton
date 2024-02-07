Automatización en Python: Sintaxis
==================

*   [Resumen](#resumen)
    *   [Envío de Correo](#envío-de-correo)
    *   [Manejo de Excepciones](#manejo-de-excepciones)
    *   [Funciones](#funciones)
    *   [Path vs OS](#path-vs-os)

* * *

## Resumen ##

Este repositorio contiene proyectos de Envío de Correos, Funciones y Excepciones, Librería Path y OS completados por mí con fines de aprendizaje para realizar automatizaciones.

## Envío de Correo ##

Para enviar e-mails desde Python, éste nos provee smtplib, otro módulo de la librería estándar de Python, quien nos permitirá enviar mensajes de correo electrónico, incluso, en formato HTML.

Solo necesitaremos:

    *   Importamos la libreria smtplib.
    *   Definimos las variables para el envío del mensaje (remitente, destinatario, asunto y mensaje) en formato HTML.
    *   Generamos el e-mail con todos los datos definidos anteriormente.
    *   Envío del mensaje usando el método sendmail del objeto SMTP.

## Manejo de Excepciones ##

Programar el decirle al computador que haga lo que uno necesita que éste haga. Para esto se utilizan librerías y operaciones preexistentes o se escribe código nuevo.

Dependiendo del problema pueden presentarse situaciones excepcionales que incluyen valores de entrada no válidos o situaciones que afectan el flujo ideal del programa interrumpiendo su ejecución.

Es posible detectar esos errores en tiempo de ejecución y tratarlos mediante el manejo de excepciones.

Se tiene el siguiente código que divide dos números enteros:

    *   def division(a, b):
    *   coc = a//b
    *   res = a % b
    *   return (coc, res)

    *   print(division(10, 0))
    *   ZeroDivisionError: integer division or modulo by zero

## Funciones ##

Son unidades pequeñas dentro de una construcción más grande que genera una salida esperada. Si se piensa en un televisor, cada botón en el control remoto cumple una función (subir volumen, bajar volumen, etc..)

Las funciones tienen dos categorías:

    *   Funciones incluídas (len, append, pop, etc..).
    *   Funciones definidas por el usuario.
   
## Path vs OS ##

Regularmente, siempre que hablamos acerca del trabajo con directorios en Python, el módulo OS sale a relucir. 

Y no es de extrañarse, este módulo, entra otras cosas, nos permite manipular directorios del sistema operativo de una forma relativamente sencilla, haciendo uso de Strings.

Solo necesitaremos el codigo de la siguiente manera:

    *   import os
    *   os.path.exists("/users/pywombat/documents/downloads")

Esto funciona, así que ahora modifiquemos un poco nuestro script:

    *   import os
    *   if not os.path.exists("/users/pywombat/downloads"):
    *      os.mkdir("/users/pywombat/downloads")

En este caso, al trabajar con Strings, todas las funciones que ejecutemos de os serán completamente independientes unas de otras, y estas carecerán del contexto para conocer sobre en qué ruta se esta trabajando, por lo tanto, si vamos a realizar múltiples operaciones sobre un mismo directorio, es necesario pasar el mismo argumento para todas las funciones, lo cual puede ser algo tedioso. 

Si bien este problema se puede solventar con alguna variable, creo que no es la solución más optima para atacar dicho problema.

A afortunadamente para nosotros, en versiones recientes del lenguaje, se añade el módulo pathlib a la biblioteca estándar de Python, módulo que, al igual que os , nos permite trabajar con directorios del sistema, solo que en esta ocasión a través de clases y objetos

Por ejemplo, repliquemos el crear el directorio descargas pero ahora con Pathlib:

    *   from pathlib import Path
    *   path = Path("/users/pywombat/documents/downloads")
    *   if not path.exists():
    *      path.mkdir()

Como podemos observar solo es necesario instanciar nuestra ruta y con el mismo objeto ya podemos realizar múltiples operaciones. 

Además de ello, con Pathlib sí podemos acceder a la meta data de los directorios.

Veamos un par de ejemplos:

    *   path = Path('/home/eduardo/projects/main.py')
    *   path.name | path.stem | path.suffix | path.parent | path.parent.name
    *   'main.py' | 'main'    | '.py'       | PosixPath('/home/eduardo/projects') | 'projects'

En conclusión, si bien es cierto que con el módulo os sí podemos trabajar con directorios en Python, la verdad es que al apoyarnos de Strings, la cantidad de cosas que podemos realizar son limitadas, además, si queremos realizar múltiples operaciones sobre un mismo directorio siempre será necesario hacerle saber a las funciones sobre de que directorio estamos hablando.

Por lo tanto, para agilizar nuestro proceso de desarrollo y que nuestro código sea mucho más legible, yo te recomiendo utilizar el módulo pathlib sobre os.
