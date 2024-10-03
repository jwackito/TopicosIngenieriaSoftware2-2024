# Dataset de avisos clasificados de venta de inmuebles

## Descripción del problema
El dataset que vamos a estudiar representa avisos clasificados de inmuebles en venta. Este dataset es generado por un *scrapper* que obtiene la información de diferentes sitios de anuncios clasificados. Como los datos provienen de diferentes sitios, es normal que un mismo inmueble aparezca publicado más de una vez. Esto es un problema para el análisis. Nuestra tarea es entrenar un sistema de inteligencia artificial que nos permita identificar aquellos avisos que hablan del mismo inmueble.

El dataset tiene dos representaciones. Una representación cruda (raw) que tiene forma de documento .csv en formato excel, con varias columnas que describen la información que obtiene el *scrapper* de cada aviso. Este archivo tiene unos 750K registros y pesa 1.4GB. Por motivos prácticos, este archivo no será compartido. Sin embargo, la columna `indice` de las muestras con las que vamos a trabajar, hace referencia a al número de linea donde aparece este aviso en el archivo original. 

Luego, cada una de las lineas del dataset original, es pre-procesada para obtener una representación en forma de grafo utilizando una ontología predefinida. Hay dos tipos de nodos de suma importancia para el análisis, 1) el nodo que representa al  aviso y 2) el nodo que representa al inmueble. Cada uno de estos nodos tiene sus propiedades. Por ejemplo, el **nodo aviso** tiene una descrición, un precio y un sitio en el que fue publicado, mientras que el **nodo inmueble** tiene una superficie, un localización geográfica, un tipo (casa, departamento, terreno, etc). Cada fila del dataset crudo es representada entonces con un subgrafo que contiene un **nodo aviso** y un **nodo inmueble**, conectados por una relación que indica que el aviso habla de ese inmueble.

Un tercer archivo, indica los índices en el dataset crudo, de aquellos registros que son candidatos a estar duplicados. Estas filas fueron pre identificadas por un algoritmo que tiene una alta tasa de falsos positivos, es decir que identifica aviso que hablan del mismo inmueble cuando no necesariamente es el caso. 

### El dataset en crudo (muestras)

### El dataset como grafo de conocimiento
El dataset puede verse como grafo de conocimiento utilizando [esta herramienta](https://www.semantechs.co.uk/turtle-editor-viewer/), cargando por ejemplo el archivo `dataset/graph-sample.ttl`. Aqui pueden verse tres inmuebles, `ns1:space_site2_A1533904546`, `ns1:space_site3_49766448` y `ns1:space_site3_52631481`. Los dos primeros son grafos que representan el mismo inmueble, y por ello están relacionados mediante `owl:sameAs`.
![image](https://github.com/user-attachments/assets/feec743c-9f0b-4dad-9d72-411338b92a40)



## Descripción de la metadata


