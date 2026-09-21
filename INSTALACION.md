# Guía de instalación del entorno de trabajo

**Módulo:** Depuración, Limpieza y Clasificación de Datos (5109)
**Curso:** Especialización en Aprendizaje Automático: gestión de datos y entrenamiento · 2026-2027

Durante el curso trabajarás con **cuadernos Jupyter** (`.ipynb`) guardados en el repositorio
[**DLCD**](https://github.com/alberto-dealarcon-pro/DLCD) de GitHub.
Esta guía te deja el ordenador preparado para abrirlos y ejecutarlos. Solo tienes que hacerla **una vez** por ordenador.

Vas a instalar, **en este orden**:

| Paso | Herramienta | Para qué sirve |
|:---:|---|---|
| 1 | **Git** | Descargar el repositorio y recibir los materiales nuevos |
| 2 | **Visual Studio Code** + extensiones Python y Jupyter | Abrir, editar y ejecutar los cuadernos |
| 3 | **uv** | Instalar Python y las librerías del curso dentro del repositorio |
| 4 | Clonar el repositorio **DLCD** | Tener los materiales en tu ordenador |
| 5 | `uv sync` | Crear el entorno `.venv` con todas las librerías |
| 6 | Elegir el kernel y ejecutar `00_comprobacion_entorno.ipynb` | Comprobar que todo funciona |

> **No necesitas instalar Python ni Anaconda.** `uv` descarga la versión de Python correcta (3.12) y crea el entorno
> dentro del proyecto. Si ya tienes otro Python instalado, **no hay conflicto**: cada uno va por su lado
> (lee el apartado [Si ya tienes Python o Anaconda](#si-ya-tienes-python-o-anaconda)).

**Requisitos:** Windows 10/11 (hay instrucciones para Linux y macOS al final), unos 3 GB libres y conexión a Internet.
No hacen falta permisos de administrador.

---

## Cómo abrir una terminal

Varios pasos se hacen escribiendo comandos. En Windows:

1. Pulsa la tecla **Windows**, escribe `PowerShell` y pulsa **Intro**.
2. Escribe (o pega con clic derecho) el comando y pulsa **Intro**.

> Cuando instales algo nuevo, **cierra la terminal y abre otra**, para que reconozca los comandos nuevos.

---

## Paso 1 · Instalar Git

1. Descarga el instalador desde <https://git-scm.com/download/win> (*64-bit Git for Windows Setup*).
2. Ejecútalo y pulsa **Next** en todas las pantallas: las opciones por defecto sirven.
3. Abre una terminal nueva y comprueba la instalación:

   ```powershell
   git --version
   ```

   Debe aparecer algo como `git version 2.x.x`.

4. Dile a Git quién eres (tu nombre y tu correo):

   ```powershell
   git config --global user.name "Nombre Apellido"
   git config --global user.email "tu_correo@ejemplo.com"
   ```

> Alternativa rápida con `winget` (incluido en Windows 10/11): `winget install --id Git.Git -e`

---

## Paso 2 · Instalar Visual Studio Code y sus extensiones

1. Descarga VS Code desde <https://code.visualstudio.com/> e instálalo.
   Durante la instalación, marca **"Agregar a PATH"** y **"Agregar la acción 'Abrir con Code'"**.
2. Abre VS Code y ve a la vista de **Extensiones** (`Ctrl + Mayús + X`).
3. Busca e instala estas dos extensiones de Microsoft:
   - **Python** (`ms-python.python`)
   - **Jupyter** (`ms-toolsai.jupyter`)

> Si quieres la interfaz en español, instala también *Spanish Language Pack for Visual Studio Code* y reinicia VS Code.
> Además, al abrir el repositorio (paso 6) VS Code te propondrá instalar las extensiones recomendadas si te falta alguna.

---

## Paso 3 · Instalar uv

`uv` es el gestor que instalará Python y todas las librerías del curso.

1. En una terminal PowerShell, ejecuta:

   ```powershell
   powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
   ```

2. **Cierra la terminal y abre otra nueva.** Comprueba la instalación:

   ```powershell
   uv --version
   ```

   Debe aparecer algo como `uv 0.x.x`.

> Alternativa con `winget`: `winget install --id astral-sh.uv -e`

---

## Paso 4 · Clonar el repositorio DLCD

*Clonar* es descargar el repositorio de GitHub a tu ordenador, conectado con el original para recibir las
actualizaciones.

1. Elige una carpeta para tus repositorios, por ejemplo `C:\Users\<tu_usuario>\Documents\GitHub` (créala si no existe).

   > **Evita carpetas sincronizadas con OneDrive o Google Drive.** El entorno `.venv` tiene miles de ficheros y la
   > sincronización lo ralentiza o lo rompe. Si tu carpeta *Documentos* está en OneDrive, usa `C:\Users\<tu_usuario>\GitHub`.

2. En la terminal, entra en esa carpeta y clona el repositorio:

   ```powershell
   cd C:\Users\<tu_usuario>\Documents\GitHub
   git clone https://github.com/alberto-dealarcon-pro/DLCD.git
   cd DLCD
   ```

---

## Paso 5 · Crear el entorno con `uv sync`

Dentro de la carpeta `DLCD`, ejecuta:

```powershell
uv sync
```

La primera vez tarda unos minutos. Este comando:

- descarga **Python 3.12** (la versión indicada en `.python-version`), si no lo tienes;
- crea la carpeta **`.venv`** dentro de `DLCD` (tu entorno virtual);
- instala las librerías del curso **con las versiones exactas** fijadas en `uv.lock`,
  de modo que toda la clase tiene el mismo entorno.

Librerías que se instalan:

| Para qué | Librerías |
|---|---|
| Cuadernos en VS Code | `ipykernel`, `ipywidgets` |
| Manipulación y carga de datos | `numpy`, `pandas`, `pyarrow`, `openpyxl` (Excel), `lxml` (XML) |
| Repositorios de datos | `datasets` (Hugging Face), `kagglehub` (Kaggle) |
| Visualización y perfilado | `matplotlib`, `seaborn`, `missingno`, `ydata-profiling` |
| Estadística (UD2) | `scipy`, `statsmodels`, `pingouin` |
| Limpieza y clasificación (UD3) | `scikit-learn`, `imbalanced-learn` |

---

## Paso 6 · Abrir el proyecto y comprobar que todo funciona

1. Abre la carpeta en VS Code. Desde la terminal, dentro de `DLCD`:

   ```powershell
   code .
   ```

   (O en VS Code: **Archivo → Abrir carpeta…** y selecciona `DLCD`.)
   Si VS Code pregunta si confías en los autores de la carpeta, pulsa **Sí, confío en los autores**.

2. Abre el cuaderno **`00_comprobacion_entorno.ipynb`**.

3. Arriba a la derecha pulsa **Select Kernel** (*Seleccionar kernel*) →
   **Python Environments** → **`.venv (Python 3.12.x)`**.

   > Si algún cuaderno te pide kernel, elige siempre **`.venv`**.

4. Pulsa **Run All** (*Ejecutar todo*). Debes ver:
   - que el intérprete está en `DLCD\.venv\...`;
   - todas las librerías con **OK**;
   - una tabla y un gráfico de pingüinos.

**Si ves el gráfico, tu entorno está listo.**

---

## Trabajo del día a día

**Cada vez que empieces a trabajar**, trae los materiales nuevos. En la terminal de VS Code
(**Terminal → Nuevo terminal**):

```powershell
git pull
uv sync
```

- `git pull` descarga los cuadernos y datos nuevos.
- `uv sync` actualiza las librerías si ha cambiado alguna (si no, termina al instante).

**Dónde hacer tus ejercicios:** antes de modificar un cuaderno, **cópialo a la carpeta `mis_cuadernos/`** y
trabaja sobre la copia. Esa carpeta no se sube a GitHub y `git pull` nunca la toca, así que evitarás conflictos
al actualizar.

> Si `git pull` se queja de que has modificado un cuaderno del repositorio, puedes descartar tus cambios en ese fichero con
> `git restore "ruta\del\cuaderno.ipynb"` (¡pierdes esos cambios! Por eso conviene trabajar en `mis_cuadernos/`).

**Celdas que instalan librerías:** algunos cuadernos traen una celda del tipo *"Instalamos la librería si no está
disponible"*. Puedes ejecutarla sin miedo: como la librería ya está en `.venv`, simplemente comprobará que está instalada.

---

## Si ya tienes Python o Anaconda

No hace falta desinstalar nada. `uv` usa su propio Python dentro de `.venv`, así que no interfiere con otras
instalaciones. Solo ten en cuenta:

- En VS Code, elige siempre el kernel **`.venv`**, no `base (Anaconda)` ni otro Python del sistema.
- **No instales librerías del curso por tu cuenta** con `pip install` o `conda install`. Si una práctica necesita una
  librería nueva, se añadirá al proyecto y te llegará con `git pull` + `uv sync`
  (además, `uv sync` elimina de `.venv` lo que no forme parte del proyecto).
- Para saber qué Python ejecuta un cuaderno, ejecuta en una celda: `import sys; print(sys.executable)`.

---

## Plan B · Google Colab

Si no puedes instalar nada (ordenador ajeno, equipo muy limitado…), puedes abrir los cuadernos en
**Google Colab** con tu cuenta de Google:

1. Entra en <https://colab.research.google.com> → pestaña **GitHub**.
2. Escribe `alberto-dealarcon-pro/DLCD` y elige el cuaderno.
3. Colab ya trae casi todas las librerías. Si falta alguna, ejecuta en la primera celda:

   ```python
   !pip install missingno ydata-profiling pingouin imbalanced-learn
   ```

Limitaciones: los cambios no se guardan en el repositorio (usa **Archivo → Guardar una copia en Drive**), las versiones de
las librerías pueden no coincidir con las del curso y los ficheros de datos locales hay que subirlos a la sesión.

---

## Solución de problemas

| Problema | Solución |
|---|---|
| `git`, `uv` o `code` *"no se reconoce como nombre de un cmdlet…"* | Cierra **todas** las terminales (y VS Code) y abre una nueva. Si sigue, reinicia el ordenador. |
| El script de instalación de `uv` da error de *directiva de ejecución* | Usa la alternativa `winget install --id astral-sh.uv -e`. |
| `uv sync` no puede descargar Python (red del centro, proxy…) | Instala **Python 3.12** desde <https://www.python.org/downloads/> y vuelve a ejecutar `uv sync`: lo detectará. |
| En *Select Kernel* no aparece `.venv` | Comprueba que abriste la carpeta **`DLCD`** (no una superior). Pulsa `Ctrl + Mayús + P` → **Python: Select Interpreter** → `.venv`. Si no está, ejecuta `uv sync` y recarga la ventana (`Ctrl + Mayús + P` → **Developer: Reload Window**). |
| `ModuleNotFoundError: No module named '...'` | Estás en otro kernel. Cambia a `.venv`. Si ya lo estás, ejecuta `uv sync`. |
| VS Code pide instalar `ipykernel` | No lo instales desde el aviso: significa que el kernel no es `.venv`. Cámbialo. |
| El entorno se ha estropeado | Cierra VS Code, borra la carpeta `.venv` dentro de `DLCD` y ejecuta `uv sync`. Se vuelve a crear en unos minutos. |
| `git pull` da conflicto con un cuaderno | Ver [Trabajo del día a día](#trabajo-del-día-a-día). |

---

## Anexo · Linux y macOS

Los pasos son los mismos; solo cambian las instalaciones:

```bash
# Git — Linux (Debian/Ubuntu)
sudo apt install git
# Git — macOS (instala las herramientas de desarrollo de Apple)
xcode-select --install

# uv (Linux y macOS)
curl -LsSf https://astral.sh/uv/install.sh | sh
```

VS Code se descarga desde <https://code.visualstudio.com/>. Después: `git clone …`, `cd DLCD`, `uv sync` y `code .`.
El intérprete del entorno estará en `DLCD/.venv/bin/python`.
