
# Prueba tecnica Cientifico de Datos 

En este repositorio se encuentran 2 soluciones posibles al problema de ranking planteado en el archivo prueba_tecnica_IA.pdf.

Los cuales se dividen en lo siguiente:

    1- Semantich Search (Deep Learning)
    2- Text classification (Fine Tunning - LoRA)
    3- resultado_clasificador.json
    4- resultado_semantic_search.json

## Semantic Search
La primera solucion se encuentra en el archivo:

- ranking_2.ipynb: Dentro del codigo se encuentra la solucion utilizando un modelo con arquitectura transformer, bajo el modelo paraphrase-MiniLM-L6-v2 de hugging face. Este modelo es utilizado para una busqueda semantica donde se busca una similitud entre una pregunta y diferentes documentos a traves del calculo de la similitud Coseno. Se implemento una nueva capa densa en la salida del modelo para modificar algunos parametros y aplicarle fine tuning con la nueva informacion de train_query y train_documents para que aprenda de los nuevos vectores y relaciones entre si, y de esta manera buscar la similitud en los resultados con los datos de testeo. 

El documento consta de los siguientes pasos:

    a- Carga de datos
    b- Tratamiento de texto (Limpieza de texto)
    d- Carga del modelo "sentence-transformers/paraphrase-MiniLM-L6-v2"
    c- Tokenizacion
    d- Se añade una nueva capa densa a la salida del modelo
    e- Fine-tunning
    f- Calculo de la similitud coseno (metrica de evaluacion)
    g- Se busca las similut entre los datos test_query y test_document con el modelo pre entrenado
    h- Guardar los resultados.

## Text Classification

La segunda solucion se encuentra en el archivo:

- rankin_3.ipynb: Dentro del archivo se encuentra la solucion utilizando un modelo con arquitectura transformer, bajo la libreria distilbert de hugging face. El archivo contiene una explicacion del modelo y la tecnica LoRA basado en el articulo 'It Takes Two to Lie: One to Lie, and One to Listen, Denis Peskov, Benny Cheng'.
A diferencia de la primera solucion, en este caso se busca juntar la informacion de las consultas y los documentos para ser entrenados por el modelo a partir de un tensor que contenga toda la informacion y tratar de predecir si la informacion es relevante o no a traves de la metrica de similitud coseno entre la salida del modelo y el label. 
Una vez se entrene con la nueva data, se procede a realizar la inferencia del modelo en los datos de testeo de query y documents para obtener el tensor por separado y asi calcular la similitud coseno entre una consulta y 10 documentos mas relevantes. 

El documento consta de los siguientes pasos:

    a- Carga de los datos
    b- Tratamiento del texto (Normalizados)
    c- Modelo LLMS - distilbert-base-uncased
    d- Tokenizados - distilbert-base-uncased
    e- Se define la metrica de evaluacion - similitud coseno
    f- Modelo Baseline - LoRA config
    g- Resultados


## Authors

- [https://github.com/camilopulzara](https://github.com/camilopulzara)

