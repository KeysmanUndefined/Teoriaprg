Puntos clave
- Legibilidad: los buenos nombres de variables son un elemento fundamental para la legibilidad del programa. Algunos tipos de variables, como los índices de bucles y las variables de estado, requieren consideraciones específicas.
- Precisión: los nombres deben ser lo más específicos posible. Los nombres demasiado vagos o generales, que pueden utilizarse para más de un propósito, suelen ser malos nombres.
- Diferenciación: las convenciones de nomenclatura distinguen entre datos locales, globales y de clase, así como entre nombres de tipos, constantes, tipos enumerados y variables.
- Convenciones: independientemente del tipo de proyecto, debes adoptar una convención de nomenclatura. La elección dependerá del tamaño del programa y del número de personas que trabajen en él.
- Abreviaturas: rara vez son necesarias en los lenguajes de programación modernos. Si las utilizas, regístralas en un diccionario de abreviaturas del proyecto o utiliza el sistema de prefijos estandarizados.
Palabras reservadas de Python
- **Palabras reservadas (keywords):** identificadores propios del lenguaje que no pueden utilizarse como nombres de variables ni como identificadores ordinarios.

- **Palabras reservadas de Python:**
  False     class      finally    is         return
  None      continue   for        lambda     try
  True      def        from       nonlocal   while
  and       del        global     not        with
  as        elif       if         or         yield
  assert    else       import     pass
  break     except     in         raise

Elección de nombres de variables
- **Buen nombre:** debe ser legible, fácil de recordar y apropiado.
- **Precisión:** debe describir completa y precisamente la entidad que representa.
- **Descripción:** expresar con palabras lo que representa la variable.
- **Orientación al problema:** debe hacer referencia al problema, no a la solución informática.
- **Significado:** debe expresar el qué, más que el cómo.
- **Legibilidad:** evitar abreviaturas difíciles de interpretar y nombres ambiguos.
- **Longitud:** evitar nombres excesivamente cortos o largos.
- **Longitud óptima:** entre 10 y 16 caracteres de media, según el estudio citado.
- **Longitud aceptable:** entre 8 y 20 caracteres de media, con resultados similares en la depuración.
- **Snake_case:** convención recomendada en Python para nombrar variables y funciones mediante palabras en minúsculas separadas por guiones bajos.
- **Prioridad:** la claridad del nombre prevalece sobre su longitud.

Ámbito de alcance de las variables (scope)
- **Nombre corto:** un nombre como `i` indica que se trata de un valor auxiliar con un ámbito de operación limitado.
- **Variables globales:** es preferible utilizar nombres largos y descriptivos.
- **Variables locales o de bucle:** pueden utilizarse nombres más cortos.

Nombres de variables con valores calculados
- **Valores calculados:** variables que contienen totales, promedios, máximos, mínimos, etc.
- **Modificadores:** `Total`, `Sum`, `Average`, `Max`, `Min`, `Record`, `String` o `Pointer`.
- **Posición del modificador:** se recomienda colocarlo al final del nombre.
- **Significado:** la parte más significativa del nombre debe aparecer al principio.
- **Excepción (Num):** su significado depende de su posición dentro del nombre.
- **Num al principio:** representa una cantidad total. Ejemplo: `numCustomers` (número total de clientes).
- **Num al final:** representa un índice o número identificativo. Ejemplo: `customerNum` (número del cliente actual).
- **Count o Total:** preferibles para representar cantidades totales.
- **Index:** utilizado para referirse a la posición de un elemento concreto.

Términos opuestos en nombres de variables
- **Coherencia:** utilizar términos opuestos favorece la consistencia y mejora la legibilidad.
- **Opuestos habituales:** son más fáciles de comprender y recordar.
- **Ejemplos:** `begin/end` (inicio/fin), `min/max` (mínimo/máximo), `open/close` (abrir/cerrar).

Nombres de los índices de bucles
- **Nombres habituales:** `i`, `j` y `k`.
- **Ámbito limitado:** los nombres cortos son aceptables cuando la variable se utiliza únicamente dentro del bucle.
- **Uso fuera del bucle:** utilizar nombres más descriptivos.
- **Nombres descriptivos:** muchos programadores experimentados evitan nombres como `i` para facilitar la lectura, modificación y reutilización del código.

Nombres de los índices de bucles
- **Uso de i, j y k:** utilizar estos nombres únicamente como índices de bucles sencillos.

Variables de estado
- **Variables de estado:** describen el estado de un programa.
- **Asignación y comprobación:** sus valores deben asignarse y comprobarse mediante tipos enumerados, constantes con nombre o variables globales que actúen como constantes.

Variables temporales
- **Resultados intermedios:** almacenan resultados parciales de cálculos.
- **Valores provisionales:** almacenan datos de manera temporal.
- **Valores auxiliares:** almacenan datos necesarios para el funcionamiento interno del programa.

