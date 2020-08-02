[Contenidos](../Contenidos.md) \| [Anterior (4 Random+)](04_Random.md) \| [Próximo (6 El album de Figuritas+)](06_Figuritas.md)

# 3.5 NumPy

Esta es una introducción al módulo NumPy.

NumPy (**Numerical Python**) es una biblioteca de Python (una colección de módulos) de código abierto que tiene aplicaciones en casi todos los campos de las ciencias y de la ingeniería.  Es el estándar para trabajar con datos numéricos en Python. Muchos módulos como Pandas, SciPy, Matplotlib, scikit-learn, scikit-image usan NumPy.

Esta biblioteca permite trabajar cómodamente con matrices multidimensionales por medio del tipo  **ndarray**, un objeto n-dimensional homogéneo (con entradas del mismo tipo), y con métodos para operar eficientemente sobre él. NumPy puede usarse para una amplia variedad de operaciones matemáticas sombre matrices. Le agrega a Python estructuras de datos muy potentes osbre las que se puede calcular y operar matemáticamente con eficiencia y a un alto nivel.

## Instalar NumPy

Si no lo tenés instalado (primero probá imoprtarlo, es muy probable que ya lo tengas) podés instalarlo escribiendo :

```bash
conda install numpy
```

o

```bash
pip install numpy
```

## Importar  NumPy

Cuando quieras usar NumPy en Python, primero tenés que importarlo:

```python
import numpy as np
```

Acortamos `numpy` a `np` para ahorrar tiempo y mantener el código estandarizado. Todes escriben `np`.


## ¿Cuál es la diferencia entre listas y arreglos?

NumPy ofrece varias formas muy eficientes de crear vectores y manipular datos numericos en su interior. Mientras que una lista de Python puede contener diferentes tipos de datos en su interior, los elementos de un vector numpy serán todos del mismo tipo. De esta forma numpy puede asegurar una alta perforance en las operaicones matemáticas.

Además, los arreglos están pensados para tener un tamaño fijo, mientras que las listas están diseñadas para agregar y sacar elementos. Son estructuras de datos similares desde un punto de vista superficial, pero muy diferentes en cuanto a las posibilidades y perfomances que brindan. 

Las operaciones matemáticas sobre vectores de numpy son más rápidas que sobre listas. Además los vectores ocupan menos memoria que las listas análogas. Pero cambiar el tamaño de una lista es algo muy sencilo mientras que el de un vector es costoso. O mezclar diferentes tipos de datos es posible en las listas pero imposible en los vectores de NumPy.

## Arreglos n-dimensionales

Los vectores (unidimensionales) y matrices (bidimensiones) se generalizan a arreglos n-dimensionales. Esta estructura de datos es la central de la biblioteca NumPy. Un arreglo (`ndarray`) es una grilla de valores que contiene información sobre los datos crudos, cómo ubicarlos y cómo interpretarlos. Tiene una grilla de elementos que pueden ser indexados de diversas maneras. Los elementos de un arreglo son todos del mismo tipo, frecuentemente abreviado como `dtype`.

Un arreglo puede ser indexado por tuplas de enteros no negativos, por variables booleanas, por otro arreglo o por enteros. El rango (`rank`) de un arreglo es su número de dimensiones. Su forma (`shape`) es una tupla de enteros que dice su tamaño en cada dimensión.

Una forma de inicializar un arreglo de NumPy es mediante una lista de números. Esto nos da un vector (arreglo de dimensión uno). Usando listas anidadas, podemos definir arreglos de más altas dimensiones.

Por ejemplo:

```python
>>> a = np.array([1, 2, 3, 4, 5, 6])
```

o:

```python
>>> a = np.array([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])
```

Podemos acceder a los elementos de un arreglo usando corchetes. Acordate que los índices comienzan a contar en 0. Esto significa que si querés acceder al primer elemento, vas a acceder al elemento “0”.

```python
>>> print(a[0]) #si tiene múltiples dimensiones, esto me da una "rebanada" de una dimension menos
[1 2 3 4]
>>> print(a[2]) #  otra rebanada
array([ 9, 10, 11, 12])
>>> print(a[2][3]) #accedo al cuarto elemento del tercer vector de a
12
>>> print(a[2,3]) # o, equivalentemente, accedo al elemento en la tercera fila y cuarta columna de a
12
```


