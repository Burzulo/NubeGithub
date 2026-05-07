# 📌 Relaciones entre Clases

En el paradigma de la Programación Orientada a Objetos, los objetos no operan de forma aislada, sino que colaboran mediante relaciones de distinta intensidad. La **Asociación** es el concepto base que describe cómo un objeto se comunica con otro, mientras que la **Agregación** y la **Composición** son especializaciones que definen la **jerarquía de posesión**.

En el ecosistema de Java, estas distinciones trascienden lo teórico: impactan directamente en la **instanciación**, la visibilidad de los atributos y la gestión del ciclo de vida de los datos en la memoria (Heap). Aunque el *Garbage Collector* gestione la liberación de memoria, es responsabilidad del desarrollador definir mediante el diseño quién 'es dueño' de cada instancia."

<br>

### 🔖 Asociación

Es la relación más básica y general, simplemente significa que un objeto utiliza o interactúa con otro. Es una relación estructural donde los objetos son independientes. En código, suele verse como un objeto pasando por un método o una variable de instancia que puede cambiar.

### ▫️ Ejemplo

````java
// Asociación: El médico atiende al paciente, pero ambos tienen vidas propias.

class Paciente {
  private String nombre;
  // ...
}

class Medico {
  public void atender(Paciente p) { 
      System.out.println("Atendiendo a: " + p.getNombre());
  }
}
````

<br>

### 🔖 Agregación

Es una forma especial de asociación que representa una relación de **"TIENE UN"**.  
Aquí hay un "todo" y sus "partes", pero las partes pueden existir sin el todo. El ciclo de vida de los objetos no está ligado.

### ▫️ Ejemplo

````java
class Motor {
    private String serie;
    public Motor(String serie) { this.serie = serie; }
}

class Auto {
    private Motor motor; // El auto TIENE UN motor

    // El motor se crea fuera y se "agrega" al auto. 
    // Si el auto se destruye, el motor puede seguir existiendo.
    public void setMotor(Motor m) {
        this.motor = m;
    }
}
````

<br>

### 🔖 Composición

Es la forma MAS FUERTE de relación.  
Aquí, el objeto hijo **no tiene sentido** sin el padre. Normalmente, el padre crea al hijo dentro de su propio constructor o métodos privados.

````java
// La parte: No tiene sentido fuera del contexto del Libro

class Pagina {
    private int numero;
    private String contenido;

    public Pagina(int numero, String contenido) {
        this.numero = numero;
        this.contenido = contenido;
    }
}

// El todo: Es el dueño del ciclo de vida de las partes

class Libro {
    private String titulo;
    private final List<Pagina> paginas; // La colección es parte integral del objeto

    public Libro(String titulo, int cantidadPaginas) {
        this.titulo = titulo;
        this.paginas = new ArrayList<>();
        
        // COMPOSICIÓN: El libro CREA sus propias páginas.
        // Las páginas nacen cuando el libro nace.
        for (int i = 1; i <= cantidadPaginas; i++) {
            this.paginas.add(new Pagina(i, "Contenido de la página " + i));
        }
    }
}
````

<br>

### ▫️ Tabla Comparativa

| Concepto | Relación | Ciclo de Vida Independiente |
| :--- | :--- | :--- |
| **Asociación** | **"Usa a"** | Sí |
| **Agregación** | **"Tiene un"** (débil) | Sí |
| **Composición** | **"Es parte de"** (fuerte) | No |