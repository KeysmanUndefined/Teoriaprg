# GitFlow: resumen general

GitFlow es un modelo de ramificación propuesto por
Vincent Driessen para organizar el desarrollo,
mantenimiento y publicación de versiones de software.

## Tipos de ramas

### Ramas principales

- Existe una única rama de cada tipo.
- Son permanentes.
- Generalmente no reciben commits directos.
- Reciben código mediante merges de otras ramas.

### Ramas auxiliares

- Pueden existir múltiples ramas de cada tipo.
- Son temporales.
- Permiten realizar commits directamente.
- Su nombre identifica su tipo y finalidad.
- Se eliminan normalmente después de su integración.

## Tabla de ramas

| Rama | Tipo | Origen | Destino | Finalidad |
|---|---|---|---|---|
| master | Principal | - | - | Producción |
| develop | Principal | master | - | Integración del desarrollo |
| feature | Auxiliar | develop | develop | Nuevas funcionalidades |
| release | Auxiliar | develop | master y develop | Preparación de versiones |
| hotfix | Auxiliar | master | master y develop | Correcciones urgentes |

## Características fundamentales

### master

- Contiene código estable destinado a producción.
- Recibe principalmente merges de release y hotfix.
- Las versiones del producto se identifican mediante tags.

### develop

- Contiene las funcionalidades integradas que todavía
  no están en producción.
- Recibe principalmente merges de feature.
- Permite integrar y verificar código sin afectar a master.

### feature

- Permite desarrollar nuevas funcionalidades o modificar
  funcionalidades existentes.
- Debe ser lo más pequeña y atómica posible.
- El código debe probarse antes de integrarlo en develop.

### release

- Permite congelar y preparar una versión.
- Admite pequeñas correcciones y ajustes.
- No deben incorporarse nuevas funcionalidades.
- Mientras se prepara la versión, develop puede continuar
  recibiendo nuevas funcionalidades.

### hotfix

- Permite corregir errores urgentes en producción.
- No necesita esperar a la siguiente release.
- La corrección debe incorporarse también al desarrollo.
- Genera normalmente una nueva versión del producto.

# Flujo de trabajo

```text
master ──────────────────────────── producción
   │                         ▲
   │                         │
develop ────────┬────────────┼──── desarrollo
   │            ▲            │
   │            │            │
feature ────────┘            │
                             │
release ─────────────────────┘
```

## Flujo de una funcionalidad

develop → feature → develop

## Flujo de una versión

develop → release → master y develop

## Flujo de una corrección urgente

master → hotfix → master y develop

# Extensión Git Flow

Git Flow también es una extensión que proporciona
comandos de alto nivel para automatizar las operaciones
del modelo GitFlow.

No es imprescindible instalar esta extensión para
trabajar siguiendo la metodología GitFlow.

Todas las operaciones pueden realizarse utilizando
los comandos tradicionales de Git.

## Comprobar la instalación

```bash
git --version
git flow version
```

## Inicializar un proyecto

```bash
mkdir proyecto
cd proyecto
git flow init
git branch
```

# Tabla general de comandos Git Flow

| Operación | Feature | Release | Hotfix |
|---|---|---|---|
| Ayuda | feature help | release help | hotfix help |
| Listar | feature list | release list | hotfix list |
| Crear | feature start | release start | hotfix start |
| Publicar | feature publish | release publish | hotfix publish |
| Finalizar | feature finish | release finish | hotfix finish |
| Eliminar | feature delete | release delete | hotfix delete |

Todos los comandos de la tabla deben estar precedidos
por `git flow`.

Los comandos disponibles pueden variar según la
implementación de Git Flow instalada.

# Significado de los subcomandos

| Subcomando | Función |
|---|---|
| help | Consultar la ayuda |
| list | Listar ramas de un tipo |
| start | Crear una rama auxiliar |
| publish | Publicar una rama en el repositorio remoto |
| track | Crear una rama local que siga una rama remota |
| pull | Obtener e integrar cambios remotos |
| finish | Finalizar e integrar una rama |
| delete | Eliminar una rama |

# Ejemplo completo de desarrollo

## 1. Crear una funcionalidad

```bash
git flow feature start calculadora
```

## 2. Desarrollar y guardar los cambios

```bash
git add .
git commit -m "feat: implementar calculadora"
```

## 3. Finalizar la funcionalidad

```bash
git flow feature finish calculadora
```

## 4. Preparar una versión

```bash
git flow release start 1.0.0
```

## 5. Realizar pruebas y correcciones

```bash
git add .
git commit -m "fix: corregir errores de la version"
```

## 6. Finalizar la versión

```bash
git flow release finish 1.0.0
```

## 7. Publicar los cambios

```bash
git push origin master
git push origin develop
git push --tags
```

## 8. Corregir un error urgente en producción

```bash
git flow hotfix start 1.0.1
```

Realizar las correcciones:

```bash
git add .
git commit -m "fix: corregir error en produccion"
```

Finalizar:

```bash
git flow hotfix finish 1.0.1
```

Publicar:

```bash
git push origin master
git push origin develop
git push --tags
```

# Conceptos clave para el examen

- Git es un sistema de control de versiones.
- GitFlow es un modelo de ramificación.
- Git Flow es también una extensión de Git.
- master representa producción.
- develop representa la integración del desarrollo.
- feature desarrolla funcionalidades.
- release prepara versiones.
- hotfix corrige errores urgentes.
- Los tags permiten identificar versiones.
- Un merge integra los cambios de una rama en otra.
- --no-ff conserva explícitamente la integración
  mediante un commit de merge cuando hay cambios que integrar.
- GitFlow puede adaptarse a las necesidades del equipo.

# Referencias

- [A successful Git branching model - Vincent Driessen](https://nvie.com/posts/a-successful-git-branching-model/)
- [Apuntes del profesor](https://gist.github.com/dfleta/78d991237155fdd061c3b22fad7a12f8)
- [Documentación oficial de Git](https://git-scm.com/docs)