## Más información sobre arreglos


Ocasionalmente vas a ver que alguien se refiere a un arreglo como un  “ndarray” que es una forma breve de decir arreglo n-dimensional. Un arreglo n-dimensional es simplemente un arreglo con n dimensiones. Recordemos que cuando son unidimensionales los llamamos vectores y si son bidimensionales los llamamos matrices.

**¿Qué atributos tiene un arreglo?**

Un arreglo es usualmente un contenedor de tamaño fijo de elementos del mismo tipo. Su forma (shape) es una tupla de enteros no negativos que especifica el tamaño del arreglo en cada dimensión. Tiene tantas dimensiones como coordenadas en la tupla.

En NumPy, las dimensiones se llaman **axes** (ejes). Esto dignifica que si tenés una arrglo bidimensional que se ve así:

```
[[0., 0., 0.],
 [1., 1., 1.]]
```

el arreglo tendrá dos ejes. El primer eje tiene tamaño dos, el segundo tamaño tres (si, se cuentan primero filas, luego columnas).

De la misma forma que los otros objetos contenedores de Python, los elementos de un arreglo pueden ser accedidos y modificados usando índices y rebanadas.

## Crear un arreglo básico

Para crear un arreglo de NumPy podés usar la función `np.array()`.
Lo único que necesitás es pasarle una lista. Si querés, podés especificar el tipo de datos que querés que tenga. 

```python
>>> import numpy as np
>>> a = np.array([1, 2, 3])
```

Vamos a representar la creación con este gráfico:

![./np_array.png](./np_array.png)

_Ojo, estas visualizaciones son simplificaciones para representar lo que esta pasando y darte un entendimiento básico de los conceptos y mecanismos de NumPy. Los arreglos y sus operaciones tienen aspectos más complejos que los que quedan capturados en estos dibujitos._

A parte de poder crear una arreglo a partir de una secuencia de elementos, podés crear un arreglo lleno de `0`’s:

```python
>>> np.zeros(2)
array([0., 0.])
```

O uno lleno de `1`’s:

```python
>>> np.ones(2)
array([1., 1.])
```

¡O incluso uno no inicializado! La función `empty` crea un arreglo cuyo contenido inicial depende del estado de la memoria. Usar `empty` en lugar de  `zeros` (o `ones`) es la velocidad - al no inicilizar los valores no perdemos tiempo. ¡Pero asegurate de ponerle valores con sentido luego!

```python
>>> # Crea un arreglo con dos elementos
>>> np.empty(2)
array([ 3.14, 42.  ])  # puede variar
```

También podés crear vectores a partir de un rango de valores:

```python
>>> np.arange(4)
array([0, 1, 2, 3])
```

También un vector que contiene elementos equiespaciados, especificando el **primer número**, el **límite**, y el **paso**.

```python
>>> np.arange(2, 9, 2)
array([2, 4, 6, 8])
```
El límite nunca está en la lista. 

También podés usar `np.linspace()` para crear un vector especificando el **primer número**, el **último número**, y la **cantidad** de elementos:

```python
>>> np.linspace(0, 10, num=5)
array([ 0. ,  2.5,  5. ,  7.5, 10. ])
```


**Especificar el tipo de datos**

Si no lo especificá, el tipo de datos (por omisión) de los arreglos es el punto flotante (`np.float64`). Sin embargo, podés explicitar otro tipo de datos usando la palabra clave `dtype`.

```python
>>> x = np.ones(2, dtype=np.int64)
>>> x
array([1, 1])
```

En estos dos casos el 64 de los tipos de datos se refiere a la cantidad de bits, 64 bits. 

## Agregar, borrar y ordenar elementos

Ordenar un vector es sencillo usando `np.sort()`. 
Por ejemplo, si comenzás con este vector:

```python
>>> arr = np.array([2, 1, 5, 3, 7, 4, 6, 8])
```

Podés ordenar sus elementos con:

