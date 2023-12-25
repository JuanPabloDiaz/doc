---
layout: post
title: "Automatiza tus commits diarios con GitHub Actions"
date: 2023-12-22
categories: git
tags: git github githubactions shell devops
image: /assets/img/featured-posts/github.jpg
---

# Automatiza tus commits diarios con GitHub Actions

Un día me propuse un desafío: **hacer un commit diario en GitHub durante todo un año**. Ahora que ya tengo la disciplina de escribir código de manera constante. Se me ocurrió que quiero automatizar este proceso, y así mismo aprender a hacerlo. Pero ¿cómo podría automatizar un commit diario en GitHub? ¿Sera que existe alguna herramienta o script que pueda usar para hacer commits automáticos? Estas eran las preguntas claves que debía resolver.

Después de investigar un poco, encontré que puedo automatizar este proceso utilizando **GitHub Actions**, que es una herramienta de _CI/CD_ integrada en GitHub. Sin más preambulos, en este artículo te mostraré un ejemplo de cómo podrías configurar un flujo de trabajo para hacer un commit diario a tu repositorio de manera automática.

Primero, necesitarás un **script que realice el commit**. Aquí hay un ejemplo simple de un **script de shell** que podría hacer esto (.github/scripts/auto_commit.sh):

```bash
#.github/scripts/auto_commit.sh

#!/bin/sh

# Crea un nuevo archivo con la fecha y hora actual como contenido. Si ya existe un archivo, reemplaza el contenido con la fecha y hora actual.

echo $(date) > commit.txt

# Agrega el nuevo archivo al staging area
git add commit.txt

# Hace un commit con un mensaje
git commit -m "Commit automatizado"

# Empuja los cambios a GitHub
git push origin main
```

Luego, necesitarás **crear un archivo del flujo de trabajo ("workflow") de GitHub Actions para ejecutar este script una vez al día**. Este archivo define una serie de pasos que se ejecutan automáticamente en respuesta a eventos específicos de GitHub, como un push o un pull request. Aquí hay un ejemplo de cómo podría ser ese archivo del flujo de trabajo (.github/workflows/daily-commit.yml):

```yaml
name: Daily Commit

on:
  schedule:
    - cron: "0 0 * * *" # Esto se ejecutará todos los días a medianoche

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Run script
        run: bash /path/to/your/auto_commit_script.sh
```

Este flujo de trabajo se ejecutará todos los días a medianoche y ejecutará tu script, que hará un commit y lo empujará a tu repositorio.

Nota: Asegúrate de reemplazar `/path/to/your/repo` y `/path/to/your/script.sh` con las rutas reales a tu repositorio y a tu script, respectivamente. Además, este script asume que estás trabajando en la rama `main`. Si estás trabajando en una rama diferente, reemplaza main con el nombre de tu rama.

Además, necesitarás **configurar las credenciales de Git** en el flujo de trabajo de GitHub Actions para que puedas empujar a tu repositorio. Puedes hacer esto utilizando un **token** de acceso personal de GitHub y configurándolo como una **variable de entorno** en tu flujo de trabajo.

Es importante tener en cuenta que **no es una buena práctica almacenar las credenciales de Git en texto plano**. Sin embargo, en este caso, no hay forma de evitarlo, ya que el flujo de trabajo de GitHub Actions se ejecuta en un entorno aislado y no tienes acceso a las credenciales de Git almacenadas en tu máquina local. Por lo tanto, _necesitarás crear un token de acceso personal de GitHub_ y _configurarlo como una variable de entorno_ en tu flujo de trabajo.

## ¿Cómo configurar las credenciales de Git?

Para _configurar las credenciales de Git_ en el flujo de trabajo de GitHub Actions, necesitarás un **token de acceso personal de GitHub**. Aquí te explico cómo hacerlo:

### 1. Genera un **`token de acceso personal en GitHub`**:

- Ve a la configuración de tu cuenta de GitHub (haz clic en tu foto de perfil en la esquina superior derecha y selecciona **`"Settings"`** (Configuración) ).
- En el menú de la izquierda, selecciona **`"Developer settings"`** (Configuración de desarrollador).
- Luego, selecciona **`"Personal access tokens"`** (Tokens de acceso personal).
- Haz clic en **`"Generate new token"`** (Generar nuevo token).
- Dale un **nombre descriptivo** a tu token.
- Selecciona los **permisos** que necesitas para tu flujo de trabajo, en este caso, necesitarás el **`permiso repo`** y haz clic en **`"Generate token"`** (Generar token).

### 2. **Configura el token** de acceso personal **como una variable de entorno** en tu flujo de trabajo:

En tu archivo del flujo de trabajo (.github/workflows/daily-commit.yml), debes agregar una _nueva etapa_ antes de la etapa **`Run script`** para **configurar las credenciales de Git**. Aquí te muestro cómo:

- Opción 1:

```yaml
- name: Set up Git credentials
  run: |
    git config --global user.name "your-username"
    git config --global user.email "your-email@example.com"
    git config --global credential.helper store
    echo "https://$TOKEN:x-oauth-basic@github.com" > ~/.git-credentials
  env:
    TOKEN: ${{ secrets.YOUR_GITHUB_TOKEN }}
```

