# Markdown: sintaxis básica y formato

Markdown es un lenguaje de marcado ligero que permite
dar formato a documentos mediante una sintaxis sencilla.

GitHub permite utilizar Markdown en archivos README.md,
documentación, comentarios, issues y pull requests.

# Encabezados (Headings)

Se utilizan entre uno y seis símbolos `#` para establecer
la jerarquía de los encabezados.

```markdown
# Encabezado de nivel 1
## Encabezado de nivel 2
### Encabezado de nivel 3
#### Encabezado de nivel 4
##### Encabezado de nivel 5
###### Encabezado de nivel 6
```

GitHub genera automáticamente un índice de contenidos
cuando existen dos o más encabezados.

# Formato de texto

| Formato | Sintaxis |
|---|---|
| Negrita | `**texto**` |
| Cursiva | `*texto*` o `_texto_` |
| Tachado | `~~texto~~` |
| Negrita y cursiva | `***texto***` |
| Cursiva dentro de negrita | `**texto _importante_**` |
| Subíndice | `<sub>texto</sub>` |
| Superíndice | `<sup>texto</sup>` |
| Subrayado | `<ins>texto</ins>` |

# Citas de texto (Blockquotes)

Se utiliza el símbolo `>` para citar texto.

```markdown
> Esto es una cita.
```

# Código

## Código en línea

Se utiliza una comilla invertida a cada lado del código.

```markdown
Utiliza `git status` para consultar el estado.
```

## Bloques de código

Se utilizan tres comillas invertidas al principio y al final.

```
git status
git add .
git commit -m "Mensaje"
```

Podemos indicar el lenguaje para activar el resaltado
de sintaxis.

```python
def sumar(a, b):
    return a + b
```

```bash
git status
```

# Modelos de color

GitHub permite visualizar colores mediante los siguientes
formatos:

| Modelo | Ejemplo |
|---|---|
| HEX | `#0969DA` |
| RGB | `rgb(9, 105, 218)` |
| HSL | `hsl(212, 92%, 45%)` |

La visualización de colores solo está disponible en
issues, pull requests y discussions.

# Enlaces (Links)

Se escribe el texto entre corchetes y la dirección
entre paréntesis.

Sintaxis:

[Texto del enlace](URL)

Ejemplo:

