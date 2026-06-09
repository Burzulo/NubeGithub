# 📌 Abstracción

<br>

- [Clases Abstractas](#-abstraccion)
- ❌ [Métodos Abstractos](#-interfaces)

<br>

## 📂 Abstraccion

La abstracción en POO es el proceso de **identificar y separar las características esenciales de un objeto** de la vida real para representarlas de forma abstracta o lógica en un programa.  
En Java, se logra mediante la creación de clases y la definición de sus atributos y métodos.

### ✧ Clases Abstractas

Es una clase que **NO PUEDE SER INSTANCIADA** directamente, es decir, no se pueden (o deben) crear objetos de esa clase específica.  
Se UTILIZA COMO una **clase base o plantilla** para otras clases relacionadas.

La principal característica de una clase abstracta es que puede tener métodos abstractos.  
Un método abstracto **es abstracto cuando está declarado pero sin su implementación**, es decir, no contiene entre sus «llaves» nada de código.  
En un MÉTODO ABSTRACTO, **sólo se declara su firma, incluyendo el nombre del método y los parámetros que acepta**, nada más que eso, convirtiéndola así en una **clase padre**.

Las clases que heredan de una clase abstracta, llamadas «subclases o clases hijas», deben proporcionar una implementación para todos los métodos abstractos heredados.  
Esto significa que **las subclases deben completar / implementar los métodos abstractos declarados en la clase abstracta**.

<br>

> [!IMPORTANT]  
> Cuando se usan clases abstractas, **una clase no puede heredar de varias clases abstractas a la vez** (como en las interfaces), **solo UNA**.

<br>

Una clase abstracta se utiliza como una abstracción general de la cual se derivan clases más específicas. Proporciona una estructura común y define los métodos abstractos que deben implementarse en las subclases. Esto promueve la reutilización del código y la creación de jerarquías de clases.

Generalmente las clases abstractas indican **«ES/SER»** de un objeto.

### ▫️ Cuando se usan las Clases Abstractas ?

Cuando se desea definir una abstracción que englobe objetos de distintos tipos y se quiere hacer uso del **polimorfismo**.

Ej: un ``círculo`` y un ``cuadrado`` son figuras geométricas, en este caso ``Figura`` es una **clase abstracta** porque no tiene sentido calcular su área, pero sí la de sus hijos (``cuadrado`` y ``círculo``) …

Cuando una clase declara al menos un método abstracto, se debe marcar como abstracta utilizando la palabra clave `abstract`. Una clase abstracta puede tener tanto métodos abstractos como métodos concretos (implementados), pero **si o si debe implementar al menos un método abstracto para considerarse como clase abstracta como tal**.

````java
modificadorAcceso abstract class nombreClase {
    ... 
    modificadorAcceso abstract tipoDato nombreMétodo();   // método abstracto
}

// ejemplo de CLASE ABSTRACTA
public abstract class Figura {
   ... 
   public abstract double calculaArea();
}
````

<br>

> ⚠️ **Importante**  
> Sus niveles de visualización deben ser *public o protected* pero **NUNCA _private_**.