Variables booleanas
- **Done (completado):** indica si un bucle u operación ha finalizado. Se establece en `False` antes de completar la operación y en `True` cuando finaliza.
- **Error (error):** indica si se ha producido un error.
- **Found (encontrado):** indica si se ha encontrado un valor.
- **Success u OK (éxito):** indica si una operación se ha realizado correctamente.
- **Precisión:** sustituir `success` por un nombre más específico que describa qué significa que la operación haya tenido éxito.
- **Significado:** los nombres deben implicar claramente un valor verdadero o falso.
- **Nombres inadecuados:** `status` y `sourceFile`, porque no implican claramente un valor booleano.

Prefijo Is en variables booleanas
- **Prefijo Is:** convierte el nombre de la variable en una pregunta cuya respuesta es `True` o `False`.
- **isDone:** ¿Está terminado?
- **isError:** ¿Existe un error?
- **isFound:** ¿Se ha encontrado?
- **isProcessingComplete:** ¿Ha finalizado el procesamiento?

Nombres booleanos positivos
- **Nombres positivos:** facilitan la lectura y comprensión de las condiciones.
- **Nombres negativos:** evitar nombres como `notFound`, `notDone` y `notSuccessful`, porque son difíciles de interpretar cuando se niegan.
- **Doble negación:** evitar expresiones como `if not not_found:`.
- **Expresión positiva:** utilizar expresiones como `if found:`.

Nombres de tipos enumerados
- **Tipos enumerados:** utilizar un prefijo común para indicar que sus miembros pertenecen al mismo grupo.
- **Ejemplos de prefijos:** `Color_`, `Planet_` o `Month_`.

Nombres de constantes
- **Constantes:** su nombre debe representar la entidad abstracta, no su valor numérico.
- **Nombre incorrecto:** `FIVE`, porque hace referencia a un valor concreto.
- **Nombre correcto:** `CYCLES_NEEDED`, porque describe lo que representa, independientemente de que su valor sea 5.0 o 6.0.

El poder de las convenciones de nomenclatura
- **Toma de decisiones:** reducen las decisiones necesarias al nombrar variables.
- **Transferencia de conocimientos:** facilitan la comprensión del código entre diferentes proyectos.
- **Proliferación de nombres:** evitan utilizar nombres diferentes para representar el mismo concepto.
- **Limitaciones del lenguaje:** permiten simular constantes con nombre y tipos enumerados.
- **Identificación de datos:** permiten diferenciar entre datos locales, globales y de clase, así como indicar su tipo.
- **Relaciones:** permiten identificar elementos relacionados mediante nombres o prefijos comunes.
- **Estructura:** aportan coherencia y facilitan la comprensión del código.

Cuándo utilizar convenciones de nomenclatura
- **Trabajo en equipo:** cuando varios programadores trabajan en un mismo proyecto.
- **Mantenimiento:** cuando otro programador deberá modificar o mantener el programa.
- **Revisión:** cuando otros programadores revisan el código.
- **Complejidad:** cuando el programa es demasiado grande para recordar todo su contenido.
- **Duración:** cuando el programa tiene una vida útil prolongada y puede retomarse después de semanas o meses.
- **Terminología:** cuando es necesario establecer términos o abreviaturas comunes dentro de un proyecto.

Convenciones de nomenclatura informales
- **Diferenciar variables y rutinas:** la convención del libro utiliza minúscula inicial para variables y objetos, y mayúscula inicial para rutinas.
- **Variable:** `variableName`.
- **Rutina:** `RoutineName()`.

Diferenciar tipos y variables
- **Mayúscula inicial:** `Widget widget`.
- **Mayúsculas completas:** `WIDGET widget`.
- **Prefijo t_ para tipos:** `t_Widget Widget`.
- **Prefijo a para variables:** `Widget aWidget`.
- **Nombres específicos:** `Widget employeeWidget`.

Identificación de variables y tipos
- **Variables globales:** identificarlas para evitar su uso incorrecto.
- **Variables miembro:** identificar los datos que pertenecen a una clase y diferenciarlos de las variables locales y globales.
- **Definiciones de tipos:** identificar explícitamente los nombres de tipos y evitar conflictos con los nombres de variables.
- **Prefijo para tipos:** utilizar, por ejemplo, `t_Color` o `t_Menu`.
- **Constantes con nombre:** identificarlas para distinguirlas de las variables cuyos valores pueden cambiar.
- **Tipos enumerados:** identificar sus elementos por las mismas razones que las constantes con nombre.
- **Parámetros de solo entrada:** identificarlos en lenguajes que no garantizan que permanezcan sin modificar.

