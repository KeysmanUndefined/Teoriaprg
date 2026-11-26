# SVN vs. Git

## SVN: control de versiones centralizado

Existe un repositorio central que almacena el historial
del proyecto.

Los desarrolladores trabajan con copias de trabajo y
dependen del servidor para registrar nuevos commits.

## Git: control de versiones distribuido

Cada desarrollador dispone de un repositorio local
con su propio historial.

Permite realizar commits, consultar el historial y
trabajar con ramas sin conexión a Internet.

# Diferencias e instantáneas

- **SVN:** tradicionalmente se explica como un sistema
  que registra las diferencias entre versiones.
- **Git:** representa cada commit como una instantánea
  (snapshot) del estado del proyecto.

Git no duplica innecesariamente los archivos que no
han cambiado, sino que reutiliza referencias a su
contenido.

## Tabla comparativa

| Característica | SVN | Git |
|---|---|---|
| Arquitectura | Centralizada | Distribuida |
| Historial completo local | No | Sí, normalmente |
| Commits sin conexión | No | Sí |
| Modelo conceptual | Diferencias | Instantáneas |
| Repositorio central obligatorio | Sí | No |

# ¿Qué es GitFlow?

GitFlow es un modelo de ramificación (branching) que
propone una estrategia para organizar el desarrollo
y la generación de versiones de un producto utilizando Git.

Se basa en:

- Buenas prácticas de desarrollo.
- Un modelo organizado de ramas.
- Comandos de alto nivel para gestionar el flujo de trabajo.

## Tipos de ramas

| Rama | Finalidad |
|---|---|
| main | Versiones estables del producto. |
| develop | Desarrollo e integración de funcionalidades. |
| feature | Desarrollo de nuevas funcionalidades. |
| release | Preparación de una nueva versión. |
| hotfix | Corrección urgente de errores en producción. |

## Objetivos de GitFlow

- Separar el desarrollo de las versiones estables.
- Facilitar el trabajo colaborativo.
- Organizar la publicación de nuevas versiones.
- Corregir errores sin interrumpir el desarrollo.

GitFlow no es un sistema de control de versiones,
sino una metodología de trabajo basada en Git.

# Flujo de trabajo de GitFlow

GitFlow distingue dos tipos de ramas: principales y auxiliares.

## Ramas principales

- `master` (actualmente también denominada `main`).
- `develop`.

### Características

- Existe una única rama de cada tipo.
- Son ramas permanentes durante la vida del proyecto.
- No se realizan commits directamente sobre ellas.
- El código se incorpora mediante la integración de otras ramas (merge).
- Su nombre coincide con el tipo de rama.

## Ramas auxiliares

- `feature`: desarrollo de nuevas funcionalidades.
- `release`: preparación de nuevas versiones.
- `hotfix`: corrección urgente de errores en producción.

### Características

- Pueden crearse tantas ramas como sean necesarias.
- Son ramas temporales.
- Se trabaja y se realizan commits directamente sobre ellas.
- Se integran en las ramas correspondientes cuando finaliza el trabajo.
- Su nombre identifica el tipo de rama y su objetivo.

Ejemplos:

- `feature/67432-alta-usuario`
- `feature/calcular-descanso`
- `release/1.0.0`
- `hotfix/error-calculo`

## Comparación

| Característica | Principales | Auxiliares |
|---|---|---|
| Tipos | master, develop | feature, release, hotfix |
| Cantidad | Una de cada tipo | Múltiples |
| Duración | Permanente | Temporal |
| Commits directos | No | Sí |
| Finalidad | Mantener e integrar código | Desarrollar y corregir código |

# Ramas de GitFlow

## Rama master (main)

- Es la rama principal. Solo existe una.
- Contiene el código estable destinado a producción.
- No se realizan commits directamente sobre ella.
- Recibe código de otras ramas mediante merges.

## Rama develop

- Se crea a partir de master.
- Solo existe una rama develop.
- Contiene código funcional que todavía no está en producción.
- Recibe código de otras ramas mediante merges.
- Generalmente no se realizan commits directamente sobre ella.
- Permite mantener master estable mientras continúa el desarrollo.

