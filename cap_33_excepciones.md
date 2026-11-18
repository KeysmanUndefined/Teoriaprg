# Excepciones en Python

- **Excepciones:** eventos que pueden modificar el flujo de ejecución de un programa.
- **Provocar excepciones:** generar excepciones automáticamente por errores o manualmente mediante nuestro propio código.
- **Interceptar excepciones:** capturar las excepciones para gestionarlas y evitar que el programa se detenga inesperadamente.
- **Controlador de excepciones:** bloque de código al que Python salta cuando se produce una excepción.
- **Flujo de ejecución:** las excepciones permiten abandonar bloques de código y saltar directamente al controlador, interrumpiendo las llamadas a funciones que estaban ejecutándose.
- **Finalidad:** detectar errores o situaciones inesperadas y ejecutar el código encargado de gestionarlos sin tener que comprobar manualmente cada operación.

## Instrucciones para gestionar excepciones

- **try/except:** permite capturar y recuperarse de las excepciones generadas por Python o por nuestro propio código.
- **try/finally:** permite ejecutar acciones de limpieza, independientemente de que se produzcan excepciones o no.
- **raise:** permite provocar manualmente una excepción en nuestro código.
- **assert:** permite provocar una excepción de forma condicional cuando una condición no se cumple.
- **with/as:** permite implementar gestores de contexto para gestionar recursos y realizar acciones de limpieza automáticamente.

## Funcionamiento de las excepciones

- **try:** establece un bloque de código que permite gestionar las excepciones que puedan producirse.
- **Excepción:** cuando se produce un error o una situación inesperada, Python interrumpe el flujo normal de ejecución.
- **Salto al controlador:** Python salta directamente al controlador de excepciones correspondiente.
- **Abandono de funciones:** se abandonan las llamadas a funciones que estaban activas desde que se entró en el bloque `try`.
- **Gestión del error:** el controlador ejecuta las instrucciones necesarias para responder a la excepción.
- **Ventaja:** simplifica el código al evitar tener que comprobar manualmente si cada operación se ha ejecutado correctamente.

## Funciones de las excepciones

- **Propósitos:** las excepciones se utilizan para gestionar errores, notificar eventos, gestionar casos especiales, realizar acciones de finalización y controlar flujos de ejecución inusuales.

- **Gestión de errores:** Python genera excepciones cuando detecta errores durante la ejecución del programa.
- **Capturar excepciones:** permite detectar los errores y responder a ellos mediante nuestro propio código.
- **Ignorar excepciones:** si no se gestionan, Python detiene el programa y muestra un mensaje de error.
- **try/except:** permite capturar y gestionar excepciones para que el programa pueda continuar ejecutándose.

- **Notificación de eventos:** permite señalar situaciones o resultados sin necesidad de pasar indicadores de resultado por todo el programa.
- **Ejemplo:** una función de búsqueda puede generar una excepción cuando no encuentra un resultado.

- **Gestión de casos especiales:** permite gestionar situaciones poco habituales mediante controladores de excepciones situados en niveles superiores del programa.
- **assert:** permite comprobar durante el desarrollo que las condiciones se cumplen según lo esperado.

- **Acciones de finalización:** la instrucción `try/finally` garantiza que se realicen determinadas operaciones de cierre, independientemente de que se produzcan excepciones o no.
- **with:** ofrece una alternativa para gestionar recursos y realizar operaciones de cierre automáticamente.

- **Flujos de control inusuales:** las excepciones permiten implementar flujos de ejecución complejos que no están disponibles directamente en Python.
- **Backtracking (retroceso):** permite implementar mecanismos de retroceso utilizando excepciones y lógica adicional para deshacer asignaciones.
- **raise:** permite provocar una excepción manualmente y utilizarla para salir de varios bucles a la vez.
- **goto:** Python no dispone de esta instrucción, pero las excepciones pueden desempeñar funciones similares.

## Controlador de excepciones predeterminado

- **IndexError:** excepción integrada de Python que se genera cuando se intenta acceder a un índice fuera de los límites de una secuencia.
- **Excepción generada:** indica qué tipo de error se ha producido.
- **Stack trace (traza de pila):** lista las líneas de código y funciones que estaban activas cuando se produjo la excepción.
- **Controlador predeterminado:** si nuestro código no captura explícitamente una excepción, Python la propaga hasta el nivel superior del programa y activa el controlador predeterminado, que muestra el mensaje de error estándar.
- **Consola básica:** el nombre del archivo aparece como `<stdin>`, que representa el flujo de entrada estándar.
- **Consola IDLE:** el nombre del archivo aparece como `<pyshell>` y también se muestran las líneas del código fuente.
- **Finalización del programa:** el controlador predeterminado termina inmediatamente el programa después de mostrar el mensaje de error.