```python
>>> np.sort(arr)
array([1, 2, 3, 4, 5, 6, 7, 8])
```
Fijate que el vector `arr` quedó desordenado. `sort` simplemente devolvió una copia ordenada de los datos pero no modificó el original.

Otra operación usual es la concatenación. Si empezás con estos dos vectores:

```python
>>> a = np.array([1, 2, 3, 4])
>>> b = np.array([5, 6, 7, 8])
```

los podés concatenar usado `np.concatenate()`.

```python
>>> np.concatenate((a, b))
array([1, 2, 3, 4, 5, 6, 7, 8])
```

Un ejemplo un poco más complejo es el siguiente: Si tenés:

```python
>>> x = np.array([[1, 2], [3, 4]])
>>> y = np.array([[5, 6]])
```

Los podés concatenar usando:

```python
>>> np.concatenate((x, y), axis=0)
array([[1, 2],
 [3, 4],
 [5, 6]])
```

Para sacar elementos de un arreglo, lo más sencillo es usar los índices para seleccionar los que queremos conservar.


## Conocer el tamaño, dimensiones y forma de un arreglo


`ndarray.ndim` te dice la cantidad de ejes (o dimensiones) de arreglo.

`ndarray.shape` te va a dar una tupla de enteros que indican la cantidad de elementos en cada eje. Si tenés una matriz con 2 filas y 3 columnas de va a dar `(2, 3)`.

`ndarray.size` te dice la cantidad de elementos (cantidad de numeros) de tu arreglo. Es el producto de la tupla `shape`. En el ejemplo del renglón anterior, el `size` es 6.

Por ejemplo, si creás este arreglo de tres dimensiones:

```python
>>> array_example = np.array([[[0, 1, 2, 3],
...                            [4, 5, 6, 7]],
...
...                           [[0, 1, 2, 3],
...                            [4, 5, 6, 7]],
...
...                           [[0 ,1 ,2, 3],
...                            [4, 5, 6, 7]]])
```

Vas a tener
```python
>>> array_example.ndim # cantidad de dimensiones
3
>>> array_example.shape # cantidad de elementos en cada eje 
(3, 2, 4)
>>> array_example.size # total de elementos 3*2*4
24
```

## Cambiar la forma de un arreglo

Usando `arr.reshape()` le podés dar una nueva forma a tu arreglo sin cambiar los datos. Solo tené en cuenta que antes y después del reshape el arreglo tiene que tener la misma cantidad de elementos. Por ejemplo, si comenzás con un arreglo con 12 elementos, tendrás que asegurarte que el nuevo arreglo siga teniendo 12 elementos.

Por ejemplo:

```python
>>> a = np.arange(6)
>>> print(a)
[0 1 2 3 4 5]
```

Podés usar `reshape()` para cambiarle la forma y que en lugar de ser un vectore de 6 elementos, sea una matriz de 3 filas y dos columnas:

```python
>>> b = a.reshape(3, 2)
>>> print(b)
[[0 1]
 [2 3]
 [4 5]]
```

## Agregar un nuevo eje a un arreglo

A veces pasa que tenemos un vector con n elementos y necesitamos pensarlo como una matriz de una fila y seis columnas o de seis filas y una columna. Podés usar `np.newaxis` para agregarle dimensiones a un vector existente.

Usando `np.newaxis` una vez podés incrementar la dimensión de tu arreglo en uno. Por ejemplo podés pasar de un vector a una matriz o de una matriz a un arreglo tridimensional, etc.

Por ejemplo, si comenzás con este vector:

```python
>>> a = np.array([1, 2, 3, 4, 5, 6])
>>> a.shape
(6,)
```

Podés usar `np.newaxis` para agregarle una dimensión y convertirlo en un vector fila:

```python
>>> vec_fila = a[np.newaxis, :]
>>> vec_fila.shape
(1, 6)
```

Or, para convertirlo en un vector columna, podés unsertar un eje en la segunda  dimensión:

```python
>>> vec_col = a[:, np.newaxis]
>>> vec_col.shape
(6, 1)
```

## Índices y rebanadas

Los arreglos de NumPy los podes indexar y rebanar como hicimos con las listas.

```python
>>> data = np.array([1, 2, 3])
```


