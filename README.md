# Patrón de diseño: Null Object

El patrón de diseño Null Object propone utilizar un objeto especial que cumpla con el tipo de objeto que se desea retornar para cuando el objeto buscado no exista, pero con la particularidad de que este objeto especial tenga todos su métodos vacíos. Esto se hace para evitar tener que verificar que el valor devuelto por el método sea un objeto o un nulo, dado que si es un nulo puede ocasionar un error en tiempo de ejecución *NullReferenceException*.  

## Estructura

![](https://reactiveprogramming.io/public/books/patterns/img/patterns-articles/null-object-diagram.png)

Los componentes que conforman este patrón son los siguientes:

1. **Client:** Clase que utiliza las instancias que pueden ser afectado por un objeto nulo. 
2. **AbstractObject:** Clase que implmenta el comportamiento que debe utilizar tanto los objetos reales y nulos.
3. **ConcreteObject:** Clase que representa al objeto real que será creado siempre y cuando el objeto buscado exista.
4. **NullObject:** Clase que representa al objeto nulo, donde sus métodos serán vacíos para evitar regresar referencias nulas. Será creado únicamente cuando el objeto buscado no exista. 

## Diagrama de secuencias

![](https://reactiveprogramming.io/public/books/patterns/img/patterns-articles/null-object-sequence.png)

1. El *Client* intenta buscar un objeto determinado.
2. El *ObjectLookup* busca si el objeto solicitado existe.
3. Si el objeto solicitado no existe, entonces regresará una instancia de *NullObject*.
4. En caso de que el objeto solicitado existe, se devolverá una instancia de *ConcreteObject*.
5. Al final se regresará al *Client* cualquiera de las dos instancias (*NullObject* o *ConcreteObject*), sin embargo, éste nunca obentendrá una referencia nula en caso de no encontrar el objeto.
