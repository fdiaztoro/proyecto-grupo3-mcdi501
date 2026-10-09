# Grupo 3 — MCDI501

Predicción de riesgo de enfermedad coronaria a 10 años, utilizando el
dataset Framingham Heart Study.

## Integrantes

- Felipe Díaz Toro
- Pablo Ríos Passteni
- Guillermo Subiabre Chacón
- Ninoska Yévenes Hernández

Docente: Jean Paul Maidana

## Contexto y problema

Las enfermedades cardiovasculares son una de las principales causas de
muerte a nivel mundial, y buena parte del riesgo puede anticiparse a
partir de factores demográficos, conductuales y médicos conocidos
(edad, tabaquismo, hipertensión, colesterol, glucosa, entre otros). El
Framingham Heart Study es uno de los estudios longitudinales de
referencia en esta área, y su dataset permite abordar el problema como
una tarea de clasificación binaria: predecir si una persona desarrollará
enfermedad coronaria en los próximos 10 años (`TenYearCHD`).

### Pregunta de investigación

¿Es posible predecir, a partir de los factores demográficos, conductuales
y médicos registrados en el Framingham Heart Study, si una persona
desarrollará enfermedad coronaria en un plazo de 10 años?

## Datos

**Framingham Heart Study (Riesgo Cardiovascular)** — predicción de enfermedad coronaria a 10
años (`TenYearCHD`) a partir de factores demográficos, conductuales y médicos. Ver
[`data/README.md`](data/README.md) para el detalle y cómo obtener el dataset.

## Estructura del repositorio

```
proyecto-grupo3-mcdi501/
├── README.md
├── requirements.txt
├── .gitignore
├── .gitattributes                                        # filtro nbstripout para los .ipynb
├── .mailmap                                               # nombres canónicos para el historial de commits
│
├── data/
│   ├── README.md                                        # cómo obtener el dataset
│   └── raw/                                              # dataset original (ignorado por git)
│
├── plantillas/                                           # plantillas LaTeX del docente, sin tocar (una por evaluación)
│   ├── formativa-1-eda-inferencia/
│   │   ├── plantilla.tex
│   │   └── logo_unab.png
│   ├── sumativa-1-analisis-exploratorio-inferencial/
│   ├── formativa-2-modelamiento-predictivo/
│   ├── sumativa-2-validacion-simulacion-remuestreo/
│   └── sumativa-3-modelamiento-predictivo-integrado/
│
├── redaccion/                                            # informe en LaTeX en desarrollo (una copia editable por evaluación)
│   ├── formativa-1-eda-inferencia/
│   │   ├── informe.tex
│   │   └── logo_unab.png
│   ├── sumativa-1-analisis-exploratorio-inferencial/
│   ├── formativa-2-modelamiento-predictivo/
│   ├── sumativa-2-validacion-simulacion-remuestreo/
│   └── sumativa-3-modelamiento-predictivo-integrado/
│
├── informes/                                             # solo lo terminado: la entrega de cada evaluación
│   ├── formativa-1-eda-inferencia/
│   │   ├── Formativa1_FraminghamHeartStudy_Codigo.ipynb  # código
│   │   └── Formativa1_FraminghamHeartStudy.pdf           # entregable final (compilado desde redaccion/)
│   ├── sumativa-1-analisis-exploratorio-inferencial/
│   ├── formativa-2-modelamiento-predictivo/
│   ├── sumativa-2-validacion-simulacion-remuestreo/
│   └── sumativa-3-modelamiento-predictivo-integrado/
```

**Flujo de trabajo para escribir un informe, en tres carpetas:**

