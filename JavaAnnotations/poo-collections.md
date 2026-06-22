
# 📌 Java Collections Framework

- [Java Collections Framework: La Jerarquía](#-jerarquía)
- [Listas: `ArrayList` & `LinkedList`](#-listas)
- [Conjuntos: `HashSet`, `LinkedHashSet` y `TreeSet`](#-set-conjuntos)
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

Para recorrerlo hay dos formas:

- **For tradicional**, recorriendolo por índice.
- **Foreach**

<br>

### ✧ LinkedList

Clase que se estructura internamente como una lista doblemente enlazada, donde sus elementos no se almacenan en ubicaciones contiguas de memoria.

Internamente, una `LinkedList` funciona mediante componentes independientes llamados **nodos**. Cada nodo actúa como un contenedor que resguarda el objeto real (el dato) y mantiene activas dos referencias o punteros directos: uno orientado hacia el nodo anterior y otro hacia el nodo siguiente.

El flujo de la estructura se gestiona a través de un nodo inicial denominado cabeza y un nodo de cierre llamado cola.

La principal ventaja es una eficiencia absoluta al momento de insertar o eliminar elementos en cualquier posición de la lista. Java ejecuta estas acciones de forma instantánea debido a que no necesita desplazar bloques de datos en la memoria RAM, sino que se limita a reconfigurar los punteros de los nodos adyacentes para enlazar el nuevo elemento.

Su mayor desventaja se encuentra en la velocidad de lectura y acceso aleatorio. Al no contar con índices físicos indexados en memoria, el sistema no puede saltar directamente a una posición específica; para recuperar un dato intermedio, se recorre secuencialmente la cadena de nodos, uno por uno, desde el inicio o el final hasta alcanzar el destino.

<br>

```java
// Linked List

  [null] ← [ 2 ] ⇆ [ 23 ] ⇆ [ a ] ⇆ [ dd ] ⇆ [ 7a ] → [null]  
          cabeza                              cola
```

> [!NOTE]
> Mantiene estrictamente el ORDEN de inserción de los elementos. (FIFO)

<br>

Se inicializa al igual que ArrayList, solo cambia el tipo:

```java
LinkedList < * > nombreLista = new LinkedList<> ();
// * se declara dentro de qué clase va a guardar la lista
```

Para recorrerlo se usa el foreach, ya que no posee un índice sino que hay que ir registro por registro.

<br>

La `LinkedList` proporciona métodos para agregar, eliminar y acceder a elementos en la lista. Por ejemplo, se pueden agregar elementos al principio o al final de la lista utilizando los métodos `addFirst()` y `addLast()`. También eliminar elementos con los métodos `removeFirst()` y `removeLast()`. Además, es posible siempre acceder a elementos individuales utilizando el método `get()` o recorrer la lista utilizando un iterador o un foreach. Por lo tanto puede ser tratada como «pila» o «cola».

```java
// .add() para agregar elementos secuenciales
lista.add (new Persona(1, "Gonza", 40));

// métodos para manipular los extremos de la estructura al instante
lista.addFirst(new Persona(9, "Ana", 30));  // Inserta directamente en la cabeza
lista.addLast(new Persona(10, "Luis", 25)); // Inserta directamente en la cola
```

<br>

`LinkedList` tambien permite poner un REGISTRO al principio de la lista, se debe poner `“0”` (cero). Esto permite que el registro al momento de recorrerlo salga en primer lugar.

```java
// Permite agregar un registro al principio de la lista usando el índice "0"
lista.add (new Persona(1, "Gonza", 40));
lista.add (new Persona(2, "Juan", 21));
lista.add (0, new Persona (5, "Gon", 40));
lista.add (new Persona(3, "Pedro", 29));
```

<br>

### ⇒ Métodos compartidos

Tanto `ArrayList` como `LinkedList` comparten estas funciones esenciales para manipular y consultar los datos de la lista.

1. **Conocer el Estado de la Lista**

   Para gestionar el flujo de la aplicación, es necesario saber cuántos elementos hay o si la lista está vacía antes de recorrerla.

    - `size()` retorna un entero (int) con la cantidad exacta de elementos. Permite conocer el TAMAÑO de la lista.
    - `isEmpty()` devuelve true si la lista no tiene nada adentro, o false si tiene al menos un registro. Permite comprobar si la LISTA está VACÍA.

      ```java
      // Ejemplo de consulta
      System.out.println("Cantidad de personas: " + lista.size());
    
      if (lista.isEmpty()) {
          System.out.println("La lista está vacía, no se puede procesar.");
      }
      ```

<br>

2. **Eliminar Elementos**

   Java permite borrar un registro específico o limpiar la estructura completa de un solo golpe.

    - `remove(index)` elimina el elemento de esa posición. En un ArrayList, los elementos siguientes se mueven automáticamente hacia atrás para reajustar los índices.
    - `clear()` borra absolutamente TODOS los elementos, dejando la lista en cero.

      ```java
      // Eliminar al elemento en la posición 1
      lista.remove(1); 
      
      // Vaciar la lista por completo
      lista.clear(); 
      System.out.println(lista.isEmpty()); // Devuelve: true
      ```

<br>

3. **Método `toString()`**

   Cuando se extrae un objeto de la lista para mostrarlo por consola, se necesita que sea legible.

   Si se intenta imprimir un objeto directamente de la lista, Java no sabe cómo mostrarlo e imprimirá su dirección de memoria física en el Heap (ejemplo: Persona@6dbb2234). Para solucionar esto, se debe ir a la clase molde (`Persona`) y sobrescribir el método `toString()`.

   ```java
   // En la clase Persona
   ...
   @Override
   public String toString() {
       return "Persona [ID=" + id + ", Nombre=" + nombre + ", Edad=" + edad + "]";
   }
  
   // En el Main
   // Al tener toString(), esto imprimirá los datos reales y no la memoria
   System.out.println(lista.get(0).toString());
   ```

<br>

### - Cual elegir ?

Para decidir cuál implementación de `List` usar en el día a día, la regla general en el desarrollo de software es muy simple: por defecto, usar siempre `ArrayList`.  
Solo cambiar a `LinkedList` en escenarios muy específicos de rendimiento.

Elegir `ArrayList` cuando la aplicación necesita buscar, leer o consultar información constantemente y la mayoría de las inserciones se hacen al final de la cola. Un ejemplo real es un catálogo de productos en una aplicación web o la lista de órdenes del día en un panel logístico; los datos se cargan una vez (o se añaden al final) y los usuarios pasan todo el día consultando, buscando o filtrando esos registros mediante sus índices, lo cual es instantáneo en memoria contigua.

Por el contrario, elegir `LinkedList` únicamente cuando el sistema va a estar insertando o eliminando datos de forma masiva y continua en el medio o al principio de la estructura. Un caso real es la gestión de una fila de prioridades críticas en una terminal de carga (donde constantemente se cuelan camiones de alta prioridad al inicio de la fila o se cancelan turnos intermedios); aquí se cambia la lectura rápida por la capacidad de alterar el orden de los elementos al instante sin sobrecargar el servidor reorganizando posiciones en la memoria.

<br>

> [!TIP]  
> En el 95% de los proyectos reales se usa `ArrayList` porque la lectura es la operación más común y consume mucha menos memoria RAM que los nodos enlazados de una `LinkedList`.

<br>

## 📂 Set (Conjuntos)

La interfaz `Set` representa una colección de elementos individuales que NO PERMITE elementos duplicados. A diferencia de las listas, los conjuntos no se basan en un índice numérico posicional, sino en las propiedades matemáticas de los elementos para asegurar su UNICIDAD.

En Java existen tres implementaciones principales de `Set`, cada una orientada a un comportamiento específico en memoria:

<br>

### ✧ HashSet

Clase que se estructura internamente mediante una tabla Hash, lo que la convierte en la opción más rápida del framework para buscar, agregar o eliminar elementos.

`HashSet` utiliza el código Hash del objeto (`hashCode()`) para determinar su ubicación exacta en memoria. Esta implementación ofrece como principal ventaja un rendimiento insuperable de tiempo constante para las operaciones básicas.

Sin embargo, su mayor desventaja radica en que no garantiza ningún orden para sus elementos; al recorrer un `HashSet`, el orden de salida puede ser completamente caótico y diferente al orden en el que se insertaron los datos.

```java
// Inicialización estándar
Set<String> paises = new HashSet<>();

// .add() para agregar elementos
paises.add("Argentina");
paises.add("España");
paises.add("Argentina"); // Java ignora silenciosamente este duplicado

System.out.println(paises); // Output: [España, Argentina] (Sin orden fijo)
```

<br>

### ✧ LinkedHashSet

Clase que combina una tabla Hash con una lista doblemente enlazada para mantener un registro de las inserciones.

Internamente, funciona de manera idéntica a `HashSet` para garantizar que no existan duplicados, pero añade punteros entre sus elementos para recordar la secuencia de entrada.

Su principal ventaja es que mantiene estrictamente el ORDEN de inserción de los elementos al momento de recorrerlos.

por el contrario, su única desventaja frente a `HashSet` es un consumo de memoria ligeramente superior debido a la necesidad de almacenar las referencias de los enlaces.

```java
Set<String> nombres = new LinkedHashSet<>();

nombres.add("Gonza");
nombres.add("Juan");
nombres.add("Ana");

// Mantiene exactamente el orden en el que entraron
System.out.println(nombres); // Output: [Gonza, Juan, Ana]
```

<br>

### ✧ TreeSet

Clase que se estructura mediante un «Red-Black Tree», orientada exclusivamente al ORDENAMIENTO AUTOMÁTICO de datos.

Internamente, cada vez que se añade un elemento, la estructura lo evalúa y lo posiciona en su lugar correspondiente según su orden natural o un criterio personalizado.

La principal ventaja de `TreeSet` es que mantiene los elementos ordenados automáticamente (de forma alfabética para textos o ascendente para números). Sin embargo, su mayor desventaja es que el rendimiento es notablemente más lento en comparación con las otras implementaciones, ya que requiere rebalancear el árbol con cada inserción o eliminación.

```java
Set<Integer> numeros = new TreeSet<>();

numeros.add(50);
numeros.add(10);
numeros.add(35);

// Se ordenan de forma natural de menor a mayor automáticamente
System.out.println(numeros); // Output: [10, 35, 50]
```

<br>

> [!IMPORTANT]  
> **¿Cómo sabe Java si un objeto está duplicado?**  
> Para tipos de datos nativos como `String` o `Integer`, Java ya sabe cómo compararlos. Pero si se van a guardar objetos de las propias clases (ej. `Set<Persona>`), es obligatorio sobrescribir los métodos `equals()` y `hashCode()` en la clase `Persona`. Si no se hace, Java comparará las direcciones de memoria y permitirá registrar dos personas con los mismos datos.

<br>

### - Cual elegir ?

Para elegir qué implementación de `Set` usar en la vida real, la regla es muy directa porque cada una resuelve un problema de ordenamiento totalmente distinto. Por defecto, si solo importa la velocidad y borrar duplicados, usar siempre `HashSet`.

Elegir `HashSet` cuando la única prioridad es la velocidad absoluta para verificar si algo ya existe o para eliminar duplicados, sin importar en absoluto el orden de los elementos. Un caso real es el control de acceso en una terminal de carga: necesitas validar instantáneamente si el ID de un chofer que acaba de llegar está en la lista de personal autorizado. No te importa quién llegó primero ni el orden alfabético, solo necesitas que la consulta tarde millonésimas de segundo entre miles de registros.

Elegir `LinkedHashSet` cuando se necesita garantizar que no haya duplicados pero es indispensable recordar el orden exacto en el que llegaron los datos. Un ejemplo real es un historial de las últimas 10 direcciones de entrega buscadas por un cliente en una aplicación de despacho; necesitas que las direcciones sean únicas (no repetir la misma casa dos veces), pero quieres mostrarlas en pantalla ordenadas exactamente desde la más reciente hasta la más antigua.

Elegir `TreeSet` únicamente cuando se necesita que los elementos se mantengan ordenados de forma automática (alfabética o numéricamente) en todo momento, asumiendo un costo mayor de procesamiento. Un escenario real es un monitor de asignación de turnos o un listado de choferes disponibles ordenados alfabéticamente por su apellido; cada vez que un chofer se da de alta, el sistema lo inserta en la posición alfabética exacta automáticamente, ahorrándo el trabajo de ordenar la colección manualmente después.

<br>

> [!TIP]  
> En producción, `HashSet` es el rey absoluto de los conjuntos debido a su velocidad implacable. El costo de memoria extra de `LinkedHashSet` o el costo de procesamiento de `TreeSet` solo es necesario si el negocio exige un orden específico.

<br>