Formato y legibilidad de los nombres
- **Mayúsculas:** permiten distinguir las palabras que componen un nombre.
- **Separadores:** permiten separar palabras mediante caracteres como el guion bajo (`_`).
- **Coherencia:** evitar mezclar diferentes técnicas de nomenclatura sin un criterio establecido.

Convenciones de nomenclatura en Python (PEP 8)
- **Variables:** snake_case. Ejemplo: `numero_clientes`.
- **Funciones:** snake_case. Ejemplo: `calcular_total()`.
- **Métodos:** snake_case. Ejemplo: `obtener_precio()`.
- **Clases:** PascalCase. Ejemplo: `DatosCliente`.
- **Objetos:** snake_case. Ejemplo: `cliente_actual`.
- **Constantes:** UPPER_CASE. Ejemplo: `PRECIO_MAXIMO`.

Estilos de nomenclatura
- **camelCase:** primera palabra en minúscula y siguientes con mayúscula inicial. Ejemplo: `numeroClientes`.
- **PascalCase:** todas las palabras comienzan con mayúscula. Ejemplo: `NumeroClientes`.
- **snake_case:** palabras en minúsculas separadas por guiones bajos. Ejemplo: `numero_clientes`.
- **UPPER_CASE:** palabras en mayúsculas separadas por guiones bajos. Ejemplo: `NUMERO_CLIENTES`.

Prefijos estandarizados
- **Prefijos estandarizados:** se componen de dos partes, la abreviatura del tipo definido por el usuario (UDT) y el prefijo semántico.
- **UDT (User-Defined Type):** identifica el tipo de dato del objeto o variable que se está nombrando.
- **Ejemplos de UDT:** ventanas, regiones de pantalla y fuentes tipográficas.
- **Prefijos semánticos:** describen cómo se utiliza una variable o un objeto.
- **Diferencia:** los UDT varían de un proyecto a otro, mientras que los prefijos semánticos están relativamente estandarizados entre proyectos.
- **Formato:** se escriben en minúsculas o combinando mayúsculas y minúsculas.
- **Combinación:** pueden combinarse con los UDT y otros prefijos semánticos.

Directrices generales para crear abreviaturas
- **Compatibilidad:** algunas técnicas se contradicen entre sí, por lo que no deben utilizarse todas al mismo tiempo.
- **Abreviaturas estándar:** utilizar abreviaturas de uso habitual que aparezcan en el diccionario.
- **Eliminar vocales:** eliminar todas las vocales excepto las iniciales. Ejemplos: `computer` → `cmptr`, `screen` → `scrn`, `apple` → `appl`, `integer` → `intgr`.
- **Eliminar palabras innecesarias:** eliminar artículos y conectores como `and`, `or` o `the`.
- **Letras iniciales:** utilizar la primera letra o las primeras letras de cada palabra.
- **Truncamiento coherente:** cortar cada palabra después de la primera, segunda o tercera letra.
- **Letras extremas:** conservar la primera y la última letra de cada palabra.
- **Palabras significativas:** utilizar las palabras importantes del nombre, hasta un máximo recomendado de tres.
- **Eliminar sufijos innecesarios:** eliminar terminaciones como `ing` o `ed`.
- **Sonidos reconocibles:** conservar el sonido más característico de cada sílaba.
- **Conservar el significado:** evitar que la abreviatura cambie el significado de la variable.
- **Python:** es preferible conservar un nombre descriptivo antes que abreviarlo innecesariamente.

Abreviaturas fonéticas
- **Abreviaturas fonéticas:** se basan en el sonido de las palabras en lugar de en su escritura.
- **Ejemplos:** `skating` → `sk8ing`, `highlight` → `hilite`, `before` → `b4`, `execute` → `xqt`.

Consideraciones sobre las abreviaturas
- **No eliminar un único carácter:** no abreviar una palabra eliminando solamente una letra.
- **Coherencia:** utilizar siempre la misma abreviatura. Ejemplo: `Num` o `No`, pero no ambas.
- **Nombres pronunciables:** utilizar `xPos` en lugar de `xPstn` y `needsComp` en lugar de `ndsCmptg`.
- **Prueba del teléfono:** si no puedes leer tu código a otra persona por teléfono, utiliza nombres más fáciles de distinguir.
- **Combinaciones confusas:** evitar combinaciones que provoquen errores de lectura o pronunciación. Ejemplo: `ENDB` en lugar de `BEND`.
- **Sinónimos:** utilizar un diccionario de sinónimos para resolver conflictos entre nombres.
- **Documentar nombres cortos:** incluir una tabla de equivalencias como comentario para recordar el significado de las variables.
- **Documentar abreviaturas:** registrar todas las abreviaturas en un documento de abreviaturas estándar del proyecto.

