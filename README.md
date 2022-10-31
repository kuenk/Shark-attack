# Shark-attack
Proyecto de estudio y limpieza de una base de datos relacionada con ataques de tiburones

Se abre el archivo con el parametro: encoding = "ISO-8859-1", para evitar problemas de lectura del fichero CSV.

Podemos observar que es un archivo que cuenta con 25723 registros y 24 columnas. Gran parte de las columnas se refieren a datos alfanumericos, como nombres, descripciones, lugares o identificadores. 
También hemos podido identificar que hay muchos valores nulos, la gran mayoria de echo, siendo la columna 'Case Number' la que menos tiene con 17021 (recordemos que la muestra tiene 25723 registros)



Nuestro primer paso, va a ser eliminar cualquier columna que supere el 80% de valores nulos, es implicaría eliminar las siguientes columnas: 'Age', 'Time', 'Species', 'Unnamed: 22' y 'Unnamed: 23'.

![Nulls_heat_map](https://user-images.githubusercontent.com/111570446/199095903-28a525a0-f820-42c2-b42f-84d72703ddc7.png)

Dado que existen muchos datos nulos, quitamos todos los duplicados, quedandonos con 6312 filas.
Con las que queda, todos los nulos van a ser sustituidos por 'desconocido'. Este sería el resultado.

![clean_heat_map](https://user-images.githubusercontent.com/111570446/199099344-81780575-8db1-4b47-9348-2f07b2054307.png)

Existen 5 columans relacionadas con la fecha del ataque. Solo vamos a necesitar el año, por lo que crearemos una columna especifica en la que vamos a combinar la columna 'year' y 'date'.

Inspeccionando parte de los datos, eliminamos mas duplicados y datos sobrantes cuya informacion relacionada con la fecha no son aprovechables. Por último borramos las otras columnas de fechas.

El siguiente paso será limpiar del todo la nueva columna creada y dejar el dato como numérico. Con esto, podemos ver los outsiders en relacion a la fecha para poder quitarnos los ultimos resquicios.


![outliers](https://user-images.githubusercontent.com/111570446/199102999-48a5d92e-328e-4e59-af59-cd2e88cf816f.png)

No haremos el corte que nos marca el test de tukey ya que nos quitaria datos que si nos pueden ser utiles. Solo recortaremos en años del pasado, quedandonos con fechas cercanas a principios de 1800, donde los datos ya empiezan a ser consistentes.


![histograma_anio](https://user-images.githubusercontent.com/111570446/199103482-7dc2cc09-320b-4284-8171-a7c9254e1f73.png)

Aprovechamos este momento para reorganizar las columnas y pasamos a limpiar las columnas relacionadas con la lozalizacion de los ataques: 'country', 'location' y 'area'.

Para la columna de 'location', todos los datos que tengamos como 'desconocido' lo sobrescribimos con los datos de 'area'. 

Para la columna de fatal_Y_N vamos a seguir el mismo procedimiento que con las anteriores, en este caso, con la columna 'injury'. Si en esta, aparece la palabra "fatal", pondremos una "Y" en la columna, si no, lo dejaremos en "N". Con una revision mas exahustiva de la columna 'injury' se podría precisar mejor.
Estos serían los resultados actuales en cuanto al resultado de los ataques:

![ataques_mortales](https://user-images.githubusercontent.com/111570446/199106377-b6208d1e-028d-4114-b531-b046740a5391.png)

No olvidemos que esto es una aproximación, ya que en este punto, los datos no eran suficiente precisos.


Ahora vamos a limpiar la columna de genero, 'sex'. En este caso, para los casos dudosos, ya que no tenemos manera de contrastarlos con otras columnas, los datos que no sean validos, se pondran como 'desconocido'. Aun así, podemos ver una gran diferencia en cuanto al genero de las víctimas:



![sexo](https://user-images.githubusercontent.com/111570446/199107092-3bfe7761-d00f-42e5-be4f-76967630f34c.png)


También se ha limpiado la columna de edades, en esta ocasion, hay una gran cantidad de valores desconocidos, por lo que para sacar algun tipo de estadistica, habria que separar estos datos y tratar los restantes.

