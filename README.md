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

Cree un módulo **entrenos.py** e implemente en él una función **lee_entrenos**, que reciba la ruta de un fichero en formato CSV codificado en UTF-8 y devuelva una lista de tuplas de tipo Entreno. Utilice la función datetime.strptime con el formato ```%d/%m/%Y %H:%M``` para convertir la fecha. Cree una función auxiliar **a_booleano** para hacer la conversión de cadena a booleano.

Cree un módulo **entrenos_test.py** e implemente en él una prueba de la función anterior, que lea los datos del ficheros ```entrenos.csv``` ubicado en la carpeta ```data``` y muestre los tres primeros y tres últimos registros leídos. 

Añada al módulo **entrenos.py** las siguientes funciones, añadiendo por cada una un método de test al módulo **entrenos_test**.

1. Función **filtra_por_ubicacion** que dadas una lista de tuplas de tipo Entreno y una ubicación, 
devuelva otra lista de tuplas de tipo Entreno con aquellos registros que son de la ubicación dada.
2. Función **tipos_entrenamiento** que dadas una lista de tuplas de tipo Entreno, una fecha de inicio y una fecha de fin, devuelva el número de tipos de entrenamientos distintos realizados  en el intervalo de fechas [fecha_inicio, fecha_fin). Si fecha_inicio es None, la función devuelve el número de tipos de entrenamientos distintos hasta fecha_fin (sin incluir fecha_inicio). Si fecha_fin es None, entonces devuelve el número de tipos de entrenamientos distintos desde fecha_inicio (inclusive). Si fecha_inicio y fecha_fin son None, entonces devuelve el número total de entrenamientos.Para implementar esta función defina una función auxiliar **fecha_en_intervalo** que tome como entrada una tupla de tipo Entreno, una fecha inicio y una fecha fin, y devuelva cierto si el Entreno está en las fechas solicitadas, teniendo en cuenta las consideraciones mencionadas anteriormente.
3. Función **distancia_total_de_momento_dia** que dadas una lista de tuplas de tipo Entreno y un momento del día (una cadena que puede tomar los valores "MAÑANA", "TARDE" o "NOCHE") devuelva la distancia total recorrida en los entrenamientos realizados en ese momento del día. Considere los siguientes rangos horarios:
    * MAÑANA [07:00, 14:00) 
    * TARDE [14:00, 21:00) 
    * NOCHE [21:00, 07:00)
   
   Para implementar esta función defina una función auxiliar **momento_dia**, que tome una tupla de tipo Entreno, y devuelva una cadena "MAÑANA", "TARDE" o "NOCHE", dependiendo del momento del día en el que se produjo el entrenamiento.