> Nota:
>
> - Reemplaza **"your-username"** y **"your-email@example.com"** con tu nombre de usuario de GitHub y tu correo electrónico.
> - En la última línea, `TOKEN` es una variable de entorno que contiene tu token de acceso personal. Necesitarás agregar este token a las **"Secrets"** de tu repositorio en GitHub (más sobre esto más adelante).

- Opción 2:

```yaml
- name: Set up Git credentials
  run: |
    git config --global user.name ""your-username"
    git config --global user.email "your-email@example.com"
    git remote set-url origin https://${{ secrets.YOUR_GITHUB_TOKEN }}@github.com/username/repo.git
```

> Nota:
>
> - Al igual que en opción 1, reemplaza **"your-username"** y **"your-email@example.com"** con tu nombre de usuario de GitHub y tu correo electrónico.

<details>
<summary>Así debería estar quedando el archivo de workflow de GitHub Actions</summary>

```yaml
# .github/workflows/daily-commit.yml
name: Daily Commit

on:
  schedule:
    - cron: "0 0 * * *"

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Set up Git credentials
        run: |
          git config --global user.name ""your-username"
          git config --global user.email "your-email@example.com"
          git remote set-url origin https://${{ secrets.YOUR_GITHUB_TOKEN }}@github.com/username/repo.git
```

</details>

#### ¿Cuales son las diferencias entre las opciones 1 y 2?

La principal diferencia entre estos dos fragmentos de código es cómo se manejan las credenciales de Git:

- En la **Opción 1**, se utiliza `git config --global credential.helper store` para almacenar las credenciales de usuario en un archivo en su directorio local. Luego, se crea un archivo `.git-credentials` en el directorio home del usuario con la URL que incluye el token de autenticación. Este método almacena las credenciales en un archivo en texto plano en su sistema.

- En la **Opción 2**, se utiliza `git remote set-url origin` para cambiar la URL del repositorio remoto 'origin' a una que incluya el token de autenticación. Este método no almacena las credenciales en su sistema, sino que las incluye en la URL del repositorio remoto.

Ambos métodos tienen sus ventajas y desventajas. El almacenamiento de credenciales es más seguro, ya que no expone el token en la línea de comandos, pero puede ser menos seguro si otras personas tienen acceso a su sistema. El uso de la URL del repositorio remoto es menos seguro ya que expone el token en la línea de comandos, pero puede ser más seguro si tu sistema es seguro y sólo tu tiene acceso a él.

### 3. Agrega tu token de acceso personal a las **`"Secrets"`** de tu repositorio:

- Ve a la página principal de tu repositorio en GitHub y selecciona **`"Settings"`** (Configuración).
- Luego, selecciona **`"Secrets"`** en el menú de la izquierda.
- Haz clic en **`"New repository secret"`** (Nuevo secreto del repositorio).
- Ingresa **`YOUR_GITHUB_TOKEN`** como el nombre del secreto y pega tu token de acceso personal en el campo **`Value`** (Valor).
- Haz clic en **`"Add secret"`** (Agregar secreto).

Ahora, tu flujo de trabajo de GitHub Actions debería ser capaz de empujar a tu repositorio utilizando tu token de acceso personal.

### 4. Ejecuta tu flujo de trabajo de GitHub Actions manualmente:

En el archivo del flujo de trabajo de GitHub Actions, debes agregar un **evento** que permita ejecutar el flujo de trabajo manualmente. Aquí te muestro cómo:

```yaml
on:
  workflow_dispatch: # This allows you to manually trigger the workflow
```

Ahora, puedes ejecutar tu flujo de trabajo de GitHub Actions manualmente haciendo clic en el botón **`"Run workflow"`** (Ejecutar flujo de trabajo) en la página principal de tu repositorio en GitHub.

<details>
<summary>Así debería estar quedando el archivo de workflow de GitHub Actions</summary>

```yaml
# .github/workflows/daily-commit.yml
name: Daily Commit

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch: # This allows you to manually trigger the workflow

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Set up Git credentials
        run: |
          git config --global user.name ""your-username"
          git config --global user.email "your-email@example.com"
          git remote set-url origin https://${{ secrets.YOUR_GITHUB_TOKEN }}@github.com/username/repo.git
```

</details>

## Error al ejecutar el script de Shell.

Si llegaste hasta acá y aun no puedes ejecutar el script de shell, asegúrate de que el script de shell tenga **`permisos de ejecución`**. Puedes hacer esto agregando el siguiente comando a tu flujo de trabajo de GitHub Actions:

```yaml
- name: Run script
  run: |
    chmod +x ./.github/scripts/auto_commit.sh
    bash ./.github/scripts/auto_commit.sh
```

<details>
<summary>Así debería estar quedando el archivo de workflow de GitHub Actions</summary>

