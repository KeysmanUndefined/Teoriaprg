# Funcionamiento de `git commit`

El repositorio local es el lugar donde se registran las instantáneas (*snapshots*) de Git.

Git permite acumular commits en un repositorio local, en lugar de realizar un cambio y enviarlo inmediatamente al repositorio central.

# Ignorar archivos mediante `.gitignore`

Un archivo `.gitignore` indica qué archivos debe ignorar Git porque, intencionadamente, no se desea realizar un seguimiento de ellos.

Git clasifica los archivos en tres categorías:

- **Tracked (rastreados):** archivos que previamente han sido añadidos al área de preparación o registrados mediante un commit.
- **Untracked (no rastreados):** archivos que todavía no han sido añadidos al área de preparación ni registrados mediante un commit.
- **Ignored (ignorados):** archivos que Git ignora según las reglas establecidas.

Git permite seleccionar qué archivos deben ignorarse.

Cuando queremos ignorar nuevos archivos, debemos modificar manualmente el archivo `.gitignore` y registrar los cambios mediante un commit si queremos compartirlos.

## Ejemplo práctico

```gitignore
# Entorno virtual de Python
.venv/

# Archivos compilados de Python
__pycache__/
*.pyc

# Variables de entorno y credenciales
.env

# Archivos temporales
*.tmp
*.log

# Caché de herramientas
.pytest_cache/
.ruff_cache/

# Archivos del sistema
Thumbs.db
.DS_Store
```

**Importante:** `.gitignore` no deja de rastrear archivos que Git ya está rastreando. Para ello podemos utilizar:

```bash
git rm --cached archivo.txt
```

Este comando elimina el archivo del índice de Git, pero lo conserva en nuestro equipo.