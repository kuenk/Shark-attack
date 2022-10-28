# Shark-attack
Proyecto de estudio y limpieza de una base de datos relacionada con ataques de tiburones

Se abre el archivo con el parametro: encoding = "ISO-8859-1", para evitar problemas de lectura del fichero CSV.

Podemos observar que es un archivo que cuenta con 25723 registros y 24 columnas. Gran parte de las columnas se refieren a datos alfanumericos, como nombres, descripciones, lugares o identificadores. 
También hemos podido identificar que hay muchos valores nulos, la gran mayoria de echo, siendo la columna 'Case Number' la que menos tiene con 17021 (recordemos que la muestra tiene 25723 registros)



Nuestro primer paso, va a ser eliminar cualquier columna que supere el 80% de valores nulos, es implicaría eliminar las siguientes columnas: 'Age', 'Time', 'Species', 'Unnamed: 22' y 'Unnamed: 23'.

![null heat map](r'C:\Users\USER\Desktop\Proyectos\Shark-attack\docs\nulls_heat_map.png)

