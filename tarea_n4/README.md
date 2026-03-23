Análisis de Rentas Vitalicias desde un POD de Solid
Este cuaderno de Google Colab (.ipynb) demuestra cómo consumir, analizar y visualizar datos de rentas vitalicias directamente desde un POD de Solid. También incluye una sección sobre análisis de privacidad para identificar riesgos de reidentificación.

Requisitos
Acceso a Google Colab (o un entorno Jupyter con Python 3).
Cómo ejecutar el cuaderno
Para ejecutar este cuaderno, sigue estos sencillos pasos:

Abrir en Google Colab
Ejecutar todas las celdas: Una vez abierto el cuaderno en Colab, ve al menú Entorno de ejecución (Runtime) y selecciona Ejecutar todas (Run all). Alternativamente, puedes ejecutar cada celda secuencialmente haciendo clic en el botón de "play" (▶) al lado de cada celda.

El cuaderno está estructurado en las siguientes secciones:

Instalación de librerías: Instala las dependencias necesarias (rdflib, pandas, matplotlib).
Carga de datos desde POD de Solid: Carga los datos RDF desde la URL del POD especificada.
Exploración y Extracción: Explora la estructura del grafo y extrae los datos a un DataFrame de Pandas.
Análisis Básico y SPARQL: Realiza análisis descriptivos y ejecuta consultas SPARQL sobre el grafo.
Visualización: Genera un gráfico de la distribución de las modalidades de pensión.
Análisis de Privacidad: Identifica y evalúa el riesgo de reidentificación en los datos.
Conclusión: Un resumen de lo aprendido y las implicaciones del uso de Solid.
Fuente de datos
Los datos se obtienen directamente de un POD de Solid público. La URL utilizada es: https://stbn2005.datapod.igrant.io/public/rentas_vitalicias_validos_30.ttl

Notas
El acceso a este POD es público para fines de demostración. En un escenario real, Solid permite un control de acceso granular.
El análisis de privacidad resalta que, si bien Solid mejora el control de acceso, las buenas prácticas de anonimización de datos siguen siendo cruciales.