```yaml
# .github/workflows/daily-commit.yml
name: Daily Commit

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch: # This allows you to manually trigger the workflow

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Set up Git credentials
        run: |
          git config --global user.name ""your-username"
          git config --global user.email "your-email@example.com"
          git remote set-url origin https://${{ secrets.YOUR_GITHUB_TOKEN }}@github.com/username/repo.git

      - name: Run script
        run: |
          chmod +x ./.github/scripts/auto_commit.sh
          bash ./.github/scripts/auto_commit.sh
```

</details>

## Error después de correr GitHub Actions

En este punto, el script de Shell ya corre pero genera un error al intentar hacer el commit y empujar los cambios a tu repositorio. Aquí hay un ejemplo de lo que podría verse en la pestaña **`"Actions"`** (Acciones) de tu repositorio en GitHub:

```bash
Run chmod +x ./.github/scripts/auto_commit.sh
[main 8a928cc] Commit automatizado
 1 file changed, 1 insertion(+)
 create mode 100644 commit.txt
remote: Write access to repository not granted.
fatal: unable to access 'https://github.com/username/repoName.git/': The requested URL returned error: 403
Error: Process completed with exit code 128.
```

Este error significa que el **flujo de trabajo** de GitHub Actions **NO tiene los permisos** necesarios para escribir/empujar a tu repositorio. Esto puede suceder por varias razones:

- Puede ser que el **token de acceso personal que configuraste NO tenga los permisos correctos**. Asegúrate de que el _token de acceso personal_ tenga el permiso **repo**.
- Asegúrate que el _token de acceso personal_ esté **bien escrito** en el archivo del flujo de trabajo y en las **"Secrets"** de tu repositorio.
- Asegúrate que los _permisos a los trabajos_ estén bien asignados en el archivo del flujo de trabajo.

#### Asignar permisos a los trabajos

Necesitarás asignar los **permisos a los trabajos** en un flujo de trabajo utilizando la palabra clave **`"permissions"`**. En este caso, debería asignar el permiso **`"contents"`** al trabajo que estás ejecutando en el script. Aquí te muestro cómo:

```yaml
permissions: # Permisos para el flujo de trabajo - Esto es necesario para crear un commit
  issues: write
  pull-requests: write
  contents: write
```

Conoce más sobre los permisos de los trabajos en [Asignar permisos a los trabajos](https://docs.github.com/en/actions/using-jobs/assigning-permissions-to-jobs).

---

En resumen, para automatizar tus commits diarios en GitHub con GitHub Actions, necesitarás un script que realice el commit y un flujo de trabajo de GitHub Actions que ejecute ese script una vez al día. Además, necesitarás configurar las credenciales de Git en el flujo de trabajo para que puedas empujar a tu repositorio. Esto se puede hacer utilizando un token de acceso personal de GitHub y configurándolo como una variable de entorno en tu flujo de trabajo. Finalmente, necesitarás asignar los permisos correctos a tu flujo de trabajo para que pueda crear un commit y empujar a tu repositorio. Aquí te dejo los archivos que necesitarás para hacer esto:

## Flujo de Trabajo de GitHub Actions

Aquí está el archivo del _flujo de trabajo_ (workflow) completo:

```yaml
# .github/workflows/daily-commit.yml
name: Daily Commit

on:
  schedule:
    - cron: "0 0 * * *" # Esto se ejecutará todos los días a medianoche
  workflow_dispatch: # esto permite ejecutar el flujo de trabajo manualmente

jobs:
  build:
    runs-on: ubuntu-latest

    permissions: # Otorga los permisos para el flujo de trabajo - Esto es necesario para crear un commit
      issues: write
      pull-requests: write
      contents: write

    steps:
      - uses: actions/checkout@v2

      - name: Set up Git credentials # Configura las credenciales de Git
        run: |
          git config --global user.name ""your-username"
          git config --global user.email "your-email@example.com"
          git remote set-url origin https://${{ secrets.YOUR_GITHUB_TOKEN }}@github.com/username/repo.git

      - name: Run script # Ejecuta el script
        run: |
          chmod +x ./.github/scripts/auto_commit.sh
          bash ./.github/scripts/auto_commit.sh
```

## Script de Shell

Aquí está el archivo del _script de shell_ completo:

```bash
# .github/scripts/auto_commit.sh
#!/bin/sh

# Check if the file exists, if not, create it
if [ ! -f ./days/auto-commit.md ]; then
    echo "- $(date)  " > ./days/auto-commit.md
	# it create a new file with the current date and time as a list item. the space after the date creates a line break
	# the > operator creates a new file
else
    # Append (add) the current date and time to the existing content of the file as a new list item
    echo "- $(date)  " >> ./days/auto-commit.md
	# the >> operator appends the output to the end of the file
fi

# Add the new file to the staging area
git add ./days/auto-commit.md

# Make a commit with a message
git commit -m "Commit automatizado $(date)"

# Push the changes to GitHub
git push origin main
```

**`git commit -m "Happy coding! 🚀"`**

<!-- ACKNOWLEDGMENTS -->

## Acknowledgments 📚

Resources list that I find helpful and would like to give credit to.

- [Asignar permisos a los trabajos](https://docs.github.com/en/actions/using-jobs/assigning-permissions-to-jobs).
