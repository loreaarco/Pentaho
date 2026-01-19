### ------------Caso 1 · Filtrado y ordenación de clientes (CSV → CSV)--------------------

* Parte 1 :
  -Lo primero es crear una transformación que es donde se va a hacer la lectura de los archivos, se ponen filtros para gestionar la información y donde se va a hacer la trasformación de un archivo a otro archivo.
  -Luego e añadido de la categoría Input(Entrada) y añado CSV file input (Entrada de archivo CSV) que es para recoger el archivo que se quiere coger la informacion. Para configurar esto hay que darle doble click. En el apartado de Filename se le pasa la ruta de donde se encuentra el archivo. Luego se le da a extraer campos, esto lo que hace es traer todos los elementos del archivo para poder coger la información del mismo.
  -Después de traer los campos hay que ponerle los tipos de datos a cada uno de ellos. Para comprobar si la lectura de datos se realiza sin ningún problema se da al botón de Preview (previsualización) sale otra pantalla con los datos sacados.



* Parte 2:

 	- Luego de haber leído los datos anteriores, lo que voy ha hacer ahora es filtrar las filas, para que pasar la información del archivo hay que darle a Main output of step. Para hacer el filtrado en la categoría de Flow cojo el Filter (Filtrar filas), y lo conecto con el anterior paso.

 	- Cuando se le da doble click para configurar el Filter. De la manera que yo lo he configurado a sido, en la condición le he puesto el STATE = NY, que esto lo que hace es filtrar por el STATE y solo coge el de NY(New York).



* Parte 3:

 	- Luego de haber hecho el filtro del STATE, lo que hago es ordenarlo de manera ascendente. Para eso en Transfom(Transformar) cojo el Sort rows(Ordenar filas) que sirve para ordenar las filas. Lo conecto con el anterior paso.

 	- Después de haber seleccionado del filtro lo configuro, selecciono el Only pass unique rows? (verifies keys only). Luego traigo los campos que se han sacado y se han filtrado anteriormente. Salen los campos que se quieren, en este caso todos los campos se quedan en N meno ZIP que hay que cambiar a S.

* Parte 4:

 	- Luego de haber ordenado el archivo, lo que hago es sacarlo en un archivo csv, para eso lo que hay que hacer es, en la categoría de Output(Salida), coger el paso de Text file output(Salida de archivo de texto).Lo conecto con el anterior paso.

 	- Para configurar la salida hay que darle doble click, en nombre fichero hay que poner la dirección de donde quieres que se guarde el fichero y nombre al archivo.



### ----------Caso 2 · Unión ventas–productos y agregación (CSV + CSV → CSV)---------------



* Parte 1:

 	-Lo primero que he hecho a sido crear una nueva transformación.

 	-Luego le he añadido de la categoría Entrada(Input) que le arrastro el CSV file input (entrada de archivo csv) a la zona donde se va a trabajar. Lo saco 2 veces por ser dos archivo csv, uno para sales y otro para productos. En el CSV file input de sales le paso la dirección de donde se encuentra el archivo de sales. Con el otro CSV file input hago lo mismo, le paso la dirección donde se encuentra el archivo de productos.

* Parte 2:

 	-Después le he añadido desde la categoría Transformar (Transform) cojo el paso de Ordenar filas, lo conecto con CSV file input seleccionando que ordenar filar pueda coger la información de los csv de ambos archivos. Cuando ya lo he añadido en el caso de sales, traigo todos los campos y cambio de los apartados que no me interesan los cambio a N y el apartado que me interesa lo pongo a S. En el caso de los sales pongo en S ProductID, los demás los pongo en N. En el caso de los productos, pongo en S ProductID y los demás los pongo en N.

* Parte 3:

 	-Luego añado del apartado de Unión cojo el de Unión por clave y lo conecto con orden de filas 2 y filas 3. Después de unirlo lo que hago es configurarlo para que mediante los campos claves sean las que he cambiado a N para que las claves con las que se junten sean ProductID en los dos apartados.

* Parte 4:

 	-Ahora añado del apartado Transformar cojo la Calculadora, lo conecto al Unión por clave. Después lo configuro, añado un nuevo campo llamado Revenue, que calcula A \* B (en este caso son los apartados de sales y productos), en el campo A son los Units, en el campo B son los UnitPrice, el tipo de valor le pongo Number, en el campo Eliminar le pongo una N, los demás los dejo vacíos.

* Parte 5:

 	-Después le he añadido desde la categoría Transformar (Transform) cojo el paso de Ordenar filas, lo conecto con la calculadora. Luego lo configuro, selecciono el traer campo para que me traiga todos los campos y solo me quedo con Country y Category, los demás campos los elimino. El campo Country hago unos cambio en el ascendente pongo S, en el campo Case sensitive compare? pongo N, en el campo Sort based on current locale? pongo N, en el campo Collator Strength pongo 0, en el campo Presorted? pongo N. El campo Category hago unos cambio en el ascendente pongo S, en el campo Case sensitive compare? pongo N, en el campo Sort based on current locale? pongo N, en el campo Collator Strength pongo 0, en el campo Presorted? pongo N.

