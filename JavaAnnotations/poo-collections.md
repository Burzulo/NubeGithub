
# 📌 Java Collections Framework

- [Java Collections Framework: La Jerarquía](#-jerarquía)
- [Listas: `ArrayList` & `LinkedList`](#-listas)
- [...](#-...)
- [...](#-...)

<br>

## 📂 Jerarquía

El Java Collections Framework es un conjunto de clases e interfaces que permiten almacenar y manipular grupos de objetos de forma DINAMICA, donde su tamaño cambia automáticamente. A diferencia de los arrays, que son estructuras similares pero estaticas.

A nivel de arquitectura, el framework está dividido en dos grandes familias independientes:
  
                        [ Java Collections Framework ]
                                      |
              +-----------------------+-----------------------+
              |                                               |
    [ Interface Collection ]                          [ Interface Map ]
              |                                               |
        +-----+-----+                             +-----------+-----------+
        |           |                             |                       |
      List         Set                         HashMap                 TreeMap
        |           |
     ArrayList  HashSet

<br>

### ✧ Interfaz `Collection`

Es la raíz de la primera gran rama, este define el comportamiento de las colecciones que almacenan elementos individuales.  

En Java, las colecciones se emplean mediante la interfaz `Collection`, que permite implementar una serie de métodos comunes como ser: añadir, eliminar, obtener el tamaño de la colección, etc.

- #### Métodos comunes heredados

  - `add(E e)` añade un elemento

  - `remove(Object o)` elimina un elemento
  - `size()` retorna la cantidad de elementos
  - `clear()` vacía la colección completa

- #### Sus subinterfaces principales

  - `List` (Listas): Permiten elementos duplicados y mantienen un orden posicional. Ejemplo: *ArrayList*.

  - `Set` (Conjuntos): No permiten elementos duplicados y, por lo general, no garantizan un orden específico. Ejemplo: *HashSet*.

<br>

### ✧ Interfaz `Map`

Un mapa representa una colección de pares Clave-Valor (`<K, V>`).  
Su objetivo fundamental es la búsqueda ultra rápida de datos mediante una clave única.

> [!IMPORTANT]  
> `Map` no implementa ni hereda de `Collection`. Es una estructura completamente independiente.

<br>

Reglas de oro de un Map:

- **Claves Únicas**  
No pueden existir dos claves iguales. Si se inserta una clave que ya existe, su valor se sobrescribe.

- **Valores Duplicados**  
Sí están permitidos. Dos claves distintas pueden apuntar al mismo valor.

- **Acceso directo****  
No se usan índices numéricos (0, 1, 2...), se usan la clave para pedir el valor (mapa.get(clave)).  

  <br>

  ### ➙ Comparativa entre ambos

  | Interfaz Raíz |  Tipo de <br> Almacenamiento| ¿Permite Duplicados? | Ejemplo de uso |
  |:--|:--|:--|:--|
  | `Collection` | Elementos simples (`E`)| Depende (`List` sí, `Set` no) | Lista de compras, fila de clientes. |
  | `Map` | Pares llave-valor (`K, V`)| Claves NO, Valores SÍ | Diccionario, ID de usuario. |

<br>

## 📂 Listas

Las listas son un **conjunto de elementos relacionados entre sí** que tienen un determinado **orden**.

Su tamaño es DINÁMICO ya que puede cambiar en el tiempo. Su tamaño en memoria crece o se achica de forma automática a medida que se añaden o eliminan elementos.

En Java existen diferentes tipos de Listas:

- `ArrayList`
- `LinkedList`
- `Stack`

  <br>

  > [!IMPORTANT]  
  > A nivel conceptual y de uso, las tres son "listas" porque permiten almacenar elementos en un orden secuencial.  
  > Pero `Stack` es una estructura especial (y antigua) orientada a comportarse como pila.

<br>

Las listas pueden tener dos tipos de orden:

- **FIFO** (first in first out) el primero en entrar es el primero en salir
- **LIFO** (last in first out) el último en entrar es el primero en salir

<br>

### ✧ ArrayList

Clase que se estructura internamente mediante un array que se redimensiona automáticamente en memoria.

Internamente, un `ArrayList` funciona almacenando sus elementos en posiciones de memoria contiguas a través de un arreglo compacto. Cuando este componente interno se llena por completo, Java gestiona la situación de forma automática creando un nuevo arreglo de mayor capacidad hacia el cual copia todos los registros existentes.

Esta estructura ofrece como principal ventaja un acceso y una velocidad de lectura instantáneos, ya que el sistema puede saltar directamente a cualquier elemento utilizando ÍNDICES reales en memoria.

Su mayor desventaja radica en que las operaciones de inserción o eliminación en posiciones intermedias de la lista resultan muy costosas a nivel de rendimiento, dado que el lenguaje se ve obligado a desplazar físicamente todos los elementos restantes para poder reacomodar los índices de la estructura.

<br>

> [!NOTE]  
> El ORDEN de los registros es el orden en el que fueron insertados. (FIFO)

<br>

Se inicializa:
```java
List < * > nombreLista;  // * se declara qué clase va a guardar la lista

// para AHORRAR CÓDIGO, se puede inicializar la lista en la misma línea
List < * > nombreLista = new ArrayList< * > ();

  nombreLista.add (new Clase_de_lista(parametrosClase));
  // .add para agregar
  // con new creamos un objeto en la misma línea y se ahorra código
  // entre paréntesis van los atributos declarados en la clase (num; nombre; edad)

  // EJEMPLO
  lista.add (new Persona(1, "Gonza", 40));
  lista.add (new Persona(2, "Juan", 21));
  lista.add (new Persona(3, "Pedro", 29));
```