```python
>>> data[1]
2
>>> data[0:2]
array([1, 2])
>>> data[1:]
array([2, 3])
>>> data[-2:]
array([2, 3])
```

Lo podés visualizar así:

![./np_indexing.png](./np_indexing.png)

Otra operación muy útil es seleccionar los elementos que cumplen cierta condición. Por ejemplo, si comenzás con un arreglo así:

```python
>>> a = np.array([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])
```

Podés imprimir todos los valores menores que cinco.

```python
>>> print(a[a < 5])
[1 2 3 4]
```

También podés seleccionar, por ejemplo, aquellos elementos mayores o iguales que 5 y usar el resultado para indexar el arreglo.

```python
>>> five_up = (a >= 5)
>>> print(a[five_up])
[ 5  6  7  8  9 10 11 12]
```

Es interesante que `five_up` da un vectore de valores booleanos. `True` si satisface la condición y `False` si no la satisface.

Podés seleccionar los elementos pares:

```python
>>> divisible_by_2 = a[a%2==0]
>>> print(divisible_by_2)
[ 2  4  6  8 10 12]
```


Usando los operadores lógicos `&` y `|` podés combinar dos o más condiciones.

Ya sea para seleccionar elementos directamente:
```python
>>> c = a[(a > 2) & (a < 11)]
>>> print(c)
[ 3  4  5  6  7  8  9 10]
```

o para definir una nueva variable booleana:
```python
>>> five_up = (a > 5) | (a == 5)
>>> print(five_up)
[[False False False False]
 [ True  True  True  True]
 [ True  True  True True]]
```

Finalmente, podés suar `np.nonzero()` para obtener las coordenadas de ciertos elementos de un arreglo.

Si empezamos con este arreglo:

```python
>>> a = np.array([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])
```

Podés usar `np.nonzero()` para imprimir los índices de los elementos que son, digamos, menores que 5:

```python
>>> b = np.nonzero(a < 5)
>>> print(b)
(array([0, 0, 0, 0]), array([0, 1, 2, 3]))
```

En este ejemplo, la respuesta es una tupla de arreglos: uno por cada dimensión. El primer arreglo representa las filas de los elementos que satisfacen la condición y el segundo sus columnas.

Si querés generar la lista de coordenadas donde se encuetran estos elementos, podés zipear los arreglos, convertir el resultado a una lista e imprimir la lista:

```python
>>> list_of_coordinates= list(zip(b[0], b[1]))
```

Surge naturalmente la pregunta: ¿porqué tengo que convertir el objeto `zip` a una lista? Vermos en la segunda mitad de la materia más detalles sobre _generadores_ en Python para entender exactamente lo que está pasando aquí. Simplemente digamos que al zipear `b[0]` y `b[1]` no se genera la lista realmente, sino potencialmente. Sólo al solicitar sus elementos (iterando sobre ello o con `list`) se generan realmente las coordenadas.

```python
>>> for coord in list_of_coordinates:
...     print(coord)
(0, 0)
(0, 1)
(0, 2)
(0, 3)
```


Podés usar `np.nonzero()` para imprimir o seleccionar los elementos del arreglo que son menores que 5:

```python
>>> print(a[b])
[1 2 3 4]
```


Si la condición que ponés no la satiface ningún elemento del arreglo entonces el arreglo de indices que obtenés con `np.nonzero()` será vacío. Por ejemplo:

```python
>>> not_there = np.nonzero(a == 42)
>>> print(not_there)
(array([], dtype=int64), array([], dtype=int64))
```


## Crear arreglos usando datos existentes

Es sencillo crear un nuevo arreglo usando una sección de otro arreglo.

Suponete que tenés este:

```python
>>> a = np.array([1,  2,  3,  4,  5,  6,  7,  8,  9, 10])
```

Podés crear otro arreglo a partir de una sección de `a`, simplemente especificando qué parte querés.

```python
>>> arr1 = a[3:8]
>>> arr1
array([4, 5, 6, 7, 8])
```

Es importante saber que este método genera una _vista_ del arreglo original y no una verdadera copia. Si modificás un elemento de la vista, ¡también se modificará en el original!

```python
>>> arr1[0] = 44
>>> print(a)
[ 1  2  3 44  5  6  7  8  9 10]
```

