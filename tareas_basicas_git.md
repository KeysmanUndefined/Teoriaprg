# Configuración de Git

Antes de utilizar Git, debemos configurar nuestra identidad.

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

## Configurar el editor de texto

Linux o macOS:

```bash
git config --global core.editor "/usr/bin/pico"
```

Windows con Visual Studio Code:

```bash
git config --global core.editor "code --wait"
```

## Consultar la configuración

```bash
git config --list
```

# Crear un repositorio Git

Creamos un directorio y accedemos a él:

```bash
mkdir repo
cd repo
```

## git init: inicializar un repositorio

```bash
git init
```

Este comando crea el directorio oculto `.git`, donde Git almacena
la información necesaria para gestionar el repositorio.

Podemos comprobarlo mediante:

```bash
ls -a
```

## Crear un archivo README

```bash
echo "# README" >> README.md
```

# Consultar la ayuda de Git

```bash
git help
git help status
```

Documentación oficial: https://git-scm.com/docs

# git status: consultar el estado del repositorio

Muestra el estado del directorio de trabajo y del área de
preparación (*staging area*).

```bash
git status
```

Para obtener una versión resumida:

```bash
git status -s
```

## Indicadores de estado

| Indicador | Significado |
|-----------|-------------|
| M | Modificado |
| A | Añadido |
| D | Eliminado |
| R | Renombrado |
| C | Copiado |
| U | Conflicto sin resolver |
| ?? | Archivo no rastreado |
| !! | Archivo ignorado |

La salida de `git status -s` utiliza dos columnas:

- Primera columna: estado en el área de preparación.
- Segunda columna: estado en el directorio de trabajo.

Ejemplos:

| Estado | Significado |
|--------|-------------|
| `?? README.md` | Archivo no rastreado |
| `A  README.md` | Archivo añadido al staging |
| ` M README.md` | Modificado sin preparar |
| `M  README.md` | Modificación preparada |
| `AM README.md` | Archivo añadido al staging y modificado posteriormente |
| `MM README.md` | Modificación preparada y modificado nuevamente |

# git add: preparar cambios

Añade archivos o modificaciones al área de preparación
(*staging area*).

```bash
git add README.md
```

Para preparar todos los cambios:

```bash
git add .
```

Si modificamos un archivo después de ejecutar `git add`,
los nuevos cambios no se incorporan automáticamente al staging.

Debemos ejecutar nuevamente `git add` para prepararlos.

# git diff: consultar diferencias

Permite visualizar las diferencias entre distintas versiones
de los archivos.

## Directorio de trabajo frente al staging

```bash
git diff
```

Muestra las modificaciones que todavía no se han preparado.

## Staging frente al último commit

```bash
git diff --staged
```

Muestra los cambios preparados para el siguiente commit.

## Diferencias entre ramas

```bash
git diff main develop
```

Para comparar únicamente un archivo:

```bash
git diff main develop -- README.md
```

# git commit: registrar cambios

Guarda una instantánea de los cambios que se encuentran
en el área de preparación.

```bash
git commit -m "docs: crear archivo README"
```

**Importante:** únicamente se registran los cambios que se
encuentran en el staging en el momento de ejecutar el commit.

# Conventional Commits

Es una convención para escribir mensajes de commit claros,
estructurados y fáciles de interpretar.

## Estructura

```text
<tipo>[ámbito opcional]: <descripción>

[cuerpo opcional]

[pie opcional]
```

## Tipos de commit

| Tipo | Finalidad |
|------|-----------|
| feat | Nueva funcionalidad |
| fix | Corrección de errores |
| docs | Cambios en la documentación |
| style | Cambios de formato del código |
| refactor | Reestructuración del código |
| perf | Mejoras de rendimiento |
| test | Añadir o modificar pruebas |
| build | Cambios en la compilación o dependencias |
| ci | Integración continua |
| chore | Tareas de mantenimiento |

## Ejemplos

```bash
git commit -m "feat: añadir calculadora"
git commit -m "fix: corregir cálculo del descanso"
git commit -m "docs: actualizar README"
git commit -m "test: añadir pruebas unitarias"
git commit -m "refactor: simplificar función de cálculo"
```

Documentación: https://www.conventionalcommits.org/es/v1.0.0/

# Resumen de comandos

| Comando | Función |
|---------|---------|
| git config | Configurar Git |
| git init | Inicializar un repositorio |
| git help | Consultar ayuda |
| git status | Consultar el estado |
| git status -s | Consultar el estado resumido |
| git add | Preparar cambios |
| git diff | Consultar cambios sin preparar |
| git diff --staged | Consultar cambios preparados |
| git commit | Registrar cambios |

# git log: consultar el historial

Muestra el historial de commits del repositorio, incluyendo:

- Identificador del commit (hash).
- Autor.
- Fecha.
- Mensaje del commit.

```bash
git log
```

Mostrar el historial de forma resumida:

```bash
git log --oneline
```

Mostrar el historial gráficamente:

```bash
git log --pretty=format:"%h %s" --graph
```

- `%h`: identificador abreviado del commit.
- `%s`: mensaje del commit.
- `--graph`: representación gráfica del historial.

Mostrar también los commits alcanzables desde las etiquetas:

```bash
git log --tags
```

# git show: consultar un commit

Muestra la información y los cambios introducidos por un commit.

```bash
git show
git show identificador_commit
```

Consultar el contenido de un archivo en un determinado commit:

```bash
git show identificador_commit:README.md
```

# git diff: consultar diferencias

## Directorio de trabajo y staging

```bash
git diff
```

Muestra los cambios que todavía no se han preparado.

## Staging y último commit

```bash
git diff --staged
```

Muestra los cambios preparados para el siguiente commit.

## Diferencias entre dos commits

```bash
git diff identificador1 identificador2
```

## Diferencias entre ramas

```bash
git diff master develop
```

# Deshacer cambios

## git reset: retirar archivos del staging

```bash
git reset HEAD README.md
```

Retira los cambios del área de preparación sin eliminar
las modificaciones del directorio de trabajo.

Actualmente también podemos utilizar:

```bash
git restore --staged README.md
```

## git checkout: descartar modificaciones

```bash
git checkout -- README.md
```

Restaura el archivo utilizando la versión almacenada
en el staging.

Para descartar las modificaciones no preparadas de
todos los archivos rastreados:

```bash
git checkout -- .
```

Actualmente también podemos utilizar:

```bash
git restore README.md
```

**Advertencia:** estos comandos pueden eliminar
modificaciones que todavía no hemos guardado en Git.

# git commit -am

```bash
git commit -am "Mensaje del commit"
```

Combina la preparación automática de las modificaciones
y eliminaciones de archivos rastreados con la creación
del commit.

- `-a`: prepara modificaciones y eliminaciones de archivos rastreados.
- `-m`: permite introducir el mensaje del commit.

No añade automáticamente archivos nuevos sin seguimiento.

# Eliminar archivos

## rm: eliminar un archivo del directorio de trabajo

```bash
rm tocino.txt
```

Git detectará que el archivo ha sido eliminado.

```bash
git status -s
```

Resultado:

```text
 D tocino.txt
```

La eliminación todavía no está preparada.

## git rm: eliminar y preparar la eliminación

```bash
git rm tocino.txt
```

Elimina el archivo del directorio de trabajo y prepara
su eliminación para el siguiente commit.

```bash
git status -s
```

Resultado:

```text
D  tocino.txt
```

Registramos la eliminación:

```bash
git commit -m "chore: eliminar tocino.txt"
```

El archivo desaparece de la versión actual del repositorio,
pero permanece en los commits anteriores.

## Recuperar un archivo eliminado

Si la eliminación todavía no está preparada:

```bash
git restore tocino.txt
```

Si la eliminación ya está preparada:

```bash
git restore --staged tocino.txt
git restore tocino.txt
```

## Eliminar un archivo del seguimiento sin borrarlo

```bash
git rm --cached tocino.txt
```

Elimina el archivo del índice de Git, pero lo conserva
en el directorio de trabajo.

# Revisar el historial de Git

## git log -p

Muestra el historial de commits junto con los cambios
introducidos por cada uno.

```bash
git log -p -2
```

- `-p`: muestra las diferencias introducidas por cada commit.
- `-2`: limita el resultado a los dos últimos commits.

## git ls-tree

Lista los archivos y directorios que forman parte de un commit.

```bash
git ls-tree identificador_commit
```

También podemos consultar el último commit:

```bash
git ls-tree HEAD
```

# Consultar un commit anterior

Podemos recuperar temporalmente el estado del proyecto
en un commit anterior:

```bash
git checkout identificador_commit
```

Git entra en un estado denominado **detached HEAD**.

En este estado, HEAD apunta directamente a un commit
en lugar de apuntar a una rama.

Podemos consultar archivos, realizar modificaciones
y experimentar sin modificar directamente ninguna rama.

Para conservar los cambios en una nueva rama:

```bash
git checkout -b nueva_rama
```

Para regresar a la rama principal:

```bash
git checkout main
```

# git commit --amend

Permite reemplazar el último commit.

Es especialmente útil cuando:

- Hemos olvidado incluir un archivo.
- Queremos corregir el mensaje.
- Queremos corregir pequeños errores.

## Modificar el mensaje del último commit

```bash
git commit --amend -m "Nuevo mensaje"
```

