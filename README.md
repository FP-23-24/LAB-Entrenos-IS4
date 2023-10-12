# Ejercicio de lectura de datos de entrenos

Disponemos de datos sobre los entrenamientos realizados por un usuario. Para cada entrenamiento se tiene 
la siguiente información: 
* tipo: tipo de entrenamiento realizado, de tipo str. 
* fechahora: fecha y hora del entrenamiento, de tipo datetime. 
* ubicación: lugar donde se ha realizado el entrenamiento, de tipo str 
* duración: duración del entrenamiento en minutos, de tipo int. 
* calorías: número de kilocalorías activas quemadas en el entrenamiento, de tipo int. 
* distancia: distancia en kilómetros recorrida en el entrenamiento, de tipo float. 
* frecuencia: frecuencia cardiaca media registrada en el entrenamiento, de tipo int. 
* compartido: indica si el entrenamiento ha sido compartido por el usuario, de tipo bool (S si ha sido 
compartido, N si no lo ha sido). 

Por ejemplo, la siguiente línea del fichero: 

```Andar,12/11/2021 8:14,Sevilla,48,155,3.49,89,N```

indica que el 12 de noviembre de 2021 a las 8:14 horas, el usuario realizó un entrenamiento de tipo ‘Andar’
durante 48 minutos, quemando 155 kilocalorías activas y recorriendo un total de 3.49 kilómetros con una
frecuencia cardiaca media de 89 lpm, y que no compartió este entreno.

Para almacenar los datos de un entrenamiento se usará obligatoriamente la siguiente namedtuple:

```Entreno = namedtuple('Entreno', 'tipo, fechahora, ubicacion, duracion, calorias, distancia, frecuencia, compartido')```

Cree un módulo **entrenos.py** e implemente en él una función **lee_entrenos**, que reciba la ruta de un fichero en formato CSV codificado en UTF-8 y devuelva una lista de tuplas de tipo Entreno. Utilice la función datetime.strptime con el formato ```%d/%m/%Y %H:%M``` para convertir la fecha. 

Cree un módulo **entrenos_test.py** e implemente en él una prueba de la función anterior, que lea los datos del ficheros ```entrenos.csv``` ubicado en la carpeta ```data``` y muestre los tres primeros y tres últimos registros leídos. 