El concepto de _vista_ es importante para entender lo que está pasando. Las operaciones más frecuentes devuelven vistas y no copias. Esto ahorra memoria y es más veloz, pero si no lo sabés puede traerte problemas.

Veamos este ejemplo:

```python
>>> a = np.array([[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12]])
```

Ahora creamos `b1` a partir de una rebanada de `a` y modificamos su primer elemento. ¡Esto va a modificar el elemento correspondiente de `a` también!

```python
>>> b1 = a[0, :]
>>> b1
array([1, 2, 3, 4])
>>> b1[0] = 99
>>> b1
array([99,  2,  3,  4])
>>> a
array([[99,  2,  3,  4],
 [ 5,  6,  7,  8],
 [ 9, 10, 11, 12]])
```

Podés usar el método `copy` para copiar los datos (una copia profunda). Por ejemplo method will make a complete copy of the array and its data (a _deep copy_). To use this on your array, you could run:

```python
>>> b2 = a[1, :].copy()
>>> b2
array([5, 6, 7, 8])
>>> b2[0] = 95
>>> b2
array([95,  6,  7,  8])
>>> a #no se modifica el 5!
array([[99,  2,  3,  4],
 [ 5,  6,  7,  8],
 [ 9, 10, 11, 12]])
```



## Operaciones básicas sobre arreglos

Una vez que sabés crear arreglos podés empezar a trabajar con ellos. Imaginemos que tenés dos arreglos, uno llamados “data” y otro llamado “ones”.

![./np_array_dataones.png](./np_array_dataones.png)

Podés sumarlos con el signo más.

```python
>>> data = np.array([1, 2])
>>> ones = np.ones(2, dtype=int)
>>> data + ones
array([2, 3])
```


![./np_data_plus_ones.png](./np_data_plus_ones.png)

Obviamente, podés hacer otras operaciones.

```python
>>> data - ones
array([0, 1])
>>> data * data
array([1, 4])
>>> data / data
array([1., 1.])
```


![./np_sub_mult_divide.png](./np_sub_mult_divide.png)

Estas operaciones básicas son simples con NumPy. Si queŕes calcular la suma de los elementos del arreglo, podés usar `sum()`. Esto funciona para vectores, matrices y arreglos de dimensión más alta también.

```python
>>> a = np.array([1, 2, 3, 4])
```


```python
>>> a.sum()
10
```

Para sumar los valores por fila o por columna en una matriz, simplemente tenés que especificar el eje sobre el que se hará la suma.

Si tenés la matriz:

```python
>>> b = np.array([[1, 1], [2, 2]])
```

podés sumar los datos de cada columna con:

```python
>>> b.sum(axis=0)
array([3, 3])
```

y los datos de cada fila usando:

```python
>>> b.sum(axis=1)
array([2, 4])
```



## Broadcasting

Hay veces en que necesitás realizar una operación entre un arreglo y un número (en matemática le decimos, un _escalar_). Por ejemplo tenés un vector con distancias en millas (lo llamamos "data") y lo necesitás convertir a distancias en kilómetros. Podés hacer esta operación así:

```python
>>> data = np.array([1.0, 2.0])
>>> data * 1.6
array([1.6, 3.2])
```


![./np_multiply_broadcasting.png](./np_multiply_broadcasting.png)

NumPy entiende que la multiplicación debe ocurrir en cada celda del vector. Este concepto se llama **broadcasting**. El mecanismo de broadcasting le permite a NumPy relizar operaicones en arreglos de diferente tamaño, pero los tamaños deben ser compatibles. Por ejemplo si ambos arreglos tienen el mismo tamaño o si uno tiene tamaño 1 (escalar). Si los tamaños no son compatibles, te va a dar un `ValueError`.


## Operaciones un poco más complejas

NumPy también te permite realizar operaciones que resumen los datos. Además de  `min`, `max`, y `sum`, podés usar  `mean` para obtener el promedio, `prod` para calcular el producto, `std` paraq obtener el desvío estándar de los datos, y más.

```python
>>> data.max()
2.0
>>> data.min()
1.0
>>> data.sum()
3.0
```


![./np_aggregation.png](./np_aggregation.png)