## Ramas feature

- Se crean a partir de develop.
- Su nombre comienza por `feature/`.
- Contienen funcionalidades que están siendo desarrolladas.
- Se crean a partir del código actualizado de develop.
- Son temporales y deben evitar prolongarse innecesariamente.
- Cuando finaliza el desarrollo, se integran en develop.

Ejemplo:

```bash
feature/alta-usuario
```

## Ramas release

- Se crean a partir de develop cuando finaliza un conjunto
  de funcionalidades.
- Su nombre comienza por `release/`.
- Permiten congelar, probar y depurar una versión antes
  de pasarla a producción.
- Se permiten pequeñas correcciones directamente sobre ellas.
- Una vez finalizadas, se integran en master y develop.

Ejemplo:

```bash
release/1.2.0
```

## Ramas hotfix

- Se crean cuando se detecta un error urgente en producción.
- Se crean a partir de master.
- Su nombre comienza por `hotfix/`.
- Permiten corregir errores sin esperar a la siguiente versión.
- Una vez corregido el error, se integran en master y develop.
- Si existe una release activa, la corrección debe incorporarse
  también a ella.

Ejemplo:

```bash
hotfix/1.2.1
```

## Resumen de ramas

| Rama | Origen | Destino | Finalidad |
|---|---|---|---|
| master | - | - | Producción |
| develop | master | - | Integración del desarrollo |
| feature | develop | develop | Nuevas funcionalidades |
| release | develop | master y develop | Preparar versiones |
| hotfix | master | master y develop | Correcciones urgentes |

# Adaptación de GitFlow al entorno

GitFlow puede adaptarse a las necesidades de cada equipo.

| Entorno | Adaptación |
|---|---|
| Equipo de QA independiente | Incorporar una rama qa para pruebas. |
| Entorno muy ágil | Prescindir de develop y utilizar master como rama de integración. |
| Equipo pequeño | Utilizar únicamente master y ramas feature. |

No es obligatorio utilizar todas las ramas del modelo.

# Git Flow: extensión de Git

Git Flow también es una extensión de Git que proporciona
comandos de alto nivel para gestionar repositorios basados
en el modelo de ramificación definido por Vincent Driessen.

## Ventajas

- Simplifica la gestión de las ramas.
- Automatiza operaciones habituales.
- Es fácil de utilizar.
- Está integrado en algunas interfaces gráficas, como Sourcetree.

## Inconvenientes

- Puede ocultar las operaciones internas de Git.
- Algunos desarrolladores prefieren utilizar los comandos clásicos.
- Puede resultar innecesariamente complejo para proyectos pequeños.

## Requisitos

- Tener Git instalado.
- Tener instalada la extensión Git Flow o una herramienta compatible.
- Disponer de un sistema Windows, Linux o macOS.

# Comandos de alto nivel de Git Flow

## Inicializar Git Flow

```bash
git flow init
```

## Crear una funcionalidad

```bash
git flow feature start alta-usuario
```

## Finalizar una funcionalidad

```bash
git flow feature finish alta-usuario
```

Este comando equivale aproximadamente a ejecutar:

```bash
git checkout develop
git merge --no-ff feature/alta-usuario
git branch -d feature/alta-usuario
```

Para publicar los cambios en el repositorio remoto:

```bash
git push origin develop
```

## Crear y finalizar una release

```bash
git flow release start 1.2.0
git flow release finish 1.2.0
```

## Crear y finalizar un hotfix

```bash
git flow hotfix start 1.2.1
git flow hotfix finish 1.2.1
```
# Instalación de Git Flow

Git Flow es una extensión de Git, por lo que es necesario
tener Git instalado previamente.

## Debian / Ubuntu

```bash
sudo apt-get install git-flow
```

## Fedora / Red Hat / CentOS

```bash
sudo dnf install gitflow
```

## macOS

Mediante Homebrew:

```bash
brew install git-flow-avh
```

Mediante MacPorts:

```bash
sudo port install git-flow-avh
```

## Windows

Git for Windows puede incluir Git Flow, dependiendo
de la versión y distribución instalada.

