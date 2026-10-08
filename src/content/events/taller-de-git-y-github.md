---
title: Taller de Git y GitHub
date: 2026-10-07T18:00:00.000Z
description: Una introducción práctica a Git y GitHub para personas que recién se inician en el versionado de código.
location: Laboratorio de Informática 1, Facultad de Ingeniería UNI
time: "15:00 - 18:00"
presenters:
  - "Adán Alvarez"
tags:
  - guias
  - git
  - talleres
  - semestre-cero
mode: in-person
---

En este taller aprenderás los fundamentos del control de versiones con Git:

- ¿Qué es Git y por qué usarlo?
- Comandos básicos: `init`, `add`, `commit`, `push`, `pull`.
- Crear repos, clonarlos y modificarlos
- Trabajo colaborativo con ramas y _pull requests_ en GitHub.
- Cómo compartir tu código en GitHub y más

Traé tu notebook. Los cupos son limitados.

Inscribite acá: [Formulario de Inscripción](https://forms.gle/sdv28XXjKdG5vSx19)

---

## Guía de Referencia del Taller

El material técnico está basado en la Guía Oficial, [ProGit (inglés)](https://git-scm.com/book/en/v2).

Para la versión en español, podés consultar [ProGit en español](https://git-scm.com/book/es/v2).

Para más materiales de Git, podés visitar [librosgratis.dev](https://librosgratis.dev/#git)

![Portada del libro de progit](@/assets/images/progit.png)

### 1. Configuración Inicial (Local)

Luego de instalar Git en tu sistema operativo, el primer paso es presentarte. Abrí tu terminal (recomendamos **Git Bash** en Windows) y ejecutá:

```sh
git config --global user.name "Juan Pérez"
git config --global user.email "jperez@email.com"

```

### 2. Comandos Básicos

Para transformar una carpeta normal en un repositorio de Git:

```sh
git init

```

Luego de crear o modificar tus archivos, preparalos (Staging Area):

```sh
git add archivo.txt
# O para agregar todo de una vez:
git add .

```

Guardá una "foto" de esos cambios (Commit) con un mensaje claro:

```sh
git commit -m "Agrega la estructura inicial del proyecto"

```

### 3. Trabajando con Ramas (Branches)

Las ramas te permiten experimentar sin romper tu código principal.

Para crear una rama nueva y moverte a ella al mismo tiempo:

```sh
git switch -c nueva-rama

```

Para fusionar (merge) el trabajo de tu rama secundaria (`nueva-rama`) a la principal (`main`):

```sh
git switch main
git merge nueva-rama

```

### 4. Conectar con GitHub (La Nube)

Para subir tu código en una plataforma remota, configuramos una **Llave SSH**.

**Paso A: Generar la llave**
En tu terminal (Git Bash), ejecutá este comando usando el correo de tu cuenta de GitHub:

```sh
ssh-keygen -t ed25519 -C "jperez@email.com"

```

Esto genera dos archivos ocultos en tu carpeta `~/.ssh/`:

- `id_ed25519` (Tu llave privada, ¡NO la compartas!)
- `id_ed25519.pub` (Tu llave pública, esta va a GitHub).

**Paso B: Copiar la llave pública**
Para no abrir el archivo y copiar espacios por error, usá este comando para copiar el texto directamente a tu portapapeles:

En **Windows** (Git Bash):

```sh
cat ~/.ssh/id_ed25519.pub | clip

```

En **Linux / Mac**:

```sh
cat ~/.ssh/id_ed25519.pub
# Seleccioná y copiá el texto que aparece en pantalla.

```

**Paso C: Pegarla en GitHub**

1. Entrá a tu cuenta en [github.com](https://github.com/).
2. Andá a **Settings** > **SSH and GPG keys** > **New SSH key**.
3. Ponele un título (ej: "Notebook Facu") y pegá la llave.

![Captura de Pantalla de la interfaz de GitHub](@/assets/images/git-taller-shot.png)

![Captura de Pantalla de la interfaz de GitHub](@/assets/images/git-taller-shot-1.png)

**Paso D: La prueba de fuego**
Para comprobar que tu computadora se vinculó correctamente, ejecutá:

```sh
ssh -T git@github.com

```

_(Escribí `yes` si te pregunta si confías en el host y dale Enter)._

Debería devolverte un mensaje de éxito similar a este:

```
Hi jperez! You've successfully authenticated, but GitHub does not provide shell access.

```

Desde ahora podrás clonar repositorios o vincular tus repositorios locales usando la URL `SSH` que te da GitHub.

### 5. Sincronizar con GitHub (Remotos)

Una vez que tenés tu código listo en tu computadora y un repositorio vacío creado en GitHub, usá estos comandos genéricos para sincronizarlos usando tu conexión SSH.

**Vincular tu carpeta local con el repositorio de GitHub:**

```sh
git remote add origin git@github.com:USUARIO/TU-REPOSITORIO.git

```

_(Cambiá `USUARIO` por tu usuario de GitHub y `TU-REPOSITORIO` por el nombre de tu proyecto)._

**Subir tu código a la nube (Push):**
La primera vez que subas una rama, necesitás indicarle a Git a dónde va:

```sh
git push -u origin main

```

_(A partir de ese momento, para subir futuros cambios solo vas a necesitar escribir `git push`)._

**Bajar código de la nube (Pull):**
Si hiciste cambios desde otra computadora o un compañero modificó el proyecto, actualizá tu carpeta local ejecutando:

```sh
git pull origin main

```