Supongamos que tenemos un arreglo, llamado “a”

```python
>>> a = np.array([[0.45053314, 0.17296777, 0.34376245, 0.5510652],
...               [0.54627315, 0.05093587, 0.40067661, 0.55645993],
...               [0.12697628, 0.82485143, 0.26590556, 0.56917101]])
```

Es usual juntar los datos por fila o por columna. Si no lo aclarás, NumPy junta los datos de todo el arreglo. Para encontrar la suma o el mínimo del  arreglo, usá:

```python
>>> a.sum()
4.8595784
```

O:

```python
>>> a.min()
0.05093587
```

Podés especificar sobre qué eje querés juntar los datos. Por ejemplo, para calcular el mínimo de cada columna especificás `axis=0`.

```python
>>> a.min(axis=0)
array([0.12697628, 0.05093587, 0.26590556, 0.5510652 ])
```


Son cuatro valores, porque la matriz tiene cuatro columnas. 


## Crear matrices

Podés usar listas de listas para crear arreglos bidimensionales (matrices).

```python
>>> data = np.array([[1, 2], [3, 4]])
>>> data
array([[1, 2],
 [3, 4]])
```


![./np_create_matrix.png](./np_create_matrix.png)

Las técnicas de indexación y rebanadas son muy útiles para manipular matrices:

```python
>>> data[0, 1]
2
>>> data[1:3]
array([[3, 4]])
>>> data[0:2, 0]
array([1, 3])
```


![./np_matrix_indexing.png](./np_matrix_indexing.png)

Podés juntar los datos de matrices como lo hicimos con vectores:

```python
>>> data.max()
4
>>> data.min()
1
>>> data.sum()
10
```


![./np_matrix_aggregation.png](./np_matrix_aggregation.png)

Podés juntar todos, o hacelo por fila o por columna usando el parámetro  `axis`:

```python
>>> data.max(axis=0)
array([3, 4])
>>> data.max(axis=1)
array([2, 4])
```


![./np_matrix_aggregation_row.png](./np_matrix_aggregation_row.png)

Una vez que tenés tus matrices creadas, podés hacer artimética con pares de matrices del mismo tamaño.

```python
>>> data = np.array([[1, 2], [3, 4]])
>>> ones = np.array([[1, 1], [1, 1]])
>>> data + ones
array([[2, 3],
 [4, 5]])
```


![./np_matrix_arithmetic.png](./np_matrix_arithmetic.png)

También con matrices de tamaños diferentes, pero solo si una de ellas tiene una sola fila o una sola columna. En este caso, NumPy v a a usar las reglas de _broadcast_ para la operación.

```python
>>> data = np.array([[1, 2], [3, 4], [5, 6]])
>>> ones_row = np.array([[1, 1]])
>>> data + ones_row
array([[2, 3],
 [4, 5],
 [6, 7]])
```


![./np_matrix_broadcasting.png](./np_matrix_broadcasting.png)

Tené en cuenta que cuando  NumPy imprime arreglos n-dimensionales, el último eje se itera más rápido y el primer más lento. Por ejemplo:

```python
>>> np.ones((4, 3, 2))
array([[[1., 1.],
 [1., 1.],
 [1., 1.]],

 [[1., 1.],
 [1., 1.],
 [1., 1.]],

 [[1., 1.],
 [1., 1.],
 [1., 1.]],

 [[1., 1.],
 [1., 1.],
 [1., 1.]]])
```

Es frecuente que querramos inicializar los valores de una matriz. NumPy ofrece las funciones `ones()` y `zeros()`, así como también la clase `random.Generator` que genera número aleatorios. Solo hay que pasarle la cantidad de elementos que queremos generar:

```python
>>> np.ones(3)
array([1., 1., 1.])
>>> np.zeros(3)
array([0., 0., 0.])
# the simplest way to generate random numbers
>>> rng = np.random.default_rng(0)
>>> rng.random(3)
array([0.63696169, 0.26978671, 0.04097352])
```


![./np_ones_zeros_random.png](./np_ones_zeros_random.png)

También podés usar  `ones()`, `zeros()`, and `random()` para crear matrices si le pasás una tupla describiendo la forma de la matriz:

