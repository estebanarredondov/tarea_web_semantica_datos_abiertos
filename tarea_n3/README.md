# README

## Descripción
`Tarea_n3.ipynb` implementa un flujo de consulta sobre datos RDF/Turtle de rentas vitalicias usando `rdflib`, consultas SPARQL y Gemini para clasificar preguntas y redactar respuestas en español.

## Requisitos
- Python 3.10 o superior
- Google Colab recomendado
- Clave de API de Google AI Studio / Gemini
- Conexión a internet para descargar archivos `.ttl`

## Dependencias
El notebook instala y usa:

```bash
pip install rdflib pandas tabulate requests google-genai
```

## Archivos utilizados
El notebook descarga automáticamente estos recursos desde GitHub:

- `rentas_vitalicias_validos_30.ttl`
- `rentas_vitalicias_shacl.ttl`

Base de descarga:
- repositorio: `estebanarredondov/tarea_web_semantica_datos_abiertos`

## Ejecución en Google Colab

1. Abrir `Tarea_n3.ipynb` en Google Colab.
2. Ejecutar la celda de instalación de dependencias.
3. Ejecutar la celda que descarga los archivos `.ttl`.
4. Configurar el secreto `GOOGLE_API_KEY`.
5. Ejecutar el resto de las celdas en orden.

## Configuración del secreto en Google Colab

El notebook usa este acceso:

```python
from google.colab import userdata
api_key = userdata.get('GOOGLE_API_KEY')
```

Para configurarlo en Colab:

1. Abrir el panel lateral izquierdo.
2. Entrar a **Secrets**.
3. Crear un secreto nuevo con:
   - **Nombre:** `GOOGLE_API_KEY`
   - **Valor:** tu API key de Gemini
4. Guardar el secreto.
5. Asegurarse de que el notebook tenga permiso para leerlo.

## Flujo del notebook

1. Instala dependencias.
2. Descarga el esquema y los datos en formato Turtle.
3. Carga ambos archivos en un grafo RDF con `rdflib`.
4. Define consultas SPARQL para preguntas de negocio.
5. Ejecuta consultas de prueba y muestra resultados tabulados.
6. Inicializa el cliente de Gemini.
7. Clasifica la pregunta del usuario en una categoría.
8. Ejecuta la consulta SPARQL correspondiente.
9. Construye un contexto textual con los resultados.
10. Pide a Gemini una respuesta final basada solo en ese contexto.

## Categorías soportadas

- `promedio_tipo`
- `promedio_modalidad`
- `mejor_modalidad`
- `promedio_sexo`
- `comparacion_mercado`

## Preguntas soportadas

- ¿Cuál es el promedio de pensión por tipo?
- ¿Cuál es el promedio de pensión por modalidad?
- ¿Qué modalidad tiene mayores montos?
- ¿Cuál es el promedio de pensión por sexo?
- ¿La pensión X está sobre o bajo el promedio del mercado?

## Notas sobre `comparacion_mercado`

La consulta base usa un pensionado de ejemplo (`Cliente14`) como placeholder, pero en ejecución el pipeline reemplaza esa parte por un `BIND` con el valor numérico detectado en la pregunta del usuario.

## Variables principales

- `archivo_esquema`: `rentas_vitalicias_shacl.ttl`
- `archivo_datos`: `rentas_vitalicias_validos_30.ttl`
- `preguntas_trabajo`: diccionario con texto, query y etiqueta
- `client`: cliente Gemini inicializado con `google-genai`

## Funciones principales

- `ejecutar_query(graph, query)`: ejecuta una consulta SPARQL y devuelve un `DataFrame`
- `clasificar_pregunta(pregunta, model)`: clasifica la pregunta en una etiqueta
- `obtener_contexto(clave, df)`: transforma el resultado en contexto textual
- `responder(pregunta, contexto, model)`: genera la respuesta final con Gemini
- `pipeline(graph, pregunta, model)`: ejecuta el flujo completo

## Modelo utilizado en los ejemplos

```python
"gemini-2.5-flash"
```

## Ejemplos del notebook

El notebook incluye pruebas con preguntas como:

- `¿Qué modalidad tiene mayores montos?`
- `¿compara La pensión 9.10 está sobre o bajo el promedio del mercado?`
- `¿Cuál es el promedio de pensión por tipo?`
- `¿Cuál es el promedio de pensión por sexo?`

## Salida esperada

Cada ejecución del pipeline retorna:

- `error`
- `df`
- `contexto`
- `respuesta`

Y en las celdas de ejemplo se muestra:

- resultado estructurado (`DataFrame`)
- contexto enviado a Gemini
- respuesta generada