## Añadir un archivo olvidado

```bash
git add archivo_olvidado.py
git commit --amend
```

Para conservar el mensaje anterior:

```bash
git commit --amend --no-edit
```

**Importante:** amend reemplaza el último commit por otro.
Normalmente, el nuevo commit tiene un identificador diferente.

Se recomienda utilizar amend sobre commits que todavía
no se han publicado en el repositorio remoto.

# git mv: renombrar archivos

Permite renombrar un archivo y preparar el cambio
para el siguiente commit.

```bash
git mv README.txt README.md
```

Es equivalente a:

```bash
mv README.txt README.md
git rm README.txt
git add README.md
```

# .gitignore

Archivo que contiene las reglas para ignorar archivos
y directorios.

Habitualmente se encuentra en la raíz del proyecto.

Podemos utilizar plantillas específicas para cada
lenguaje de programación o framework.

Consultar los archivos ignorados:

```bash
git status --ignored
```

# Ramas (branches)

Una rama permite desarrollar funcionalidades de forma
independiente sin modificar directamente otras ramas.

## Listar ramas

```bash
git branch
```

Listar ramas de seguimiento remoto:

```bash
git branch -r
```

Listar todas las ramas:

```bash
git branch -a
```

Mostrar las ramas locales y sus ramas de seguimiento:

```bash
git branch -vv
```

## Crear una rama

```bash
git branch develop
```

## Cambiar de rama

```bash
git checkout develop
```

Alternativa moderna:

```bash
git switch develop
```

## Crear una rama y cambiar a ella

```bash
git checkout -b develop
```

Alternativa moderna:

```bash
git switch -c develop
```

## Volver a la rama anterior

```bash
git checkout -
```

## git merge: integrar ramas

Incorpora los cambios de otra rama en la rama actual.

```bash
git checkout main
git merge develop
```

Forzar la creación de un commit de fusión:

```bash
git merge --no-ff develop
```

## Comparar ramas

```bash
git diff main develop
```

## Renombrar la rama actual

```bash
git branch -m nuevo_nombre
```

Por ejemplo:

```bash
git branch -m main
```

## Configurar el nombre de la rama inicial

```bash
git config --global init.defaultBranch main
```

# Ramas remotas

## Publicar una rama local

```bash
git push -u origin develop
```

- `origin`: nombre del repositorio remoto.
- `develop`: nombre de la rama.
- `-u`: establece la relación de seguimiento.

Una vez establecida esta relación, normalmente podemos
utilizar simplemente:

```bash
git push
git pull
```

## Publicar una rama con otro nombre

```bash
git push origin rama_local:rama_remota
```

## Crear una rama local a partir de una remota

```bash
git checkout -t origin/develop
```

También podemos utilizar:

```bash
git checkout --track -b develop origin/develop
```

# Eliminar ramas

## Eliminar una rama local

```bash
git branch -d develop
```

Git comprueba que la rama esté integrada antes
de permitir su eliminación.

## Forzar la eliminación de una rama local

```bash
git branch -D develop
```

**Advertencia:** puede eliminar una rama que contiene
commits todavía no integrados.

## Eliminar una referencia local de seguimiento remoto

```bash
git branch -dr origin/develop
```

No elimina la rama del servidor remoto.

## Eliminar una rama del repositorio remoto

```bash
git push origin --delete develop
```

## Limpiar referencias a ramas remotas eliminadas

```bash
git fetch --prune
```

# git stash: guardar cambios temporalmente

Permite guardar temporalmente modificaciones sin
necesidad de crear un commit.

Es útil cuando estamos trabajando en una funcionalidad
y necesitamos cambiar de rama sin terminar el trabajo.

## Crear un stash

```bash
git stash
```

Crear un stash con un mensaje:

```bash
git stash push -m "Trabajo pendiente"
```

Sintaxis antigua:

```bash
git stash save "Trabajo pendiente"
```

## Listar los stash

```bash
git stash list
```

## Consultar los cambios guardados

```bash
git stash show -p stash@{0}
```

## Recuperar cambios

```bash
git stash apply stash@{0}
```

Recupera los cambios y conserva el stash.

```bash
git stash pop stash@{0}
```

Recupera los cambios y elimina el stash si se aplica
correctamente.

## Eliminar un stash

```bash
git stash drop stash@{0}
```

## Eliminar todos los stash

```bash
git stash clear
```

## Guardar también archivos sin seguimiento

```bash
git stash push -u -m "Trabajo pendiente"
```

## Guardar archivos sin seguimiento e ignorados

```bash
git stash push -a -m "Trabajo pendiente"
```

- `-u` o `--include-untracked`: incluye archivos sin seguimiento.
- `-a` o `--all`: incluye también los archivos ignorados.