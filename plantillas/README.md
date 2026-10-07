# Plantillas MCDI501 — Estadística Computacional para la Toma de Decisiones

Plantillas en LaTeX para las evaluaciones formativas y sumativas del curso,
alineadas con los enunciados y rúbricas publicados en Canvas. Cada carpeta
corresponde a una evaluación y es **autocontenida**: trae su propio archivo
`.tex` y el logo institucional, sin depender de nada fuera de la carpeta.

Son una copia local de las plantillas del repositorio del docente
([jpmaidana/MCDI501-202682](https://github.com/jpmaidana/MCDI501-202682/tree/main/04-plantillas/latex)).
Si el docente actualiza una plantilla, hay que volver a copiarla
manualmente desde ahí.

## Estructura

```
plantillas/
├── formativa-1-eda-inferencia/
│   ├── plantilla.tex
│   └── logo_unab.png
├── sumativa-1-analisis-exploratorio-inferencial/
│   ├── plantilla.tex
│   └── logo_unab.png
├── sumativa-2-validacion-simulacion-remuestreo/
│   ├── plantilla.tex
│   └── logo_unab.png
├── formativa-2-modelamiento-predictivo/
│   ├── plantilla.tex
│   └── logo_unab.png
└── sumativa-3-modelamiento-predictivo-integrado/
    ├── plantilla.tex
    └── logo_unab.png
```

| Carpeta | Evaluación | Fase | Ponderación |
| --- | --- | --- | --- |
| `formativa-1-eda-inferencia` | Formativa 1 | Fase 2 | 0 % |
| `sumativa-1-analisis-exploratorio-inferencial` | Sumativa 1 | Fase 2 | 20 % |
| `sumativa-2-validacion-simulacion-remuestreo` | Sumativa 2 | Fase 3 | 20 % |
| `formativa-2-modelamiento-predictivo` | Formativa 2 | Fase 3 | 0 % |
| `sumativa-3-modelamiento-predictivo-integrado` | Sumativa 3 | Fase 4 | 60 % |

## Cómo usar una plantilla

No se edita el original aquí: se copia a `redaccion/<evaluación>/`,
renombrando `plantilla.tex` a `informe.tex`, y se completa y compila ahí
(ver el README principal del proyecto). El PDF final, ya revisado, se
copia a `informes/<evaluación>/` junto al notebook — esa carpeta es la
que queda solo con lo terminado.

### Opción A — Overleaf (recomendada, no requiere instalar nada)

1. Entra a [overleaf.com](https://www.overleaf.com) e inicia sesión.
2. Click en **New Project → Upload Project**.
3. Sube **los dos archivos de `redaccion/<evaluación>/`**: `informe.tex`
   y `logo_unab.png` (deben quedar juntos en el mismo proyecto).
4. Overleaf compila automáticamente. Si no, click en **Recompile**.
5. Completa los datos del grupo al inicio del documento (título del
   proyecto, integrantes, dataset, docente y fecha) y desarrolla cada
   sección donde dice `[Desarrollen aquí]`.
6. Descarga el PDF compilado y cópialo a `informes/<evaluación>/` con el
   nombre definitivo del entregable.

> Si subes solo el `.tex` sin el `.png`, la portada no va a compilar
> porque no encuentra el logo. Asegúrate de subir ambos archivos juntos.

### Opción B — Compilar localmente

Si tienes una distribución de LaTeX instalada (TeX Live, MiKTeX, MacTeX):

```bash
cd redaccion/<evaluación>
pdflatex informe.tex
pdflatex informe.tex   # segunda pasada: arma el índice correctamente
```

El PDF resultante (`informe.pdf`) queda en la misma carpeta — es un
archivo de trabajo (`.gitignore` lo excluye junto con `.aux`/`.log`/`.toc`).
Cuando esté listo, cópialo a `informes/<evaluación>/` con el nombre
definitivo del entregable.

## Requisitos técnicos

Las plantillas usan paquetes estándar, disponibles por defecto en Overleaf
y en cualquier distribución de TeX Live reciente:

`geometry`, `graphicx`, `xcolor`, `titlesec`, `fancyhdr`, `tcolorbox`,
`hyperref`, `booktabs`, `enumitem`, `array`.

No requieren `babel` para compilar (las etiquetas en español —Índice,
Figura, Tabla, Bibliografía— están definidas manualmente).

## Cómo está armada la plantilla

Cada `.tex` incluye, al inicio del archivo, dos comandos útiles para
entender su estructura:

- `\guia{...}` — descripción breve bajo cada título, con el puntaje de la
  rúbrica entre paréntesis.
- `\resp` — marca discreta `[Desarrollen aquí]` que indica dónde
  completar; se borra al entregar.

Los datos de portada (título del proyecto, integrantes, dataset, docente,
fecha, repositorio) se completan editando las líneas `\newcommand{\proy...}`
cerca del inicio del archivo.