[Documentación de Git](https://git-scm.com/docs)

# Enlaces a secciones (Section links)

Permiten navegar directamente a un encabezado dentro
del documento.

GitHub genera automáticamente un identificador
(anchor) para cada encabezado.

## Reglas para generar identificadores

- Las letras se convierten en minúsculas.
- Los espacios se sustituyen por guiones.
- Se eliminan los signos de puntuación correspondientes.
- Se elimina el formato Markdown.
- Si existen encabezados repetidos, se añade un número.

Ejemplo:

## Instalación de Git

Para enlazar a esta sección:

[Ir a instalación](#instalación-de-git)

## Encabezados repetidos

Si tenemos dos encabezados con el mismo nombre:

## Ejemplo

## Ejemplo

Sus identificadores serán:

- `#ejemplo`
- `#ejemplo-1`

Si modificamos un encabezado, puede ser necesario
actualizar los enlaces que apuntan a él.

# Enlaces relativos (Relative links)

Permiten enlazar archivos utilizando su ubicación
dentro del repositorio, sin necesidad de indicar
una URL completa.

Ejemplos:

[Apuntes de Python](python.md)

[Apuntes de Git](documentacion/git.md)

[Volver al README](../README.md)

- `./`: directorio actual.
- `../`: directorio superior.
- `/`: raíz del repositorio en los enlaces relativos de GitHub.

## Ejemplos de formato

| Sintaxis Markdown | Resultado |
|---|---|
| `**Importante**` | **Importante** |
| `*Variable*` | *Variable* |
| `~~Error~~` | ~~Error~~ |
| `***Atención***` | ***Atención*** |
| `` `git status` `` | `git status` |
| `H<sub>2</sub>O` | H<sub>2</sub>O |
| `x<sup>2</sup>` | x<sup>2</sup> |
| `<ins>Texto</ins>` | <ins>Texto</ins> |
| `**Texto _importante_**` | **Texto _importante_** |

## Atajos de teclado en GitHub

| Atajo Windows/Linux | Atajo macOS | Función |
|---|---|---|
| `Ctrl + B` | `Cmd + B` | Negrita |
| `Ctrl + I` | `Cmd + I` | Cursiva |
| `Ctrl + E` | `Cmd + E` | Código en línea |
| `Ctrl + K` | `Cmd + K` | Insertar enlace |

# Enlaces relativos (Relative links)

Los enlaces relativos permiten acceder a otros archivos
del repositorio sin utilizar una URL completa.

La ruta se establece respecto a la ubicación del archivo
desde el que se crea el enlace.

## Ejemplo de estructura de un repositorio

```text
proyecto/
├── README.md
├── docs/
│   ├── CONTRIBUTING.md
│   └── instalacion.md
└── imagenes/
    └── logo.png
```

Desde README.md podemos acceder a CONTRIBUTING.md:

```markdown
[Guía de contribución](docs/CONTRIBUTING.md)
```

## Operadores de rutas relativas

| Operador | Significado |
|---|---|
| `./` | Directorio actual |
| `../` | Directorio superior |
| `/` | Raíz del repositorio en GitHub |

## Ejemplos

Desde README.md:

```markdown
[Instalación](./docs/instalacion.md)
```

Desde instalacion.md para regresar a README.md:

```markdown
[Volver al inicio](../README.md)
```

Desde cualquier archivo Markdown del repositorio en GitHub:

```markdown
[Volver al inicio](/README.md)
```

También podemos utilizar rutas relativas para imágenes:

```markdown
![Logo del proyecto](imagenes/logo.png)
```

## Ventajas

- Facilitan la navegación entre archivos.
- No dependen de una URL absoluta.
- GitHub adapta los enlaces a la rama actual.
- Facilitan la portabilidad del repositorio.
- Son recomendables para repositorios que serán clonados.

## Restricciones

El texto del enlace debe estar en una sola línea.

Correcto:

```markdown
[Guía de contribución](docs/CONTRIBUTING.md)
```

Incorrecto:

```markdown
[Guía de
contribución](docs/CONTRIBUTING.md)
```

# Anclas personalizadas (Custom anchors)

Las anclas permiten crear puntos de navegación dentro
de un documento sin necesidad de utilizar encabezados.

Para crear un ancla personalizada se utiliza HTML.

## Sintaxis

```html
<a name="nombre-del-ancla"></a>
```

## Ejemplo

```markdown
<a name="configuracion"></a>

Aquí comienza la explicación de la configuración.

[Ir a configuración](#configuracion)
```

## Características

- Permiten enlazar directamente a cualquier punto del documento.
- Deben tener nombres únicos para evitar ambigüedades.
- No aparecen en el índice automático de GitHub.
- No afectan a la numeración automática de los identificadores
  de los encabezados.

# Saltos de línea (Line breaks)

El comportamiento de los saltos de línea depende
del lugar donde se utilice Markdown.

En issues, pull requests y discussions de GitHub,
los saltos de línea simples se representan automáticamente.

En los archivos `.md`, un salto de línea simple no
implica necesariamente un salto de línea visual.

## Métodos para introducir saltos de línea

### Método 1: dos espacios al final de la línea

Añadir dos espacios después del último carácter
y pulsar Enter.

### Método 2: barra invertida

```markdown
Primera línea\
Segunda línea
```

### Método 3: etiqueta HTML

```markdown
Primera línea<br/>
Segunda línea
```

### Método 4: separar párrafos

Dejar una línea vacía entre dos líneas de texto.

```markdown
Primer párrafo.

Segundo párrafo.
```

Este método crea dos párrafos independientes,
no simplemente un salto de línea.

## Resumen

| Sintaxis | Resultado |
|---|---|
| Enter | Salto en el código fuente, no necesariamente visual |
| Dos espacios + Enter | Salto de línea |
| Barra invertida + Enter | Salto de línea |
| `<br/>` | Salto de línea mediante HTML |
| Línea vacía | Nuevo párrafo |

# Conceptos clave

- Los enlaces relativos permiten navegar entre archivos.
- Las anclas permiten navegar dentro de un documento.
- GitHub genera anclas automáticamente para los encabezados.
- También podemos crear anclas personalizadas mediante HTML.
- Un salto de línea y un nuevo párrafo no son lo mismo.
- Markdown admite determinadas etiquetas HTML.

# Imágenes en Markdown (Images)

Markdown permite mostrar imágenes mediante una sintaxis
similar a la de los enlaces, añadiendo el símbolo `!`.

## Sintaxis

```markdown
![Texto alternativo](ruta_de_la_imagen)
```

- `!`: indica que se trata de una imagen.
- `[]`: contiene el texto alternativo (alt text).
- `()`: contiene la ruta o URL de la imagen.

## Texto alternativo (Alt text)

Es una descripción breve de la imagen.

- Facilita la accesibilidad.
- Permite interpretar la imagen mediante lectores de pantalla.
- Proporciona información cuando la imagen no puede cargarse.

## Imágenes externas

Podemos mostrar una imagen alojada en Internet.

```markdown
![Octocat](https://myoctocat.com/assets/images/base-octocat.svg)
```

## Imágenes del repositorio

Se recomienda utilizar rutas relativas cuando las imágenes
se encuentran dentro del propio repositorio.

Ejemplo de estructura:

```text
proyecto/
├── README.md
├── docs/
│   └── instalacion.md
└── imagenes/
    └── logo.png
```

Desde README.md:

```markdown
![Logo del proyecto](imagenes/logo.png)
```

Desde docs/instalacion.md:

```markdown
![Logo del proyecto](../imagenes/logo.png)
```

Desde cualquier archivo Markdown del repositorio en GitHub:

```markdown
![Logo del proyecto](/imagenes/logo.png)
```

## Rutas de imágenes en GitHub

| Contexto | Ruta |
|---|---|
| Misma rama | `/assets/images/logo.png` |
| Otra rama | `/../main/assets/images/logo.png` |
| Issues, PR y comentarios | `../blob/main/assets/images/logo.png?raw=true` |
| Archivo de otro repositorio | `/../../../../usuario/repositorio/blob/main/assets/images/logo.png` |
| Comentarios de otro repositorio | `../../../usuario/repositorio/blob/main/assets/images/logo.png?raw=true` |

Si la imagen pertenece a un repositorio privado,
el usuario debe disponer de permisos de lectura.

## Diferencia entre enlaces e imágenes

| Elemento | Sintaxis | Función |
|---|---|---|
| Enlace | `[Texto](ruta)` | Navegar a un recurso |
| Imagen | `![Texto](ruta)` | Mostrar una imagen |

## Imágenes mediante HTML

GitHub admite determinadas etiquetas HTML dentro de Markdown.

La etiqueta `img` permite especificar propiedades
adicionales, como la anchura de una imagen.

```html
<img src="imagenes/logo.png" alt="Logo" width="300">
```

## Elemento picture

GitHub admite el elemento HTML `picture`.

Permite mostrar diferentes imágenes dependiendo
de determinadas condiciones, como el tema claro u oscuro.

```html
<picture>
    <source media="(prefers-color-scheme: dark)"
            srcset="imagenes/logo-oscuro.png">
    <source media="(prefers-color-scheme: light)"
            srcset="imagenes/logo-claro.png">
    <img alt="Logo del proyecto" src="imagenes/logo.png">
</picture>
```

## Dónde podemos utilizar imágenes en GitHub

- Archivos Markdown (.md).
- README.md.
- Issues.
- Pull requests.
- Discussions.
- Comentarios.

## Buenas prácticas

- Utilizar textos alternativos descriptivos.
- Utilizar rutas relativas para imágenes del repositorio.
- Organizar las imágenes en un directorio específico.
- Evitar depender innecesariamente de imágenes externas.
- Comprobar los permisos de acceso a las imágenes.

## Conceptos clave

- Markdown permite insertar imágenes mediante `![]()`.
- Los enlaces y las imágenes tienen una sintaxis similar.
- El texto alternativo mejora la accesibilidad.
- Las rutas relativas mejoran la portabilidad.
- HTML permite controlar propiedades adicionales de las imágenes.

# Listas en Markdown (Lists)

Markdown permite crear listas desordenadas, ordenadas,
anidadas y listas de tareas.

## Listas desordenadas (Unordered lists)

Se utiliza un guion (`-`), un asterisco (`*`) o
un símbolo de suma (`+`) delante de cada elemento.

```markdown
- Python
- Java
- JavaScript
```

También es válido:

```markdown
* Python
* Java
* JavaScript
```

```markdown
+ Python
+ Java
+ JavaScript
```

Los tres símbolos producen el mismo resultado.

## Listas ordenadas (Ordered lists)

Se utiliza un número seguido de un punto y un espacio.

```markdown
1. Crear el repositorio.
2. Añadir los archivos.
3. Realizar un commit.
4. Publicar los cambios.
```

Markdown genera automáticamente la numeración de la lista.

## Listas anidadas (Nested lists)

Permiten introducir listas dentro de otras listas
mediante la indentación.

```markdown
- Programación
  - Python
    - Variables
    - Funciones
    - Diccionarios
  - Java
- Entornos de desarrollo
  - Git
  - GitHub
```

También podemos combinar listas ordenadas y desordenadas.

```markdown
1. Crear un proyecto.
   - Crear un directorio.
   - Inicializar Git.
     - Configurar el usuario.
     - Configurar el correo electrónico.
2. Desarrollar el programa.
3. Realizar las pruebas.
```

### Reglas de indentación

El símbolo de la lista anidada debe quedar alineado
con el primer carácter del contenido del elemento superior.

```markdown
1. Primer elemento
   - Primer elemento anidado
     - Segundo elemento anidado
```

La cantidad de espacios depende de la longitud
del marcador del elemento superior.

```markdown
100. Primer elemento
     - Primer elemento anidado
       - Segundo elemento anidado
```

En este último ejemplo se necesitan cinco espacios
para el primer nivel de anidación y siete para el segundo.

# Listas de tareas (Task lists)

Permiten representar tareas pendientes y completadas
mediante casillas de verificación.

## Sintaxis

| Sintaxis | Estado |
|---|---|
| `- [ ] Tarea` | Pendiente |
| `- [x] Tarea` | Completada |

## Ejemplo

```markdown
- [x] Crear el repositorio.
- [x] Desarrollar las funciones.
- [ ] Realizar las pruebas.
- [ ] Corregir errores.
- [ ] Publicar la versión definitiva.
```

## Resultado

- [x] Crear el repositorio.
- [x] Desarrollar las funciones.
- [ ] Realizar las pruebas.
- [ ] Corregir errores.
- [ ] Publicar la versión definitiva.

## Listas de tareas anidadas

```markdown
- [x] Configurar el entorno.
  - [x] Instalar Python.
  - [x] Crear entorno virtual.
- [ ] Desarrollar el programa.
  - [x] Crear las funciones.
  - [ ] Implementar los tests.
  - [ ] Corregir errores.
```

Si la descripción de una tarea comienza con un paréntesis,
GitHub recomienda escapar el carácter mediante una
barra invertida.

```markdown
- [ ] \(Opcional) Mejorar la documentación.
```

## Utilidades de las listas de tareas

- Gestionar tareas pendientes.
- Controlar el progreso de un proyecto.
- Organizar funcionalidades.
- Preparar listas de comprobación (checklists).
- Planificar versiones.
- Controlar errores pendientes de solucionar.

# Mencionar personas y equipos en GitHub

GitHub permite mencionar usuarios y equipos mediante
el símbolo `@`.

## Mencionar un usuario

```markdown
@nombre-usuario
```

Ejemplo:

```markdown
@desarrollador ¿Puedes revisar esta función?
```

## Mencionar un equipo

```markdown
@organizacion/nombre-equipo
```

Ejemplo:

```markdown
@empresa/desarrollo Revisad los cambios realizados.
```

## Características

- Las menciones pueden generar notificaciones.
- Permiten llamar la atención de usuarios y equipos.
- GitHub ofrece autocompletado al escribir `@`.
- Se pueden seleccionar usuarios mediante las flechas
  del teclado y confirmar con Tab o Enter.
- Las sugerencias están limitadas a colaboradores
  del repositorio y participantes de la conversación.
- Mencionar un equipo padre también puede notificar
  a los miembros de sus equipos hijos.

## Requisitos para recibir notificaciones

- Tener permisos de lectura sobre el repositorio.
- Si el repositorio pertenece a una organización,
  pertenecer a dicha organización.

# Resumen de sintaxis

| Elemento | Sintaxis |
|---|---|
| Lista desordenada | `- Elemento` |
| Lista ordenada | `1. Elemento` |
| Lista anidada | Indentación mediante espacios |
| Tarea pendiente | `- [ ] Elemento` |
| Tarea completada | `- [x] Elemento` |
| Mencionar usuario | `@usuario` |
| Mencionar equipo | `@organizacion/equipo` |

# Conceptos clave

- Las listas permiten organizar información.
- La indentación determina la jerarquía de las listas.
- Las listas de tareas permiten controlar el progreso.
- Las menciones facilitan la comunicación entre colaboradores.
- Las menciones y las listas de tareas son funcionalidades
  compatibles con GitHub Flavored Markdown (GFM).

 # Referencias y funcionalidades avanzadas de Markdown en GitHub

## Referenciar issues y pull requests

GitHub permite referenciar incidencias (issues) y solicitudes
de integración (pull requests) mediante el símbolo `#`
seguido de su número.

```markdown
Este cambio soluciona el problema descrito en #25.
```

GitHub convierte automáticamente la referencia en un enlace.

Al escribir `#` en el editor de GitHub, aparece una lista
de issues y pull requests disponibles.

Podemos buscar por número o título y seleccionar el
resultado mediante Tab o Enter.

### Referencias a otros repositorios

```markdown
usuario/repositorio#25
```

### Cerrar automáticamente una incidencia

Podemos utilizar determinadas palabras clave para cerrar
una incidencia cuando se integra el pull request en la
rama predeterminada del repositorio.

```markdown
Closes #25
Fixes #25
Resolves #25
```

## Referencias a recursos externos

GitHub permite configurar enlaces automáticos personalizados
(autolinks) hacia herramientas externas.

Por ejemplo:

- Jira: gestión de proyectos e incidencias.
- Zendesk: gestión de solicitudes de soporte.

```markdown
JIRA-123
```

Si el repositorio tiene configurado el autolink correspondiente,
GitHub convierte automáticamente la referencia en un enlace.

Esta configuración requiere permisos de administración
sobre el repositorio.

# Subir archivos (Uploading assets)

GitHub permite adjuntar archivos e imágenes mediante:

- Arrastrar y soltar (drag and drop).
- Seleccionar archivos desde el explorador.
- Pegar contenido desde el portapapeles.

Se pueden adjuntar archivos en:

- Issues.
- Pull requests.
- Comentarios.
- Archivos Markdown.

GitHub genera la referencia necesaria para acceder
al archivo adjunto.

# Emojis

GitHub permite insertar emojis mediante códigos
delimitados por dos puntos.

## Sintaxis

```markdown
:codigo_del_emoji:
```

## Ejemplos

| Código | Resultado | Significado |
|---|---|---|
| `:smile:` | 😄 | Sonrisa |
| `:+1:` | 👍 | Aprobación |
| `:rocket:` | 🚀 | Lanzamiento |
| `:bug:` | 🐛 | Error |
| `:warning:` | ⚠️ | Advertencia |
| `:white_check_mark:` | ✅ | Completado |
| `:x:` | ❌ | Error o rechazo |
| `:tada:` | 🎉 | Celebración |
| `:memo:` | 📝 | Documentación |
| `:construction:` | 🚧 | En desarrollo |
| `:lock:` | 🔒 | Seguridad |
| `:bulb:` | 💡 | Idea |

Al escribir `:` en el editor de GitHub, aparece una lista
de sugerencias de emojis.

También podemos insertar directamente caracteres Unicode.

Lista completa:

[Emoji Cheat Sheet](https://github.com/ikatyang/emoji-cheat-sheet)

# Párrafos (Paragraphs)

Para crear un nuevo párrafo se deja una línea vacía
entre dos bloques de texto.

```markdown
Este es el primer párrafo.

Este es el segundo párrafo.
```

# Notas al pie (Footnotes)

Las notas al pie permiten añadir referencias,
aclaraciones o información complementaria sin
interrumpir el contenido principal.

## Sintaxis

```markdown
Git es un sistema de control de versiones[^1].

[^1]: Creado por Linus Torvalds en 2005.
```

## Notas con varias líneas

```markdown
GitFlow es un modelo de ramificación[^2].

[^2]: Modelo propuesto por Vincent Driessen.  
    Permite organizar el desarrollo mediante ramas.
```

## Características

- Las referencias aparecen numeradas.
- Las notas se muestran al final del documento.
- Su posición en el código fuente no determina
  su posición visual.
- GitHub no admite notas al pie en sus wikis.

# Alertas (Alerts)

Las alertas, también denominadas callouts o admonitions,
son una extensión de Markdown que permite destacar
información relevante.

Utilizan una sintaxis basada en las citas de texto (`>`).

GitHub dispone de cinco tipos de alertas.

## NOTE: información adicional

```markdown
> [!NOTE]
> GitFlow es una metodología de trabajo, no un sistema
> de control de versiones independiente.
```

## TIP: consejo

```markdown
> [!TIP]
> Utiliza git status antes de realizar un commit.
```

## IMPORTANT: información importante

```markdown
> [!IMPORTANT]
> Comprueba que estás trabajando en la rama correcta.
```

## WARNING: advertencia

```markdown
> [!WARNING]
> Comprueba los cambios antes de ejecutar git reset --hard.
```

## CAUTION: precaución

```markdown
> [!CAUTION]
> El comando git clean -fd elimina archivos y directorios
> no rastreados que no estén ignorados.
```

## Resumen de alertas

| Tipo | Finalidad |
|---|---|
| `NOTE` | Información útil o complementaria |
| `TIP` | Consejo o recomendación |
| `IMPORTANT` | Información imprescindible |
| `WARNING` | Advertencia que requiere atención |
| `CAUTION` | Riesgo o posibles consecuencias negativas |

## Buenas prácticas

- Utilizar alertas únicamente cuando sean necesarias.
- Evitar utilizar demasiadas alertas.
- Evitar colocar varias alertas consecutivas.
- No anidar alertas dentro de otros elementos.

# Comentarios ocultos (HTML comments)

Markdown permite ocultar contenido en el documento
renderizado mediante comentarios HTML.

## Sintaxis

```html
<!-- Este contenido no se mostrará -->
```

## Ejemplo

```markdown
# Documentación del proyecto

<!-- TODO: Añadir instrucciones de instalación -->

Descripción del proyecto.
```

## Utilidades

- Dejar anotaciones para otros desarrolladores.
- Recordar tareas pendientes.
- Añadir instrucciones internas.
- Ocultar temporalmente contenido de la vista renderizada.

El contenido sigue existiendo en el código fuente,
por lo que no debe utilizarse para ocultar contraseñas,
credenciales o información confidencial.

# Escapar caracteres (Escaping)

La barra invertida (`\`) permite evitar que determinados
caracteres sean interpretados como formato Markdown.

## Ejemplos

| Sintaxis | Resultado |
|---|---|
| `\*texto\*` | \*texto\* |
| `\# Título` | \# Título |
| `\> Texto` | \> Texto |
| `\- Elemento` | \- Elemento |
| `\**texto\**` | \**texto\** |

## Ejemplo práctico

```markdown
\# Esto no es un encabezado.

\*Esto no está en cursiva.\*
```

También podemos utilizar bloques de código o código
en línea para mostrar sintaxis Markdown sin interpretarla.

# Desactivar el renderizado de Markdown

GitHub permite visualizar un archivo Markdown de dos formas:

- Preview: muestra el documento con el formato aplicado.
- Code: muestra el código fuente del documento.

La vista de código permite:

- Consultar la sintaxis original.
- Visualizar los números de línea.
- Crear enlaces a líneas concretas.
- Comprobar cómo se ha escrito el documento.

# Resumen general

| Elemento | Sintaxis |
|---|---|
| Referenciar issue o PR | `#25` |
| Referenciar otro repositorio | `usuario/repositorio#25` |
| Mencionar usuario | `@usuario` |
| Mencionar equipo | `@organizacion/equipo` |
| Emoji | `:rocket:` |
| Nuevo párrafo | Línea vacía |
| Nota al pie | `[^1]` |
| Definición de nota | `[^1]: Texto` |
| Alerta | `> [!NOTE]` |
| Comentario oculto | `<!-- Texto -->` |
| Escapar carácter | `\` |

# Conceptos clave

- Markdown facilita la creación de documentación.
- GitHub Flavored Markdown (GFM) amplía la sintaxis
  básica de Markdown.
- GitHub incorpora funcionalidades adicionales relacionadas
  con usuarios, repositorios, issues y pull requests.
- No todas las funcionalidades de GitHub están disponibles
  en todos los editores de Markdown.
- Los comentarios HTML ocultan contenido visualmente,
  pero no eliminan la información del archivo original.

# Documentación oficial

[GitHub: sintaxis básica de escritura y formato](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

[Especificación de GitHub Flavored Markdown](https://github.github.com/gfm/)