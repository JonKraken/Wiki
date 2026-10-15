# Wiki
Wiki de comandos de Git y GitHub con ejemplos

# Guía rápida de comandos Git

Este README recoge los comandos Git más usados, con una explicación breve y ejemplos de uso. Está pensado como referencia para trabajar con repositorios locales y remotos.

---

## Configuración inicial

- `git config --global user.name "Tu Nombre"`
  - Define tu nombre de usuario para los commits.

- `git config --global user.email "tucorreo@ejemplo.com"`
  - Define tu email para los commits.

- `git config --list`
  - Muestra la configuración actual.

---

## Crear y clonar repositorios

- `git init`
  - Inicializa un nuevo repositorio Git en el directorio actual.
  - Ejemplo: `git init`.

- `git clone <url>`
  - Clona un repositorio remoto a una carpeta local.
  - Ejemplo: `git clone https://github.com/usuario/proyecto.git`.

---

## Estado y cambios

- `git status`
  - Muestra el estado del working directory y el área de staging.
  - Ejemplo: `git status -s` (resumen corto).

- `git add <archivo>`
  - Añade archivos al área de staging (preparándolos para commit).
  - Ejemplo: `git add README.md` o `git add .` para todos los cambios.

- `git diff`
  - Muestra las diferencias entre el working directory y el área de staging.
  - `git diff --staged` muestra diferencias entre staging y último commit.

- `git commit -m "mensaje"`
  - Crea un commit con los cambios en el área de staging.
  - Ejemplo: `git commit -m "Arregla bug en la validación"`.

- `git commit --amend`
  - Modifica el último commit (útil para corregir mensaje o añadir cambios olvidados).
  - Atención: no usar si ya has pusheado ese commit a un remoto compartido.

- `git log`
  - Muestra el historial de commits.
  - Ejemplo: `git log --oneline --graph --all` para vista compacta y gráfica.

---

## Ramas (branches)

- `git branch`
  - Lista ramas locales.
  - `git branch <nombre>` crea una rama nueva.

- `git checkout <rama>`
  - Cambia a la rama especificada (antiguo comando; ver `git switch`).

- `git switch <rama>`
  - Cambia a otra rama.
  - `git switch -c <nueva-rama>` crea y cambia a una nueva rama.

- `git merge <rama>`
  - Fusiona la rama indicada en la rama actual.
  - Puede generar conflictos que habrá que resolver manualmente.

- `git rebase <base>`
  - Reaplica commits de la rama actual sobre `base`. Usado para mantener historial lineal.
  - Atención con rebase sobre commits compartidos.

---

## Actualizar desde remoto y enviar cambios

- `git remote -v`
  - Muestra los remotos configurados y sus URLs.

- `git remote add origin <url>`
  - Añade un remoto llamado `origin`.

- `git fetch`
  - Descarga los objetos y referencias desde el remoto pero no fusiona.

- `git pull`
  - Equivalente a `git fetch` + `git merge` por defecto: trae cambios y los mezcla con la rama actual.
  - `git pull --rebase` aplica los commits locales encima de los cambios remotos (evita merges automáticos).

- `git push <remoto> <rama>`
  - Envía commits locales al remoto.
  - Ejemplo: `git push origin main`.

- `git push --set-upstream origin <rama>`
  - Empuja una rama nueva y vincula la rama local con la remota.

---

## Recuperación y manipulación de commits

- `git reset --soft <commit>`
  - Mueve HEAD a `<commit>` pero conserva los cambios en staging.

- `git reset --mixed <commit>` (por defecto)
  - Mueve HEAD a `<commit>` y deja los cambios en working directory (no staged).

- `git reset --hard <commit>`
  - Mueve HEAD a `<commit>` y descarta todos los cambios en staging y working directory. Usar con cuidado.

- `git revert <commit>`
  - Crea un nuevo commit que invierte los cambios de `<commit>` (seguro para repositorios compartidos).

- `git cherry-pick <commit>`
  - Aplica el cambio de un commit específico en la rama actual.

---

## Stash (guardar trabajo temporalmente)

- `git stash`
  - Guarda cambios del working directory y limpia el directorio para cambiar de rama.

- `git stash list`
  - Lista los stashes guardados.

- `git stash apply` o `git stash pop`
  - `apply` aplica el stash seleccionado sin borrarlo; `pop` lo aplica y lo elimina de la lista.

---

## Etiquetas (tags)

- `git tag`
  - Lista tags locales.

- `git tag -a v1.0 -m "Versión 1.0"`
  - Crea un tag anotado.

- `git push origin --tags`
  - Empuja tags al remoto.

---

## Submódulos

- `git submodule add <url> <ruta>`
  - Añade un submódulo al repositorio.

- `git submodule update --init --recursive`
  - Inicializa y actualiza submódulos.

---

## Otras utilidades útiles

- `git rm <archivo>`
  - Elimina un archivo y añade la eliminación al siguiente commit.

- `git mv <viejo> <nuevo>`
  - Mueve/renombra un archivo y registra el cambio.

- `git clean -fd`
  - Elimina archivos y directorios no rastreados. Usar con precaución; probar `git clean -n` antes.

- `git bisect start` / `git bisect bad` / `git bisect good <commit>`
  - Herramienta para localizar el commit que introdujo un bug (búsqueda binaria).

- `git blame <archivo>`
  - Muestra qué commit y autor introdujo cada línea del archivo.

- `git show <commit>`
  - Muestra detalles y diff de un commit específico.

- `git log --follow -- <archivo>`
  - Muestra historial de un archivo incluso si fue renombrado.

- `git fetch --all --prune`
  - Trae todos los remotos y elimina referencias remotas que ya no existen.

---

## Buenas prácticas rápidas

- Haz commits pequeños y con mensajes claros.
- Usa ramas para desarrollar características (feature branches) y PRs para integrar cambios.
- Evita reescribir historial (rebase, reset) en ramas que ya compartiste; si lo haces, avisa al equipo.
- Revisa antes de pushear: `git status`, `git diff`, `git log --oneline`.

---

Si quieres, puedo:
- Añadir ejemplos más detallados para alguno de los comandos.
- Formatearlo en secciones por nivel (básico/intermedio/avanzado).
- Incluir alias útiles para la configuración (`.gitconfig`).