1. **`plantillas/`** — copia local, intacta, de las plantillas del docente
   ([jpmaidana/MCDI501-202682](https://github.com/jpmaidana/MCDI501-202682/tree/main/04-plantillas/latex)).
   Cada carpeta es autocontenida (trae su propio `logo_unab.png`), igual
   que en el repo original. Nunca se edita acá. Si el docente actualiza
   una plantilla, hay que volver a copiarla manualmente.
2. **`redaccion/`** — se copia `plantillas/<evaluación>/plantilla.tex` y
   `logo_unab.png` acá, renombrando el `.tex` a `informe.tex`. Es donde
   se completa el contenido real (portada, secciones) y se compila
   (Overleaf o `pdflatex`, ver [`plantillas/README.md`](plantillas/README.md)).
   Los archivos que genera la compilación (`.aux`, `.log`, `.toc`, el
   `informe.pdf` de prueba) están en `.gitignore`: son desechables y se
   regeneran recompilando.

   Si el `informe.tex` incluye figuras (`\includegraphics{figuras/...}`),
   el notebook de `informes/<evaluación>/` las guarda **directo** en
   `redaccion/<evaluación>/figuras/` al correrlo (no hay una copia
   intermedia en `informes/`, para que no existan dos versiones que se
   puedan desincronizar). Esa carpeta **sí se sube a git** (igual que
   `logo_unab.png`), así cualquiera puede clonar el repo y compilar el
   informe directo, sin instalar Python ni correr el notebook primero. Si
   alguien cambia el notebook y las figuras cambian, hay que correrlo de
   nuevo y commitear la carpeta `figuras/` actualizada.
3. **`informes/`** — una vez compilado y revisado, se copia el PDF final
   acá (junto al notebook de esa evaluación), con el nombre definitivo
   del entregable. Esta carpeta queda siempre limpia: solo lo terminado
   y lo que se sube a Canvas.

## Requisitos y ejecución

Python 3.13 o superior

```bash
# 1. Clonar repositorio e ingresar a la carpeta
git clone https://github.com/fdiaztoro/proyecto-grupo3-mcdi501.git
cd proyecto-grupo3-mcdi501

# 2. Crear y activar entorno virtual
python3 -m venv .venv
source .venv/bin/activate        # macOS y Linux
# .venv\Scripts\activate         # Windows

# 3. Instalar dependencias del proyecto
python -m pip install --upgrade pip
python -m pip install -r requirements.txt

# 4. Activar la higiene automática de notebooks en el repositorio local
# nbstripout borra las salidas (outputs) de las celdas antes de cada commit
nbstripout --install
# - extrakeys: quita metadata ruidosa que varía según el entorno de cada
#   integrante (versión de Python, metadata de Colab, etc.).
# - --keep-id: sin esto, nbstripout reasigna el `id` de TODAS las celdas en
#   cada commit (a secuenciales 0,1,2...), generando diffs de metadata sin
#   cambios reales cada vez que alguien del equipo commitea el notebook.
git config filter.nbstripout.extrakeys "metadata.language_info.version metadata.colab cell.metadata.id cell.metadata.colab cell.metadata.outputId" \
  && git config filter.nbstripout.clean "$(git config filter.nbstripout.clean) --keep-id"

# 5. Registrar el kernel del proyecto en Jupyter
python -m ipykernel install --user --name grupo3_mcdi501 --display-name "Python (grupo3-mcdi501)"
```

### LaTeX (para compilar los informes)

No hace falta instalar nada local si usan **Overleaf** (ver
[`plantillas/README.md`](plantillas/README.md)). Para compilar localmente
se necesita una **distribución LaTeX** (el motor que compila). La extensión
*LaTeX Workshop* de VS Code es solo la interfaz: sin una distribución
instalada falla con `spawn latexmk ENOENT`.

#### macOS

La opción liviana es **BasicTeX** (instalador oficial, no compila
nada desde código fuente — evitar `brew install tectonic`, que puede
arrastrar una compilación de LLVM de 30-60+ minutos):

```bash
brew install --cask basictex
eval "$(/usr/libexec/path_helper)"   # o abrir una terminal nueva

# Paquetes que usan las plantillas y no vienen en BasicTeX por defecto:
sudo tlmgr update --self
sudo tlmgr install enumitem tcolorbox titlesec trimspaces environ \
  tikzfill pdfcol pdftexcmds ifplatform listingsutf8 accsupp \
  attachfile2 epstopdf-pkg

# Compilar (dos pasadas, para que el índice salga completo):
cd redaccion/<evaluación>
pdflatex informe.tex
pdflatex informe.tex
```

#### Windows

La opción equivalente es **MiKTeX** (~1 GB, se instala solo para el
usuario, sin permisos de administrador). A diferencia de BasicTeX, descarga
por su cuenta los paquetes que falten (`tcolorbox`, `titlesec`, etc.) la
primera vez que se compila, así que no hay que instalarlos a mano:

```powershell
winget install --id MiKTeX.MiKTeX --exact --scope user

# Abrir una terminal NUEVA (para que tome el PATH) y luego:
initexmf --set-config-value "[MPM]AutoInstall=1"   # instala paquetes faltantes sin preguntar
miktex packages update-package-database
miktex packages update

# Compilar (dos pasadas, para que el índice salga completo):
cd redaccion\<evaluación>
pdflatex informe.tex
pdflatex informe.tex
```

Después de instalar MiKTeX hay que **cerrar y volver a abrir VS Code por
completo** para que encuentre `pdflatex`.

**LaTeX Workshop en Windows:** su receta por defecto usa `latexmk`, que en
MiKTeX requiere tener Perl instalado. Para evitarlo, configurarlo para que
compile con `pdflatex` dos veces (igual que arriba) y que no compile solo
al abrir o guardar (así nunca genera archivos dentro de `plantillas/`). En
`.vscode/settings.json` (es local de cada uno, está en `.gitignore`):

```jsonc
{
    "latex-workshop.latex.autoBuild.run": "never",
    "latex-workshop.latex.tools": [
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": ["-synctex=1", "-interaction=nonstopmode", "-file-line-error", "%DOC%"]
        }
    ],
    "latex-workshop.latex.recipes": [
        { "name": "pdflatex x2", "tools": ["pdflatex", "pdflatex"] }
    ]
}
```

Se compila con `Ctrl+Alt+B` y el PDF se abre con `Ctrl+Alt+V`.

## Convención de commits

El equipo utiliza prefijos estandarizados para registrar cada avance en Git.
Los mensajes deben ser breves, descriptivos y redactados en tiempo presente.

Prefijos usados: `docs`, `data`, `feat`, `fix`, `refactor`, `chore`.
* `feat:` Nueva funcionalidad, módulo o notebook analítico.
* `fix:` Corrección de un error en código, rutas o cuadernos.
* `data:` Incorporación, filtrado o transformación de datos en `data/`.
* `docs:` Cambios en la documentación, README u observaciones del informe.
* `refactor:` Reorganización o optimización de código sin alterar sus resultados.
* `chore:` Tareas de mantenimiento de la estructura o del entorno.
