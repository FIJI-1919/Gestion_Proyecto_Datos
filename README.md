# Segmentación de clientes mayoristas

Proyecto académico de **Gestión de Proyectos de Datos (SCY1102)** para la Evaluación 3 (EP5 y EP6). El caso de estudio corresponde a **Distribuidora Alimentos del Pacífico S.A.**

El objetivo es agrupar clientes con patrones de compra similares para apoyar la planificación de despachos, la gestión de inventario y el diseño de promociones. El notebook entrena un modelo de segmentación y muestra cómo asignar nuevos clientes a los perfiles obtenidos.

## Datos y método

El proyecto usa el conjunto [Wholesale customers de UCI](https://doi.org/10.24432/C5030X) como referencia académica. Contiene **440 clientes** y seis variables de gasto anual en unidades monetarias: frescos, lácteos, abarrotes, congelados, detergentes y papel, y delicatessen. El canal comercial y la región se usan para describir los perfiles.

El notebook sigue las seis fases de **CRISP-DM**, desde la comprensión del negocio hasta la aplicación del modelo. Compara **20 configuraciones** de K-means y agrupamiento jerárquico de Ward con valores de `k` entre 2 y 6. En cada configuración aplica `log1p` y luego escalado estándar o robusto sobre las seis variables de gasto. El análisis de componentes principales (PCA) permite visualizar los grupos y sus centroides en dos dimensiones.

## Resultados

El modelo seleccionado fue **K-means con `StandardScaler` y `k = 2`**. Obtuvo un **Silhouette de 0,290** y un **ARI mediano de 0,966** en diez remuestreos.

| Perfil | Clientes | Categorías en las que destaca |
| --- | ---: | --- |
| Perfil 1 | 252 (57,3 %) | Frescos y congelados |
| Perfil 2 | 188 (42,7 %) | Abarrotes, lácteos y detergentes y papel |

La Fase 6 aplica el pipeline entrenado a **cuatro clientes ficticios** y muestra su asignación de perfil: A y D en el Perfil 1, B y C en el Perfil 2. Las recomendaciones de despacho, inventario y promociones quedan sujetas a validación con datos operativos de la distribuidora.

## Archivos del proyecto

| Archivo | Contenido |
| --- | --- |
| [Segmentacion_Clientes_Mayoristas_EP5_EP6(1).ipynb](Segmentacion_Clientes_Mayoristas_EP5_EP6%281%29.ipynb) | Notebook final con análisis, entrenamiento, evaluación y demostración. |
| [Wholesale customers data.csv](Wholesale%20customers%20data.csv) | Datos utilizados por el notebook. |
| [Informe_EP5_Segmentacion_Mayoristas.docx](Informe_EP5_Segmentacion_Mayoristas.docx) | Informe de implementación y seguimiento, con evidencia del tablero de Trello. |
| [Tareas_Trello_EP5.txt](Tareas_Trello_EP5.txt) | Ocho tarjetas basadas en las tareas de la Carta Gantt de la Evaluación 2. |

## Cómo ejecutar el notebook

1. Descarga o clona el repositorio. Mantén el notebook y el CSV en la carpeta desde la que iniciarás JupyterLab, con el nombre exacto `Wholesale customers data.csv`.
2. Con Python 3 instalado, ejecuta estos comandos desde esa carpeta:

   ```bash
   python -m pip install jupyterlab numpy pandas scikit-learn matplotlib
   python -m jupyterlab
   ```

3. Abre el notebook y ejecuta todas las celdas en orden. Al final de la Fase 6 verás la tabla de asignación de los cuatro clientes ficticios.

Si usas **Google Colab**, importa el notebook, sube el CSV al entorno de ejecución y corre todas las celdas.

## Integrantes

**Equipo 3** · Vicente Tapia y Adriano Contreras