Tipos de nombres que se deben evitar
- **Nombres engañosos:** evitar nombres o abreviaturas cuyo significado habitual sea diferente al que representan.
- **Significados similares:** evitar nombres como `input` e `inputValue`, `recordNum` y `numRecords`, o `fileNumber` y `fileIndex`.
- **Nombres visualmente similares:** evitar nombres como `clientRecs` y `clientReps`, cuya diferencia resulta difícil de apreciar.
- **Sonidos similares:** evitar nombres que suenen de forma parecida, como `wrap` y `rap`.
- **Números en los nombres:** evitar nombres como `file1` y `file2`. Si los números tienen un significado importante, utilizar un array o una lista.
- **Palabras escritas incorrectamente:** evitar modificar la escritura de una palabra para ahorrar caracteres. Ejemplo: `hilite` en lugar de `highlight`.
- **Diferencias de capitalización:** no diferenciar nombres únicamente mediante mayúsculas y minúsculas.
- **Nombres propios del lenguaje:** evitar nombres de tipos, variables y rutinas estándar. En Python: `list`, `str`, `int`, `dict`, `sum`, `max` o `min`.
- **Nombres sin relación:** evitar nombres que no tengan relación con lo que representan las variables.
- **Caracteres difíciles de distinguir:** evitar caracteres visualmente similares, como `l`, `I`, `1` o `O`, `0`.
- **Mezcla de idiomas:** establecer un único idioma para todo el código, especialmente en proyectos multinacionales.

Principio fundamental de nomenclatura
- **Legibilidad:** los programadores dedican más tiempo a leer código que a escribirlo.
- **Prioridad:** los nombres son más importantes para quien lee el código que para quien lo escribe.
- **Mantenimiento:** escribir código pensando en la persona que tendrá que leerlo, aunque esa persona seas tú mismo dentro de seis meses.

## CHECKLIST: Nomenclatura de variables

### Consideraciones generales
- [ ] ¿El nombre describe completa y precisamente lo que representa la variable?
- [ ] ¿El nombre hace referencia al problema real en lugar de a la solución informática?
- [ ] ¿El nombre es suficientemente largo como para comprenderlo sin esfuerzo?
- [ ] ¿Los modificadores de valores calculados aparecen al final del nombre?
- [ ] ¿Se utiliza `Count` o `Index` en lugar de `Num`?

### Nombres de tipos específicos de datos
- [ ] ¿Los índices de bucles tienen nombres significativos en lugar de `i`, `j` o `k` cuando el bucle tiene más de una o dos líneas o está anidado?
- [ ] ¿Se han sustituido los nombres de las variables temporales por otros más descriptivos?
- [ ] ¿Los nombres de las variables booleanas permiten comprender claramente su significado cuando su valor es `True`?
- [ ] ¿Los nombres de los elementos enumerados incluyen un prefijo o sufijo que identifica su categoría? Ejemplo: `Color_Red`, `Color_Green`, `Color_Blue`.
- [ ] ¿Los nombres de las constantes representan entidades abstractas en lugar de los valores numéricos que contienen?

### Convenciones de nomenclatura
- [ ] ¿La convención distingue entre datos locales, globales y de clase?
- [ ] ¿La convención distingue entre nombres de tipos, constantes, tipos enumerados y variables?
- [ ] ¿La convención identifica los parámetros de solo entrada en lenguajes que no garantizan que permanezcan sin modificar?
- [ ] ¿La convención es lo más compatible posible con las convenciones estándar del lenguaje?
- [ ] ¿El formato de los nombres favorece la legibilidad?

### Nombres cortos
- [ ] ¿El código utiliza nombres descriptivos y suficientemente largos, salvo cuando es necesario utilizar nombres cortos?
- [ ] ¿Se evitan las abreviaturas que solamente ahorran un carácter?
- [ ] ¿Todas las palabras se abrevian de manera coherente?
- [ ] ¿Los nombres son pronunciables?
- [ ] ¿Se evitan nombres que puedan pronunciarse incorrectamente?
- [ ] ¿Los nombres cortos están documentados mediante tablas de equivalencias?

### Problemas habituales de nomenclatura: ¿se han evitado...?
- [ ] Nombres engañosos.
- [ ] Nombres con significados similares.
- [ ] Nombres que solo se diferencian en uno o dos caracteres.
- [ ] Nombres con sonidos similares.
- [ ] Nombres que contienen números innecesarios.
- [ ] Nombres escritos incorrectamente de forma intencionada para acortarlos.
- [ ] Palabras que habitualmente se escriben de forma incorrecta en inglés.
- [ ] Nombres que coinciden con funciones de bibliotecas estándar o variables predefinidas.
- [ ] Nombres completamente arbitrarios y sin relación con su significado.
- [ ] Caracteres difíciles de leer o distinguir.