```python
>>> np.ones((3, 2))
array([[1., 1.],
 [1., 1.],
 [1., 1.]])
>>> np.zeros((3, 2))
array([[0., 0.],
 [0., 0.],
 [0., 0.]])
>>> rng.random((3, 2))
array([[0.01652764, 0.81327024],
 [0.91275558, 0.60663578],
 [0.72949656, 0.54362499]])  # may vary
```


![./np_ones_zeros_matrix.png](./np_ones_zeros_matrix.png)


Esta idea se generaliza a dimensiones más altas.

## Fórmulas matemáticas

La facilidad para implementar fórmulas matemáticas sobre un arreglo es una de las características de NumPy que lo hacen tan ampliamente usado en la comunidad científica de Python.

Por ejemplo, esta es la fórmula del error cuadrático medio:

![./np_MSE_formula.png](./np_MSE_formula.png)

Implementar esta fórmula es simple y directo con NumPy:

![./np_MSE_implementation.png](./np_MSE_implementation.png)

Lo genial de esta abstracción es que `predictions` y `labels` puede tener uno o mil valores. Solo tiene que tener el mismo tamaño para que todo funcione.

Lo podés visulalizar así:

![./np_mse_viz1.png](./np_mse_viz1.png)

En este ejemplo, tanto las predicciones como las etiquetas tienen tres valores. Es decir `n` vale tres. Luego de hacer la resta los valores se elevan al cuadrado. Luego NumPy suma los valores y el resultado es el error de esa predicción y puede usarse como un _puntaje_ que mide la calidad del modelo que predice.

![./np_mse_viz2.png](./np_mse_viz2.png) ![./np_MSE_explanation2.png](./np_MSE_explanation2.png)

## How to save and load NumPy objects

You will, at some point, want to save your arrays to disk and load them back without having to re-run the code. Fortunately, there are several ways to save and load objects with NumPy. The ndarray objects can be saved to and loaded from the disk files with `loadtxt` and `savetxt` functions that handle normal text files, `load` and `save` functions that handle NumPy binary files with a **.npy** file extension, and a `savez` function that handles NumPy files with a **.npz** file extension.

The **.npy** and **.npz** files store data, shape, dtype, and other information required to reconstruct the ndarray in a way that allows the array to be correctly retrieved, even when the file is on another machine with different architecture.

If you want to store a single ndarray object, store it as a .npy file using `np.save`. If you want to store more than one ndarray object in a single file, save it as a .npz file using `np.savez`. You can also save several arrays into a single file in compressed npz format with `savez_compressed`.

It’s easy to save and load and array with `np.save()`. Just make sure to specify the array you want to save and a file name. For example, if you create this array:

```python
>>> a = np.array([1, 2, 3, 4, 5, 6])
```


You can save it as “filename.npy” with:

```python
>>> np.save('filename', a)
```


You can use `np.load()` to reconstruct your array.

```python
>>> b = np.load('filename.npy')
```


If you want to check your array, you can run::

```python
>>> print(b)
[1 2 3 4 5 6]
```


You can save a NumPy array as a plain text file like a **.csv** or **.txt** file with `np.savetxt`.

For example, if you create this array:

```python
>>> csv_arr = np.array([1, 2, 3, 4, 5, 6, 7, 8])
```


You can easily save it as a .csv file with the name “new_file.csv” like this:

```python
>>> np.savetxt('new_file.csv', csv_arr)
```


You can quickly and easily load your saved text file using `loadtxt()`:

```python
>>> np.loadtxt('new_file.csv')
array([1., 2., 3., 4., 5., 6., 7., 8.])
```


The `savetxt()` and `loadtxt()` functions accept additional optional parameters such as header, footer, and delimiter. While text files can be easier for sharing, .npy and .npz files are smaller and faster to read. If you need more sophisticated handling of your text file (for example, if you need to work with lines that contain missing values), you will want to use the `genfromtxt` function.

With `savetxt`, you can specify headers, footers, comments, and more.




[Contenidos](../Contenidos.md) \| [Anterior (4 Random+)](04_Random.md) \| [Próximo (6 El album de Figuritas+)](06_Figuritas.md)
