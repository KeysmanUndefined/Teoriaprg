# Tipado dinámico en Python

En Python, los tipos se determinan automáticamente durante la ejecución, no mediante declaraciones en el código.

Todo se reduce a tres elementos:

- Variables.
- Objetos.
- Referencias que los conectan.

## Creación de variables

Una variable (es decir, un nombre), como `a`, se crea cuando el código le asigna un valor por primera vez.

Las asignaciones posteriores modifican la referencia asociada al nombre que ya existe.

## Tipos de variables

Una variable no tiene información de tipo ni restricciones de tipo asociadas a ella durante la ejecución.

**El tipo pertenece al objeto, no al nombre de la variable.**

## Uso de variables

Cuando una variable aparece en una expresión, Python utiliza inmediatamente el objeto al que hace referencia en ese momento, sea cual sea.

Todas las variables deben recibir una asignación antes de poder utilizarse.

- Las variables se crean cuando se les asigna un valor.
- Pueden hacer referencia a cualquier tipo de objeto.
- Deben recibir una asignación antes de ser utilizadas.

Los contadores, por ejemplo, deben inicializarse antes de poder incrementar su valor.

## Funcionamiento de una asignación

Ante una asignación como `a = 3`, conceptualmente, Python realiza tres pasos diferentes:

1. Crear un objeto que represente el valor `3`.
2. Crear la variable `a`, si todavía no existe.
3. Vincular la variable `a` con el objeto `3`.

Las variables y los objetos se almacenan en diferentes partes de la memoria y están asociados mediante enlaces.

Las variables siempre están vinculadas a objetos y nunca a otras variables.

Los objetos más complejos pueden estar vinculados a otros objetos, como sucede con las listas.

## Referencias

Los enlaces entre variables y objetos se denominan **referencias** en Python.

Python sigue automáticamente los enlaces entre las variables y sus objetos.

| Concepto | Definición |
| --- | --- |
| Variables | Entradas en una tabla del sistema, con espacio para almacenar referencias a objetos. |
| Objetos | Bloques de memoria reservada, con espacio suficiente para representar sus valores. |
| Referencias | Enlaces que Python sigue automáticamente desde las variables hasta los objetos. |

## Creación y reutilización de objetos

Conceptualmente, cada vez que se genera un nuevo valor mediante la ejecución de una expresión, Python crea un objeto para representar ese valor.

Como mecanismo de optimización, Python almacena en caché y reutiliza internamente determinados tipos de objetos inmutables, como los números enteros pequeños y algunas cadenas de texto.

## Estructura interna de los objetos

En CPython, cada objeto tiene dos campos estándar en su cabecera:

- **Identificador de tipo:** utilizado para indicar el tipo del objeto.
- **Contador de referencias:** utilizado para determinar cuándo se puede liberar la memoria ocupada por el objeto.

# Los tipos pertenecen a los objetos, no a las variables

Las referencias se siguen automáticamente cuando se utilizan. No se puede manipular directamente una referencia como se haría con un puntero en C.

**Los nombres no tienen tipos. Los tipos pertenecen a los objetos, no a los nombres.**

Lo único que podemos afirmar sobre una variable en Python es que hace referencia a un objeto determinado en un momento concreto.

Los objetos conocen su propio tipo: cada objeto contiene un campo en su cabecera que identifica su tipo.

**Como los objetos conocen sus tipos, las variables no necesitan conocerlos.**

## Estructura interna de los objetos

En CPython, los objetos tienen dos campos fundamentales en su cabecera:

- **Identificador de tipo:** identifica el tipo del objeto.
- **Contador de referencias:** registra cuántas referencias apuntan al objeto.

## Recolección de basura (Garbage Collection)

En Python, cada vez que se asigna un nombre a un nuevo objeto, el objeto anterior puede eliminarse si ningún otro nombre u objeto hace referencia a él.

Esta recuperación automática del espacio ocupado por los objetos se conoce como **recolección de basura (garbage collection)**.

El espacio ocupado por el objeto vuelve al conjunto de memoria disponible para reutilizarse con futuros objetos.

Python gestiona automáticamente la memoria, sin necesidad de que el programador la reserve o libere manualmente.

## Contador de referencias (Reference Counting)

CPython mantiene un contador en cada objeto que registra el número de referencias que apuntan actualmente a dicho objeto.

Cuando este contador llega a cero, normalmente se libera automáticamente la memoria ocupada por el objeto.

La gestión automática de memoria de CPython se basa principalmente en dos mecanismos:

- Contadores de referencias.
- Detección y eliminación de referencias cíclicas.

# Referencias compartidas (Shared References)

```python
a = 3
b = a
```

La segunda instrucción hace que Python cree la variable `b`.

La variable `a` se está utilizando, no se le está realizando una asignación, por lo que Python obtiene el objeto al que hace referencia (`3`) y hace que `b` también haga referencia a ese objeto.

**Las variables `a` y `b` hacen referencia al mismo objeto**, es decir, apuntan al mismo bloque de memoria.

Cuando varios nombres hacen referencia al mismo objeto, se denomina **referencia compartida (shared reference)** o, simplemente, objeto compartido.

Las variables no están vinculadas entre sí, sino al mismo objeto.

## Reasignación de variables

```python
a = 3
b = a
a = 'spam'

print(a)  # spam
print(b)  # 3
```

La reasignación de `a` no modifica el valor de `b`, que continúa haciendo referencia al objeto original, el entero `3`.

## Inmutabilidad de los objetos

No existe ninguna forma de sobrescribir el valor del objeto entero `3`.

**Los números enteros son inmutables y, por tanto, nunca pueden modificarse directamente.**

```python
a = 3
b = a
a = a + 2

print(a)  # 5
print(b)  # 3
```

La operación `a + 2` produce un objeto con el valor `5`, al que pasa a hacer referencia la variable `a`.

## Comportamiento de las asignaciones

En Python, las variables son siempre referencias a objetos.

Asignar un nuevo valor a una variable no altera el objeto original, sino que hace que la variable apunte a otro objeto.

**Una reasignación de una variable solo modifica la referencia de la propia variable que recibe dicha asignación.**

Esto no debe confundirse con modificar directamente un objeto mutable compartido por varias variables.