## Comprobar la instalación

Comprobar que Git está instalado:

```bash
git --version
```

Comprobar que Git Flow está instalado:

```bash
git flow
git flow version
```

# Inicializar un repositorio con Git Flow

## Crear el directorio del proyecto

```bash
mkdir gitflow-Project
cd gitflow-Project
```

## Inicializar Git Flow

```bash
git flow init
```

Durante la inicialización se configuran:

- Rama de producción: master o main.
- Rama de desarrollo: develop.
- Prefijo de funcionalidades: feature/.
- Prefijo de versiones: release/.
- Prefijo de correcciones urgentes: hotfix/.
- Prefijo de ramas de soporte: support/.
- Prefijo de etiquetas de versión.

Para aceptar directamente la configuración predeterminada:

```bash
git flow init -d
```

## Comprobar las ramas creadas

```bash
git branch
```

Resultado habitual:

```text
* develop
  master
```

El asterisco indica la rama en la que estamos trabajando.

# Diferencia entre git init y git flow init

| Comando | Función |
|---|---|
| git init | Inicializa un repositorio Git. |
| git flow init | Inicializa y configura un repositorio para trabajar con GitFlow. |
| git flow init -d | Utiliza la configuración predeterminada. |
| git branch | Lista las ramas locales. |

# Comandos de GitFlow y su equivalencia en Git

GitFlow proporciona comandos de alto nivel que automatizan
operaciones realizadas mediante comandos tradicionales de Git.

# Ramas master y develop

## Inicializar un repositorio

GitFlow:

```bash
git flow init
```

Git:

```bash
git init
```

Clonar un repositorio existente:

```bash
git clone <ubicacion>
```

## Crear develop a partir de master

```bash
git branch develop master
```

Crear la rama y cambiar a ella:

```bash
git checkout -b develop master
```

Publicar develop:

```bash
git push origin develop
```

## Integrar develop en master

```bash
git checkout master
git merge --no-ff develop
git push origin master
```

En GitFlow, normalmente esta integración se realiza
mediante una rama release.

# Ramas feature

Las ramas feature se crean a partir de develop y,
cuando finalizan, se integran nuevamente en develop.

## Consultar comandos disponibles

```bash
git flow feature help
```

## Listar funcionalidades

```bash
git flow feature list
```

## Crear una feature

GitFlow:

```bash
git flow feature start alta-usuario
```

Git:

```bash
git checkout -b feature/alta-usuario develop
```

## Publicar una feature

GitFlow:

```bash
git flow feature publish alta-usuario
```

Git:

```bash
git push -u origin feature/alta-usuario
```

## Obtener una feature remota

GitFlow:

```bash
git flow feature track alta-usuario
```

Git:

```bash
git fetch origin
git checkout --track origin/feature/alta-usuario
```

## Actualizar una feature

GitFlow:

```bash
git flow feature pull origin alta-usuario
```

Git, desde la rama feature correspondiente:

```bash
git pull origin feature/alta-usuario
```

## Finalizar una feature

GitFlow:

```bash
git flow feature finish alta-usuario
```

Git:

```bash
git checkout develop
git merge --no-ff feature/alta-usuario
git branch -d feature/alta-usuario
```

Publicar los cambios:

```bash
git push origin develop
```

## Eliminar una feature

GitFlow:

```bash
git flow feature delete alta-usuario
```

Git:

```bash
git branch -d feature/alta-usuario
```

# Ramas release

Las ramas release se crean a partir de develop y
permiten preparar una versión para producción.

## Consultar comandos disponibles

```bash
git flow release help
```

## Listar releases

```bash
git flow release list
```

## Crear una release

GitFlow:

```bash
git flow release start 1.0.0
```

Git:

```bash
git checkout -b release/1.0.0 develop
```

## Publicar una release

GitFlow:

```bash
git flow release publish 1.0.0
```

Git:

```bash
git push -u origin release/1.0.0
```

## Obtener una release remota

GitFlow:

```bash
git flow release track 1.0.0
```

Git:

```bash
git fetch origin
git checkout --track origin/release/1.0.0
```