## Backtracking (retroceso)

- **Backtracking:** técnica que permite deshacer los cálculos anteriores antes de continuar la ejecución.
- **Excepciones en Python:** no implementan un retroceso completo.
- **Variables:** los valores modificados entre la entrada en un bloque `try` y la aparición de una excepción no recuperan automáticamente sus valores anteriores.

## Capturar excepciones (try/except)

- **try/except:** permite capturar excepciones y recuperarse de ellas para que el programa pueda continuar ejecutándose.
- **Recuperación:** después de capturar una excepción, el programa continúa ejecutándose después de toda la instrucción `try`, no desde la instrucción que provocó el error.
- **Reanudación:** Python no permite volver directamente al código que provocó la excepción. Para repetirlo, hay que volver a ejecutar el código necesario.
- **Funciones abandonadas:** Python libera las funciones que se abandonaron como consecuencia de la excepción. Estas funciones no pueden reanudarse.
- **Funcionamiento de try:** captura las excepciones y establece el punto a partir del cual continúa la ejecución del programa después de gestionarlas.
- **Indentación:** las instrucciones `except` deben estar alineadas con `try`, respetando la estructura de bloques de Python.
- **Consola interactiva:** el indicador `...` señala que Python espera que se introduzcan más líneas de código para completar la instrucción.
- **Ejecución:** los ejemplos escritos en la consola interactiva deben introducirse línea por línea, respetando la indentación.

## Provocar excepciones (raise)

- **Origen de las excepciones:** pueden ser generadas automáticamente por Python o manualmente por nuestro propio programa.
- **Capturar excepciones:** las excepciones generadas pueden capturarse para gestionarlas o dejarse sin capturar.
- **raise:** permite provocar manualmente una excepción en nuestro código.
- **Excepciones no capturadas:** se propagan hasta el controlador de excepciones predeterminado, que termina el programa y muestra un mensaje de error.

## Excepciones definidas por el usuario

- **User-Defined Exceptions:** excepciones personalizadas que se crean mediante clases y permiten definir errores específicos de un programa.
- **Exception:** clase integrada de Python de la que normalmente heredan las excepciones personalizadas.
- **Clase personalizada:** permite crear un nuevo tipo de excepción específico para nuestro programa.
- **raise:** provoca una instancia de nuestra excepción personalizada.
- **except:** captura la excepción utilizando el nombre de su clase.

## Características de las excepciones personalizadas

- **Herencia:** permite heredar comportamientos de otras clases de excepción.
- **Estado:** permite almacenar información propia dentro de la excepción.
- **Métodos:** permite incorporar funciones dentro de la clase de excepción.
- **Personalización:** permite modificar el mensaje de error que se muestra cuando la excepción no se captura.


## Acciones de finalización (try/finally)

- **finally:** bloque que puede incluirse en una instrucción `try` y que siempre se ejecuta al salir de ella, independientemente de que se produzca una excepción o no.
- **Ejecución:** si el bloque `try` termina sin excepciones, se ejecuta `finally` y el programa continúa después de toda la instrucción `try`.
- **Excepciones:** si se produce una excepción dentro de `try`, el bloque `finally` se ejecuta antes de que Python propague la excepción.
- **try/except:** permite capturar excepciones y recuperarse de ellas.
- **try/finally:** garantiza que se ejecuten determinadas acciones de finalización, independientemente de las excepciones que se produzcan.
- **Aplicaciones:** utilizar `try/except` para capturar errores de bibliotecas externas y `try/finally` para garantizar el cierre de archivos o conexiones con servidores.
- **Combinación:** desde Python 2.5 es posible combinar las cláusulas `except` y `finally` en una misma instrucción `try`.
- **Ejecución de finally:** se ejecuta al salir del bloque `try`, independientemente de que se produzca una excepción o de que esta sea capturada por `except`.

## Gestores de contexto (with/as)

- **with/as:** utiliza la gestión de contexto de un objeto para garantizar que se realicen las acciones de finalización, independientemente de las excepciones que se produzcan.
- **try/finally:** es una estructura de finalización más general y puede utilizarse cuando `with` no está disponible.
- **Inicialización:** `with/as` también permite ejecutar acciones de inicialización.
- **Gestores personalizados:** permite crear gestores de contexto propios mediante las herramientas de programación orientada a objetos de Python.

## Ventajas de las excepciones

- **Comprobación de errores:** Python detecta automáticamente los errores y genera excepciones.
- **Controladores de excepciones:** permiten gestionar errores sin necesidad de comprobar cada operación individualmente.
- **Simplificación del código:** permiten evitar comprobaciones adicionales y centrarse en las operaciones principales del programa.
- **Ventaja:** permiten ignorar en gran medida las situaciones poco habituales y reducir el código dedicado a comprobar errores.