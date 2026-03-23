# README

## Estructura del proyecto

El repositorio está organizado para trabajar con datos abiertos y su transformación hacia formatos de web semántica. La estructura es la siguiente:

### 📁 `datos/`

Contiene los datos utilizados en el proyecto.

* Incluye datasets de origen (datos abiertos).
* Archivos utilizados como entrada para los procesos de transformación.
* Puede contener versiones limpias o preprocesadas de los datos.

### 📁 `esquemas/`

Contiene los esquemas semánticos utilizados para modelar los datos.

* Definiciones en formatos como RDF, OWL o TTL.
* Ontologías utilizadas para estructurar la información.
* Modelos que describen cómo se representan los datos en formato semántico.

### 📁 `tarea_n3/`

Implementación correspondiente a la Tarea 3.

* Notebook principal donde se realiza:

  * Carga de datos desde `datos/`.
  * Procesamiento y transformación de la información.
  * Generación de representaciones semánticas.
* Puede incluir generación de grafos o serialización en RDF.

### 📁 `tarea_n4/`

Implementación correspondiente a la Tarea 4.

* Notebook principal enfocado en:

  * Consumo de los datos ya transformados.
  * Ejecución de consultas sobre datos semánticos (por ejemplo SPARQL).
  * Análisis o explotación de la información generada en la tarea anterior.

## Organización general

* Las carpetas `datos/` y `esquemas/` actúan como base común para todas las tareas.
* Cada carpeta `tarea_nX/` contiene un flujo independiente de ejecución en notebooks.
* El proyecto sigue un flujo progresivo:

  1. Datos → procesamiento (Tarea 3)
  2. Datos semánticos → consulta y análisis (Tarea 4)

## Notas

* Los notebooks deben ejecutarse en orden dentro de cada tarea.
* Es necesario contar con los datos en la carpeta `datos/` para la correcta ejecución.
* Los esquemas definen la estructura que se aplica sobre los datos durante su transformación.