## Finalizar una release

GitFlow:

```bash
git flow release finish 1.0.0
```

Git:

```bash
git checkout master
git merge --no-ff release/1.0.0
git tag -a 1.0.0 -m "Version 1.0.0"

git checkout develop
git merge --no-ff release/1.0.0

git branch -d release/1.0.0
```

Publicar las ramas y la etiqueta:

```bash
git push origin master
git push origin develop
git push origin 1.0.0
```

## Eliminar una release

```bash
git flow release delete 1.0.0
```

# Ramas hotfix

Las ramas hotfix se crean a partir de master para
corregir errores urgentes en producción.

## Consultar comandos disponibles

```bash
git flow hotfix help
```

## Listar hotfix

```bash
git flow hotfix list
```

## Crear un hotfix

GitFlow:

```bash
git flow hotfix start 1.0.1
```

Git:

```bash
git checkout -b hotfix/1.0.1 master
```

## Publicar un hotfix

GitFlow:

```bash
git flow hotfix publish 1.0.1
```

Git:

```bash
git push -u origin hotfix/1.0.1
```

## Actualizar un hotfix

Desde la rama correspondiente:

```bash
git pull origin hotfix/1.0.1
```

## Finalizar un hotfix

GitFlow:

```bash
git flow hotfix finish 1.0.1
```

Git:

```bash
git checkout master
git merge --no-ff hotfix/1.0.1
git tag -a 1.0.1 -m "Version 1.0.1"

git checkout develop
git merge --no-ff hotfix/1.0.1

git branch -d hotfix/1.0.1
```

Publicar los cambios:

```bash
git push origin master
git push origin develop
git push origin 1.0.1
```

## Eliminar un hotfix

```bash
git flow hotfix delete 1.0.1
```

# Merge --no-ff (No Fast Forward)

```bash
git merge --no-ff feature/alta-usuario
```

La opción `--no-ff` fuerza la creación de un commit
de integración cuando hay cambios que integrar,
incluso cuando sería posible realizar un fast-forward.

## Ventajas

- Conserva la estructura de las ramas en el historial.
- Permite identificar los cambios asociados a una funcionalidad.
- Facilita la revisión del historial.
- Facilita revertir una integración completa.

Consultar el historial gráficamente:

```bash
git log --oneline --graph --all
```

Revertir un commit de integración:

```bash
git revert -m 1 identificador_merge
```

La opción `-m 1` indica que se toma el primer padre
del merge como línea principal de referencia.

# Revisión por pares (Peer Review)

La revisión por pares consiste en revisar el código
desarrollado por otros miembros del equipo.

Su objetivo es detectar defectos en fases tempranas,
proponer mejoras y comprobar el cumplimiento de los
estándares de codificación.

## Participantes

- Compañeros de trabajo.
- Miembros del equipo de desarrollo.
- Responsables de calidad.
- Personas implicadas en el producto.

## Beneficios

- Detectar errores antes de llegar a producción.
- Mejorar la calidad del código.
- Establecer y mantener estándares.
- Obtener diferentes puntos de vista.
- Compartir conocimientos.
- Generar métricas para mejorar el desarrollo.
- Reducir la frustración provocada por errores.

## Inconvenientes

- Pueden aparecer conflictos por diferencias de criterio.
- La influencia de un líder puede reducir la independencia
  de otros revisores.
- Aumenta el tiempo dedicado a revisar código.
- Puede aumentar el coste inicial del desarrollo.
- Puede requerir herramientas adicionales.

## Buenas prácticas

- Realizar revisiones pequeñas y atómicas.
- Evitar incluir demasiados cambios en una revisión.
- Dividir funcionalidades complejas en partes pequeñas.
- Revisar el código, no juzgar al desarrollador.
- Proponer mejoras justificadas.

## Costes y beneficios

La revisión por pares supone una inversión de tiempo
y recursos a corto plazo.

A largo plazo puede reducir los costes de mantenimiento,
la cantidad de defectos y el trabajo necesario para
corregir errores.

El time-to-market puede aumentar inicialmente, aunque
la detección temprana de errores puede compensarlo.

