# El archivo .gitignore

El archivo `.gitignore` contiene los patrones que identifican los archivos y directorios que queremos que Git ignore.

Se puede utilizar un archivo `.gitignore` en el directorio raíz del repositorio para definir los archivos que deben ignorarse.

Cuando aparecen nuevos archivos que deseas ignorar, puedes modificar manualmente el archivo `.gitignore` y confirmar los cambios mediante un commit.

Los patrones del archivo `.gitignore` se comparan con los nombres y rutas de los archivos del repositorio para determinar si deben ignorarse.

## Patrones y estructura del archivo .gitignore

Cada línea del archivo `.gitignore` contiene un patrón que indica qué archivos o directorios deben ignorarse.

Para hacer coincidir nombres de archivos se utilizan caracteres comodín mediante patrones conocidos como *globbing*.

Puedes escapar dichos caracteres utilizando una barra invertida (`\`).

## Comentarios (#)

Las líneas que comienzan con una almohadilla (`#`) son comentarios y Git las ignora.

Las líneas vacías permiten mejorar la legibilidad y agrupar patrones relacionados.

## Barra inclinada (/)

La barra inclinada representa un separador de directorios.

- Si un patrón comienza con `/`, hace referencia al directorio donde se encuentra el archivo `.gitignore`.
- Si el `.gitignore` está en la raíz del repositorio, un patrón que comienza con `/` se limita a dicha raíz.
- Si el patrón no contiene ninguna barra, salvo una posible barra final, puede coincidir con archivos o directorios de cualquier nivel.
- Si un patrón termina con `/`, únicamente coincide con directorios.

Cuando se ignora un directorio, también se ignoran todos los archivos y subdirectorios que contiene.

## Nombres literales de archivos

Un nombre de archivo literal, sin caracteres especiales, es el patrón más sencillo.

| Patrón | Ejemplos de coincidencias |
| --- | --- |
| `/access.log` | `access.log` en la raíz |
| `access.log` | `access.log` |
| | `logs/access.log` |
| | `var/logs/access.log` |
| `build/` | Cualquier directorio llamado `build` |

## Caracteres comodín (Wildcards)

### Asterisco (*)

El asterisco coincide con cero o más caracteres, excepto el separador de directorios `/`.

| Patrón | Ejemplos de coincidencias |
| --- | --- |
| `*.log` | `error.log` |
| | `logs/debug.log` |
| | `build/logs/error.log` |
| `*.pyc` | `programa.pyc` |
| | `motor/calculos.pyc` |

### Doble asterisco (**)

Dos asteriscos consecutivos permiten representar múltiples niveles de directorios cuando se utilizan en determinadas posiciones del patrón.

| Patrón | Ejemplos de coincidencias |
| --- | --- |
| `logs/**` | Todo el contenido del directorio `logs` |
| `**/build` | `build` |
| | `var/build` |
| | `proyecto/motor/build` |
| `foo/**/bar` | `foo/bar` |
| | `foo/test/bar` |
| | `foo/test/datos/bar` |

### Signo de interrogación (?)

El signo de interrogación coincide exactamente con un carácter, excepto `/`.

| Patrón | Coincide | No coincide |
| --- | --- | --- |
| `access?.log` | `access0.log` | `access01.log` |
| `access?.log` | `accessA.log` | `accessABC.log` |
| `temp??` | `temp01` | `temp0` |
| `temp??` | `tempAB` | `tempABC` |

## Negación de patrones (!)

Un patrón que comienza con un signo de exclamación (`!`) permite volver a incluir un archivo que había sido ignorado por un patrón anterior.

```gitignore
*.log
!error.log
```

En este ejemplo se ignoran todos los archivos con extensión `.log`, excepto los llamados `error.log`.

**No se puede volver a incluir un archivo si su directorio padre continúa completamente excluido.**

## Ignorar archivos que ya están siendo rastreados

El archivo `.gitignore` no afecta a los archivos que Git ya está rastreando.

Si un archivo ya está siendo rastreado y quieres que Git deje de hacerlo sin eliminarlo de tu ordenador, puedes utilizar:

```bash
git rm --cached archivo.txt
```

Después, debes añadirlo al `.gitignore` y confirmar los cambios mediante un commit.

## Ejemplo de .gitignore para un proyecto Python

```gitignore
# Entorno virtual
.venv/

# Caché de Python
__pycache__/
*.pyc

# Caché de pytest
.pytest_cache/

# Caché de Ruff
.ruff_cache/

# Variables de entorno y credenciales
.env

# Archivos de registro
*.log

# Archivos temporales
*.tmp
```

# Configuración avanzada de .gitignore

## .gitignore global

Git permite configurar un archivo de exclusión global que puede utilizarse en todos nuestros repositorios.

Comando en la terminal para configurar un `.gitignore` global:

```bash
git config --global core.excludesFile ~/.gitignore_global
```

Después, debemos crear el archivo `.gitignore_global` en nuestro directorio personal y añadir los patrones correspondientes.

## Ignorar un archivo previamente confirmado mediante un commit

### 1. Añadir el archivo al .gitignore

```gitignore
bug_fix_sample.py
```

### 2. Eliminar el archivo del índice de Git

Utilizamos el parámetro `--cached`:

```bash
git rm --cached bug_fix_sample.py
```

Esto elimina el archivo del índice de Git, pero no del disco duro.

### 3. Dejar de rastrear un directorio completo

Si queremos dejar de rastrear todos los archivos de un directorio, utilizamos:

```bash
git rm -r --cached carpeta/
```

### 4. Simular la operación

Si queremos comprobar previamente qué cambios se realizarán, podemos utilizar el parámetro `--dry-run`:

```bash
git rm -r --cached --dry-run carpeta/
```

### 5. Confirmar los cambios

```bash
git add .gitignore
git commit -m "Dejar de rastrear archivos innecesarios"
```

**Esta operación no elimina el archivo del historial de commits anteriores.**

## Forzar la inclusión de un archivo ignorado

Podemos utilizar el parámetro `-f` para añadir un archivo ignorado al índice de Git:

```bash
git add -f archivo.txt
```

## Archivos ignorados y Git Stash

`git stash` es una herramienta de Git que permite guardar temporalmente los cambios locales y retirarlos del directorio de trabajo para poder recuperarlos posteriormente.

De forma predeterminada, `git stash` únicamente guarda los cambios de los archivos rastreados por Git.

```bash
git stash
```

### Incluir archivos no rastreados

Puedes utilizar la opción `--include-untracked` o su abreviatura `-u` para guardar también los archivos que todavía no están siendo rastreados.

```bash
git stash -u
```

### Incluir archivos ignorados

Puedes utilizar la opción `--all` para guardar también los archivos ignorados y los archivos no rastreados.

```bash
git stash --all
```

| Comando | Rastreados | No rastreados | Ignorados |
| --- | --- | --- | --- |
| `git stash` | Sí | No | No |
| `git stash -u` | Sí | Sí | No |
| `git stash --all` | Sí | Sí | Sí |

### Recuperar los cambios guardados

```bash
git stash pop
```

Este comando aplica los cambios guardados y elimina la entrada del stash si se aplican correctamente.

## Depuración del archivo .gitignore

### Comprobar por qué se ignora un archivo

El comando `git check-ignore`, junto con la opción `-v` (*verbose*), permite mostrar información detallada sobre el patrón que provoca que un archivo sea ignorado.

Por ejemplo, para comprobar por qué se ignora el directorio `temp/`:

```bash
git check-ignore -v temp/
```

La salida indica:

- El archivo que contiene la regla de exclusión.
- El número de línea.
- El patrón que provoca la exclusión.
- La ruta comprobada.

### Mostrar los archivos ignorados

Para mostrar también los archivos ignorados, se utiliza la opción `--ignored` junto con el comando `git status`.

```bash
git status --ignored
```

## Resumen de comandos

| Comando | Propósito |
| --- | --- |
| `git config --global core.excludesFile ~/.gitignore_global` | Configurar un archivo de exclusión global. |
| `git add -f archivo` | Forzar la inclusión de un archivo ignorado. |
| `git rm --cached archivo` | Dejar de rastrear un archivo sin eliminarlo localmente. |
| `git rm -r --cached carpeta/` | Dejar de rastrear un directorio y su contenido. |
| `--dry-run` | Simular una operación sin ejecutarla. |
| `git stash` | Guardar temporalmente los cambios de archivos rastreados. |
| `git stash -u` | Incluir también archivos no rastreados. |
| `git stash --all` | Incluir también archivos ignorados. |
| `git stash pop` | Recuperar los cambios guardados. |
| `git check-ignore -v archivo` | Averiguar por qué se ignora un archivo. |
| `git status --ignored` | Mostrar también los archivos ignorados. |

## Consideraciones importantes

- `.gitignore` no afecta a los archivos que ya están siendo rastreados.
- `--cached` permite eliminar archivos del índice sin eliminarlos del disco duro.
- `--dry-run` permite comprobar una operación antes de ejecutarla.
- Ignorar un archivo no elimina su contenido del historial de Git.
- `git stash --all` puede guardar archivos sensibles o directorios voluminosos, como `.env` o `.venv/`. Debe utilizarse con precaución.

# Git commit: guardar los cambios preparados

El comando `git commit` guarda todos los cambios del proyecto que se encuentran actualmente en el área de preparación (*staging area*).

Los commits se utilizan para documentar el estado de un proyecto en un momento determinado.

El comando `git commit` crea una instantánea (*snapshot*) del estado del proyecto a partir de los cambios preparados.

Cuando añadimos un archivo mediante `git add`, sus cambios pasan al área de preparación. Para guardar esos cambios en el repositorio, utilizamos el comando `git commit`.

El área de preparación nos permite seleccionar los cambios que queremos guardar, mientras que el commit permite registrar dichos cambios en el sistema de control de versiones.

## Identificador de un commit (Commit ID)

Cada commit tiene su propio identificador (*commit ID*), por lo que dos commits diferentes no se sobrescriben entre sí.

Este identificador se genera mediante un algoritmo criptográfico denominado SHA (*Secure Hash Algorithm*).

Tradicionalmente, Git utiliza SHA-1, aunque también admite repositorios basados en SHA-256.

## Repositorios distribuidos

En Git, los repositorios son distribuidos.

Las instantáneas se guardan en el repositorio local y no es necesario interactuar con otros repositorios Git para realizar un commit.

Los commits de Git pueden enviarse a un repositorio remoto mediante `git push`.

## Flujo de trabajo

```text
Directorio de trabajo
        |
     git add
        |
Área de preparación (Staging Area)
        |
    git commit
        |
Repositorio local
        |
     git push
        |
Repositorio remoto
```

# Opciones del comando git commit

## -a, --all

Prepara automáticamente los cambios y las eliminaciones de archivos que ya están siendo rastreados y crea un commit.

```bash
git commit -a
```

No incluye automáticamente archivos nuevos sin rastrear.

## -m, --message

Crea un commit utilizando el mensaje proporcionado.

```bash
git commit -m "Actualizar función de cálculo"
```

Si no se proporciona un mensaje, `git commit` abre el editor de texto configurado localmente y solicita que introduzcas un mensaje.

## --interactive

Permite seleccionar interactivamente los cambios que queremos incluir en el commit.

```bash
git commit --interactive
```

## -n, --no-verify

Permite omitir la ejecución de los hooks `pre-commit` y `commit-msg`.

```bash
git commit --no-verify
```

Los hooks son scripts que permiten ejecutar comprobaciones automáticas.

## -am

Combina los parámetros `-a` y `-m`.

```bash
git commit -am "Corregir errores de cálculo"
```

Prepara automáticamente los cambios de archivos rastreados y crea un commit con el mensaje proporcionado.

No incluye automáticamente archivos nuevos sin rastrear.

## --amend

Permite modificar el último commit.

```bash
git commit --amend
```

Los cambios preparados se incorporan al commit anterior y se abre el editor de texto para modificar el mensaje.

Para incorporar cambios conservando el mensaje anterior:

```bash
git commit --amend --no-edit
```

**Git crea un nuevo commit que sustituye al anterior, por lo que cambia su identificador.**

Debe utilizarse con precaución cuando el commit anterior ya ha sido publicado en un repositorio compartido.

## --dry-run

Simula la creación de un commit sin realizarlo.

```bash
git commit --dry-run
```

Muestra:

- Los archivos que se incluirían en el commit.
- Los archivos con modificaciones locales que quedarían sin confirmar.
- Los archivos no rastreados.

# Mensajes de commit

La primera línea del mensaje de un commit se utiliza normalmente como asunto, de forma similar a un correo electrónico.

El resto del mensaje se denomina cuerpo y se utiliza para proporcionar información adicional sobre los cambios realizados.

Muchos desarrolladores utilizan el modo imperativo para redactar sus mensajes de commit.

Ejemplo:

```text
Añadir cálculo del descanso semanal

Implementar la comprobación del descanso reducido.
Añadir pruebas para las compensaciones pendientes.
Corregir el cálculo de las fechas límite.
```

# Resumen de comandos

| Comando | Propósito |
| --- | --- |
| `git add archivo` | Preparar los cambios de un archivo. |
| `git add .` | Preparar los cambios del directorio actual y sus subdirectorios. |
| `git status` | Consultar el estado del repositorio. |
| `git commit` | Guardar los cambios preparados. |
| `git commit -m "mensaje"` | Crear un commit con un mensaje. |
| `git commit -a` | Preparar y confirmar cambios de archivos rastreados. |
| `git commit -am "mensaje"` | Combinar las opciones `-a` y `-m`. |
| `git commit --interactive` | Seleccionar cambios interactivamente. |
| `git commit --no-verify` | Omitir determinados hooks de comprobación. |
| `git commit --amend` | Sustituir el último commit. |
| `git commit --amend --no-edit` | Sustituir el último commit conservando su mensaje. |
| `git commit --dry-run` | Simular la creación de un commit. |
| `git push` | Enviar commits a un repositorio remoto. |