# Revisión de la Sumativa 1 según la pauta de Fase 2

## Correcciones consolidadas

- Introducción: problema, datos y objetivo de esta fase; atención primaria como contexto de aplicación propuesto.
- Calidad: diccionario de variables y unidades, validación de educación, conteos negativos y mediciones no positivas; reporte de faltantes y decisiones por variable.
- Categóricas: frecuencias absolutas y relativas para cada categoría, denominadores válidos y faltantes; educación y objetivo incluidos. Barras completas en el notebook y versión compacta para el informe.
- Numéricas: cuartiles y rango intercuartílico; distribuciones completas de las ocho variables. El colesterol se grafica sin `clip`, que acumulaba extremos en P99.
- Bivariado: selección explícita de columnas originales para poder repetir correlaciones después de crear categorías. Los tramos de presión son descriptivos, no diagnósticos.
- Estimación: IC del 95 % con t de Student para tres medias y Wilson para CHD; Wald se conserva como comparación. Se documentan independencia, representatividad y sesgo potencial por faltantes.
- Hipótesis: justificación de α sin afirmar que equilibra errores I/II; χ² con Yates y V de Cramér sin corrección, explicitados. IC individuales de RR/OR y diferencia de riesgos; Holm para las tres hipótesis sustantivas.
- Interpretación: no rechazar independencia entre faltantes y CHD no demuestra ausencia aleatoria. Los efectos son asociaciones crudas; comparar promedios no descarta confusión ni demuestra una señal independiente del sexo.
- Reproducibilidad: reutilización de CSV local, búsqueda de raíz del repositorio, SHA-256 y versiones. Carga sin avisos de tqdm ni impresión de la ruta absoluta; tablas con visualización HTML.
- Entrega: notebook ejecutado y PDF para Canvas en `informes/sumativa-1-analisis-exploratorio-inferencial/`; una excepción específica de `nbstripout` en `.gitattributes` conserva todas las salidas del notebook. Informe con resultados y figuras actualizados.

## Datos y validación

Dataset analizado: 4.238 filas y 16 columnas.

SHA-256 de `data/raw/framingham.csv`:
`40921748dbdf6587045b9822414199a1ae3349358b63b975ab2208aa3cccc45b`

El notebook se ejecutó desde un kernel limpio con las dependencias de `requirements.txt`: 24 celdas de código, sin errores ni avisos en sus salidas finales. Los IC de las tres medias mantienen los valores redondeados del informe; Wilson para CHD es [14,15 %; 16,31 %]. Holm mantiene el rechazo de las tres hipótesis nulas sustantivas. Estos resultados no prueban causalidad ni representatividad de otras poblaciones.

Validación local completada: Python 3.14.7, las versiones fijadas en `requirements.txt`, código y resultados de la copia ejecutada conservados en el notebook del repositorio, 14 celdas con tablas HTML y carga inicial verificada usando una carpeta temporal. PDF compilado con Tectonic y revisado visualmente en sus ocho páginas, incluida portada; sin referencias sin resolver ni desbordamientos reportados por LaTeX. El PDF definitivo y el notebook ejecutado se conservan juntos en `informes/sumativa-1-analisis-exploratorio-inferencial/`, sin duplicar entregables en otra carpeta.

## Regenerar los entregables para Canvas

Desde la raíz del repositorio, con el entorno del proyecto y su kernel registrados:

```powershell
python -m nbconvert --to notebook --execute --ExecutePreprocessor.timeout=300 --inplace informes/sumativa-1-analisis-exploratorio-inferencial/Sumativa1_FraminghamHeartStudy_Codigo.ipynb
```

Compilar `redaccion/sumativa-1-analisis-exploratorio-inferencial/informe.tex` después de ejecutar el notebook. Revisar visualmente el PDF y confirmar máximo ocho páginas, contando la portada. Copiar el PDF aprobado junto al notebook ejecutado en `informes/sumativa-1-analisis-exploratorio-inferencial/`. Ambos archivos se versionan. `.gitattributes` desactiva `nbstripout` solo para este notebook, de modo que conserva las salidas al subirlo a GitHub; la configuración de los demás notebooks no cambia.

La primera carga necesita internet si no hay CSV local. La huella permite detectar cambios del archivo; la descarga de Kaggle no fija por sí misma una versión inmutable del dataset.
