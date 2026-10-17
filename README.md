# ConnectaTel: análisis del uso de servicios móviles

Proyecto de análisis exploratorio realizado en el curso de Análisis de Datos de TripleTen. Se estudian los clientes de ConnectaTel, una empresa de telecomunicaciones con operaciones en México y Colombia, y sus registros de llamadas y mensajes hasta 2024.

## Objetivo

Identificar patrones de uso, revisar la calidad de los datos, detectar valores atípicos y crear segmentos de clientes que ayuden a orientar decisiones comerciales.

## Archivos del proyecto

| Archivo | Contenido |
| --- | --- |
| `S7 Version-Estudiante-Project-ConnectaTel.ipynb` | Notebook con código, resultados, gráficas y análisis ejecutivo. |
| `README.md` | Descripción e instrucciones para reproducir el análisis. |

## Datos utilizados

Los tres CSV se proporcionan en la plataforma del curso:

- `plans.csv`: catálogo de planes, precios y beneficios; 2 filas y 8 columnas.
- `users_latam.csv`: información de clientes, edades, ciudades, registro, plan y cancelación; 4,000 filas y 8 columnas.
- `usage.csv`: registros de llamadas y mensajes; 40,000 filas y 6 columnas.

Los CSV no están incluidos en esta entrega. Para ejecutar el notebook es necesario obtenerlos desde el curso. Los datos de consumo se resumen sobre los registros disponibles; no se interpretan como consumos mensuales.

## Herramientas

Python, pandas, seaborn y matplotlib, en un entorno Jupyter Notebook o Google Colab.

## Etapas del análisis

1. Carga y exploración de los tres datasets.
2. Revisión de nulos, tipos, categorías y valores inconsistentes.
3. Limpieza de edades, ciudades y fechas fuera del periodo del proyecto.
4. Agregación de mensajes, llamadas y minutos por usuario y combinación con clientes.
5. Estadísticas descriptivas, distribución de planes e histogramas.
6. Detección de valores atípicos con boxplots y límites IQR.
7. Segmentación por nivel de uso y edad, con gráficas de conteo.
8. Conclusiones y recomendaciones comerciales.

## Cómo ejecutar el notebook

### En la plataforma del curso

1. Abre el notebook en Jupyter.
2. Comprueba que los archivos estén en `/datasets/plans.csv`, `/datasets/users_latam.csv` y `/datasets/usage.csv`.
3. Reinicia el kernel y ejecuta todas las celdas desde el inicio, en orden.

### En Google Colab

1. Abre https://colab.research.google.com/ y selecciona **Archivo > Abrir notebook**.
2. En la pestaña **GitHub**, pega la dirección del repositorio y selecciona el notebook. También puedes usar **Subir** para abrir la copia descargada.
3. Sube los tres CSV desde el panel **Archivos** de Colab.
4. Ajusta únicamente las rutas de la celda `# cargar archivos` a `/content/plans.csv`, `/content/users_latam.csv` y `/content/usage.csv`.
5. Ejecuta todas las celdas desde el principio. Los archivos subidos deben cargarse nuevamente si se elimina la sesión de Colab.

## Decisiones y límites del análisis

- Las edades con sentinel `-999` se reemplazan por la mediana de las edades distintas de ese código: 48 años en la ejecución guardada.
- Las ciudades con `?` se convierten en nulos. No se inventan ubicaciones.
- Las 40 fechas de registro de 2026 están fuera del corte de 2024 y se marcan como `NaT`.
- Los campos que no corresponden al tipo de actividad se conservan como nulos; los minutos se suman únicamente para llamadas.
- Un usuario sin coincidencia en la tabla de actividad permanece sin clasificación de uso.
- Los valores atípicos se conservan para revisión; no se consideran fraude automáticamente.
- La agrupación por edad no prueba diferencias de consumo entre edades. Tampoco se estima rentabilidad ni se evalúan causalmente la cancelación o la satisfacción.

## Hallazgos principales

- Basico representa el 64.875 % de los clientes y Premium el 35.125 %.
- Entre los 3,999 usuarios con información de uso, las medianas son 5 mensajes, 4 llamadas y 19.74 minutos acumulados.
- Los límites superiores IQR son 11.5 mensajes, 10.5 llamadas y aproximadamente 61.32 minutos.
- Predomina el segmento de uso medio; en la segmentación por edad, el grupo Adulto es el más numeroso.

Para reproducir los resultados, utiliza los mismos CSV y ejecuta el notebook desde un kernel reiniciado. Los cambios en los datos o en las versiones de las librerías pueden alterar los resultados o la presentación.
