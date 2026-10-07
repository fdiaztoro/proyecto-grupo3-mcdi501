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

## Cómo obtener el dataset

Se descarga automático vía [`kagglehub`](https://pypi.org/project/kagglehub/) (no requiere
cuenta ni login de Kaggle para este dataset público): basta con correr la primera celda de
descarga del notebook
(`informes/formativa-1-eda-inferencia/Formativa1_FraminghamHeartStudy_Codigo.ipynb`), que deja
`framingham.csv` copiado en `data/raw/`. El archivo en `data/raw/` no se versiona en Git (ver
`.gitignore`); cada integrante lo obtiene corriendo esa celda la primera vez que trabaja en el
proyecto.

## Estructura

```
data/
├── README.md   # este archivo
└── raw/        # dataset original (ignorado por git)
```