* Parte 6:

 	-Luego del apartado Statistics cojo el Agrupar por. Lo primero que hago es obtener los campos luego elimino todos los campos que no sean Country y Category. En el siguiente apartado añado Total Unidades y Total Revenue. En Total Unidades en el campo Asunto pongo Units, en el campo Tipo pongo Suma.En Total Revenue en el campo Asunto pongo Revenue, en el campo Tipo pongo Suma.

* Parte 7:

 	-Después del apartado Salida añado la Salida Fichero de Texto. Ahora lo configuro con la dirección donde quiero que se guarde, indicando el tipo de extensión quiero que se guarde.





### --------Caso 3 · Selección/renombrado, filtro compuesto y salida JSON (múltiples CSV → JSON)--

* Parte 1 :

&nbsp;	-Lo primero que he hecho a sido crear una nueva transformación.

&nbsp;	-Lo que he hecho es añadir un CSV fiel input. Lo saco dos veces uno para el archivo de logs1 y el otro para el archivo de logs2. En la configuración del primero le cambio el nombre para poner el nombre de: CSV file logs1 para diferenciarlo del otro. Al otro le pongo el nombre: de CSV file logs2. Para el CSV file logs1 la configuración que le he puesto es: en el filename pongo la dirección en la que se encuentra el archivo. Luego le doy a traer campos del archivo. Para el CSV file logs2 la configuración que le he puesto es: en el filename pongo la dirección en la que se encuentra el archivo.

* Parte 2:

&nbsp;	-Ahora saco un Selecciona/Renombre valores que lo uno a CSV file logs1 que en este caso lo voy a utilizar para renombrar algunos campos. La configuración que le he hecho a sido en el apartado de selecciona \& modifica. Le doy al obtener campos a seleccionar Y traigo todos los campos del archivo. Elimino los que no quiero cambiar el nombre y solo me quedo con timestamp que le cambio el nombre a ts, también me quedo con message que le cambio el nombre a msg.



&nbsp;	-Ahora saco otro Selecciona/Renombre valores que lo uno a CSV file logs2 que en este caso lo voy a utilizar para eliminar algunos campos. La configuración que le he hecho a sido en el apartado de Eliminar. Le doy al obtener campos a seleccionar Y traigo todos los campos del archivo. Elimino los que no quiero cambiar el nombre y solo me quedo con timestamp, también me quedo con message.



* Parte 3:

&nbsp;	-Luego saco el Java filter. Lo conecto con Selecciona/Renombre valores del CSVfile logs1.Tambien añado Transformación simulada(no hace nada) aquí no cambio nada.

&nbsp;La configuración que le pongo es en Destination step for matching rows le pongo JSON output. En Destination step for non-mathing rows le pongo Transformación simulada(no hace nada). En Condition (Java expresión) pongo: ( (level != null \&\& (level.equals("ERROR") || level.equals("WARN"))) || service == null ) \&\& ts != null .

&nbsp;	-Ahora añado JSON output. Lo conecto con el Java filter Que es para sacar el un json la información. La configuración que le he puesto es en el Output File que solo pongo donde quiero que se guarde el JSON, le nombre que le he dado es: case3\_logs1\_filtered

* Parte 4:

&nbsp;	-Luego saco el Java filter. Lo conecto con Selecciona/Renombre valores del CSVfile logs2.Tambien añado Transformación simulada(no hace nada) aquí no cambio nada.

 La configuración que le pongo es en Destination step for matching rows le pongo JSON output. En Destination step for non-mathing rows le pongo Transformación simulada(no hace nada). En Condition (Java expresión) pongo: (level != null \&\& (level.equals("ERROR") || level.equals("WARN"))) || service == null .

 	-Ahora añado JSON output. Lo conecto con el Java filter Que es para sacar el un json la información. La configuración que le he puesto es en el Output File que solo pongo donde quiero que se guarde el JSON, el nombre que le he dado es: case3\_logs2\_filtered.



### -------Caso 4 · Informe por fabricante y precio medio (CSV + CSV + CSV → CSV / S3)------------



* Parte 1 :

 	-Lo primero que he hecho a sido crear una nueva transformación.

&nbsp;	-Ahora saco un CSV file input, la configuracion que he puesto es: en el filename pongo la direccion de donde se encuentra el archivo csv que es sales.csv. Tambien le cambio a CSV sales. Luego traigo los campos del archivo.

* Parte 2:

&nbsp;	-Luego saco ordenar filas, que la configuracion es traer los campos y el campo ProductID y el campo ascendente lo pongo a S. Lo uno a CSV sales



* Parte 3:

&nbsp;	-Ahora saco un CSV file input, la configuracion que he puesto es: en el filename pongo la direccion de donde se encuentra el archivo csv que es products.csv. Tambien le cambio a CSV productos. Luego traigo los campos del archivo.

* Parte 4:

&nbsp;	-Luego saco ordenar filas, que la configuracion es traer los campos y el campo ProductID y el campo ascendente lo pongo a S. Lo uno a CSV productos.



* Parte 5:

&nbsp;	-Ahora saco un CSV file input, la configuracion que he puesto es: en el filename pongo la direccion de donde se encuentra el archivo csv que es manufacturers.csv. Tambien le cambio a CSV fabricantes. Luego traigo los campos del archivo.

* Parte 6:

&nbsp;	-Luego saco ordenar filas, que la configuracion es traer los campos y los campos ManufacturerID, ManufacturerName, Country y el campo ascendente lo pongo a S. Lo uno a CSV fabricantes.

* Parte 7:

&nbsp;	-Ahora saco Union por clave, que lo uno con Ordenar filas2 y Ordenar filas3. La configuracion es: en el primer paso pongo Ordenar por filas 2, en el segundo Ordenar por filas 3. Luego en las columnas traigo los campos y borro todas menos ProductID, en las dos columnas.

* Parte 8:

 	-Ahora saco Union por clave2, que lo uno con Ordenar filas4 y Union por clave. La configuracion es: en el primer paso pongo Union por clave, en el segundo Ordenar por filas 4. Luego en las columnas traigo los campos y borro todas menos ManufacturerID, en las dos columnas.

* Parte 9:

&nbsp;	-Ahora saco una Calculadora, lo uno con Union por clave2. en los campos añado uno nuevo: el nombre que le pongo Revenue, el calculo es A \* B, en el campo A pongo la variabla Units, en el campo B UnitPrice, el Tipo Valor number, Eliminar N.

* Parte 10:

&nbsp;	-Luego añado Agrupar, lo uno con la calculadora, la configuracion en la primera tabla, lo primero que hago es obtener campos, borro todos los campos menos Country, ManufacturerID, ManufacturerName. En la segunda tabla añado nombre a dos agregados uno TotalUnidades, el asunto Units, el tipo Suma. Dos totalRevenue, el asunto Revenue, el tipo Suma.

* Parte 11:

 	-Ahora saco una Calculadora, lo uno con Agrupar. En los campos añado uno nuevo: el nombre que le pongo AvgPrice, el calculo es A \* B, en el campo A pongo la variabla TotalRevenue, en el campo B TotalUnidades, el Tipo Valor number, Eliminar N.

* Parte 12:

&nbsp;	-Luego añado Salida fichero de Texto que lo uno con la ultima calculadora que se a configurado. La configuracion es la direccion de donde se quiere guarda el archivo.



### ------Caso 5 · Job orquestador (comprobaciones + ejecución encadenada)--------------

* Parte 1:

&nbsp;	-Lo primero que hago es crear un Job que es donde voy a trabajar.

&nbsp;	-Ahora añado Start que no hay que configurarlo de ninguna manera.

* Parte 2:

&nbsp;	-Luego añado Create a folder que lo unico que hay que hacer es la direccion donde se quiere que se cree una carpeta y para que no de error de que ya existe la carpeta hay que quitar el boton que dice fail if dolder exits. Lo conecto con el Start.

* Parte 3:

&nbsp;	-Ahora añado File exists que la configuracion es al nombre le pongo: File exists case2\_sales\_by\_country\_category, al file name le pongo: la direccion donde se va a guardar y el nombre del archivo que es: case2\_sales\_by\_country\_category.csv. Lo uno con Create a folder.

&nbsp;	-Ahora añado File exists que la configuracion es al nombre le pongo: File exists 2 case4\_manufacturer\_report, al file name le pongo: la direccion donde se va a guardar y el nombre del archivo que es: case4\_manufacturer\_report.csv. Lo uno con Create a folder.

* Parte 4:

&nbsp;	-Luego añado Delete file que la configuracion es el nombre es Delete file caso4. En el fiel name es donde se va a guardar el archivo para que no de error de que si existe el archivo o no. Lo conecto con File exists 2 case4\_manufacturer\_report.

* &nbsp;	-Luego añado Delete file que la configuracion es el nombre es Delete file caso2. En el fiel name es donde se va a guardar el archivo para que no de error de que si existe el archivo o no.Lo conecto con File exists case2\_sales\_by\_country\_category.
* Parte 5:

&nbsp;	-Ahora añado Display msgbox info que la configuracion es en el Message Title: Comienza pipeline Pentaho. En Message Body: Comienza pipeline Pentaho. Lo conecto con Delete file caso2, Delete file caso4, Transformation caso4, Transformation caso2.

* Parte 6:

&nbsp;	-Luego añado Abort job la configuracion es en Message: No se encuentran los archivos. Esta conectado con File exists case2\_sales\_by\_country\_category,File exists 2 case4\_manufacturer\_report,Transformation caso 4, Transformation caso 2.



* Parte 7:

&nbsp;	-Ahora añado Transformation caso4 que la configuracion es en trasformation: es la direccion de donde esta el caso4.ktr, el nombre: Transformation caso 4. Esta conectado con Abort job.

* Parte 8:

 	-Ahora añado Transformation caso2 que la configuracion es en trasformation: es la direccion de donde esta el caso2.ktr, el nombre:Transformation caso 2. Esta conectado con Abort job.

* Parte 9:

&nbsp;	-Luego añado Success que no hay que configurar. Esta conectado con: Transformation caso4 y Transformation caso2. 



