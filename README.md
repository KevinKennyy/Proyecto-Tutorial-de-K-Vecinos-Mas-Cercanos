# Sistema de Recomendación de Películas
# Descripción del Proyecto
Este proyecto tiene como objetivo desarrollar un sistema de recomendación de películas utilizando un conjunto de datos que recopila información de la API TMDB (The Movie Database). Se proporcionan dos conjuntos de datos: tmdb_5000_movies y tmdb_5000_credits, que contienen información sobre películas y sus créditos respectivamente.

# Instrucciones
# Paso 1: Carga del Conjunto de Datos
Descarga los conjuntos de datos desde los siguientes enlaces:

tmdb_5000_movies
tmdb_5000_credits
Carga cada archivo en un DataFrame de Pandas separado para almacenar la información de películas y créditos respectivamente.

# Paso 2: Creación de una Base de Datos
Crea una base de datos para almacenar los dos DataFrames en tablas distintas. Luego, únelas utilizando SQL para generar una tercera tabla que contenga información unificada de ambas. La clave para la unión será el título de la película (title).

Limpia la tabla generada dejando solo las siguientes columnas:

- movie_id
- title
- overview
- genres
- keywords
- cast
- crew

# Paso 3: Transforma los Datos
Procesa las columnas con formato JSON seleccionando el atributo name y reemplazando las columnas genres y keywords. Para la columna cast, selecciona los tres primeros nombres.

Transforma la columna crew para que contenga solo el nombre del director. Convierte la columna overview en una lista de palabras.

Elimina los espacios entre las palabras en las columnas genres, cast, crew y keywords.

Combina todas las columnas convertidas en una sola columna llamada tags y reemplaza las comas por espacios en blanco.

# Paso 4: Construye un KNN
Vectoriza el texto de la columna tags y elige la distancia del coseno como métrica de similitud.

Diseña una función de recomendación basada en la distancia del coseno que devuelva las 5 películas más similares a la película dada.

python
Copiar código
def recommend(movie):
    movie_index = new_df[new_df["title"] == movie].index[0]
    distances = similarity[movie_index]
    movie_list = sorted(list(enumerate(distances)), reverse=True, key=lambda x: x[1])[1:6]
    
    for i in movie_list:
        print(new_df.iloc[i[0]].title)
Úsala de la siguiente manera:

python
Copiar código
recommend("Introduce una película")
