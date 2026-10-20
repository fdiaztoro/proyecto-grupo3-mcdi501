# Datos

## Framingham Heart Study (Riesgo Cardiovascular)

- **Tipo:** Clasificación binaria.
- **Variable a predecir:** `TenYearCHD` — ¿desarrollará enfermedad coronaria en 10 años? (Sí/No).
- **Descripción:** datos del estudio cardiovascular longitudinal de la ciudad de Framingham
  (Massachusetts), con más de 4.000 registros y unos 15 atributos. El objetivo es predecir el
  riesgo de enfermedad coronaria a 10 años a partir de factores demográficos, conductuales y
  médicos.
- **Variables:** sexo, edad, nivel educativo, tabaquismo (fumador actual y cigarrillos por día),
  uso de antihipertensivos, antecedentes de ACV, hipertensión y diabetes, colesterol total,
  presión arterial sistólica y diastólica, índice de masa corporal, frecuencia cardíaca y
  glucosa.
- **Aplicaciones prácticas:** prevención cardiovascular, estratificación de riesgo de pacientes,
  salud pública, diseño de intervenciones y campañas de prevención.
- **Fuente:** <https://www.kaggle.com/datasets/dileep070/heart-disease-prediction-using-logistic-regression>
- **Desafíos:** datos faltantes en varias variables numéricas (glucosa, colesterol, IMC,
  frecuencia cardíaca, cigarrillos por día); clases desbalanceadas (pocos casos positivos de
  enfermedad coronaria).

## Copia versionada del dataset

`data/raw/framingham.csv` **se versiona en el repositorio**: es la copia exacta con la que se
calcularon todos los resultados de la Formativa 1 y de las Sumativas 1 y 2. Kaggle puede
entregar versiones distintas del mismo dataset (circulan copias con 4.240 filas en vez de
4.238), y una descarga nueva podría no reproducir las cifras de los informes. No hay que
descargar nada: el archivo llega con `git clone` o `git pull`.

| Dato | Valor |
|---|---|
| Fuente | Kaggle, `dileep070/heart-disease-prediction-using-logistic-regression` |
| Título en Kaggle | *Logistic regression To predict heart disease* (autor: Dileep) |
| Versión | 1, publicada el 07/06/2019 |
| Licencia declarada en Kaggle | No especificada ("Unknown"); se usa con fines académicos y citando la fuente |
| Filas × columnas | 4.238 × 16 (15 predictores y `TenYearCHD`) |
| SHA-256 | `40921748dbdf6587045b9822414199a1ae3349358b63b975ab2208aa3cccc45b` |

El archivo usa finales de línea de Windows (CRLF). `.gitattributes` lo marca como `-text` para
que git lo guarde byte a byte y la huella sea la misma en Windows, macOS y Linux.

### Verificar la copia

Los notebooks comprueban la huella y la forma antes de analizar, y se detienen si no
coinciden. Para verificarla a mano:

```bash
sha256sum data/raw/framingham.csv        # Linux o Git Bash
shasum -a 256 data/raw/framingham.csv    # macOS
```

```powershell
Get-FileHash data\raw\framingham.csv -Algorithm SHA256   # Windows PowerShell
```

Si la huella no coincide, restaure la copia del repositorio con
`git checkout -- data/raw/framingham.csv`.

### Si el archivo falta

Los notebooks lo descargan de Kaggle con [`kagglehub`](https://pypi.org/project/kagglehub/),
fijando la versión 1 del dataset (no requiere cuenta), y luego verifican la huella.

## Estructura

```
data/
├── README.md          # este archivo
└── raw/
    └── framingham.csv # copia versionada del dataset (SHA-256 arriba)
```
