# Taller: Manejo de Excepciones en Java - Sistema de Gestión de Inventario

## Descripción
Este taller está diseñado para profundizar en el manejo de excepciones en Java, utilizando tanto excepciones checked como unchecked en el contexto de un sistema de gestión de inventario para una tienda.

## Objetivos
- Comprender la diferencia entre excepciones checked y unchecked
- Implementar y utilizar excepciones personalizadas
- Practicar el uso de bloques try-catch-finally
- Aplicar el manejo de excepciones en situaciones realistas
- Utilizar la cláusula throws y el bloque throw
- Implementar try-with-resources para manejo eficiente de recursos

## Contenido del Taller

### 1. Excepciones Personalizadas
Crea las siguientes clases de excepciones:
- `StockInsuficienteException.java` (checked)
  - Esta excepción se lanza cuando se intenta reducir el stock de un producto por debajo de cero.
  - Extiende directamente de Exception.
- `ProductoNoEncontradoException.java` (unchecked)
  - Esta excepción se lanza cuando se intenta buscar un producto que no existe en el inventario.
  - Extiende de RuntimeException.

#### Explicación de Excepciones Checked y Unchecked:
- Excepciones Checked:
  - Heredan directamente de la clase Exception (pero no de RuntimeException).
  - El compilador obliga a manejarlas (try-catch) o declararlas (throws).
  - Se usan para condiciones excepcionales recuperables que un programa bien escrito debería anticipar y recuperar.

- Excepciones Unchecked:
  - Heredan de RuntimeException (que a su vez hereda de Exception).
  - El compilador no obliga a manejarlas o declararlas.
  - Se usan para errores de programación o condiciones irrecuperables.

#### ¿Por qué usar RuntimeException para excepciones unchecked?
1. Flexibilidad: No obligan al programador a manejarlas, lo que puede ser útil para errores que no siempre pueden ser manejados de manera significativa en el momento en que ocurren.
2. Menos código repetitivo: Evita la necesidad de añadir cláusulas try-catch o throws en cada método que podría lanzar la excepción.
3. Errores de programación: Muchas veces representan bugs o errores lógicos en el programa que no deberían ocurrir si el código está bien escrito.
4. Propagación automática: Pueden propagarse automáticamente a través de la pila de llamadas sin necesidad de declaración explícita.

En nuestro caso, `ProductoNoEncontradoException` es unchecked porque:
- Representa un error que podría ocurrir debido a un mal uso del sistema (buscar un producto que no existe).
- No siempre es necesario o práctico manejar esta excepción en cada punto donde se busca un producto.
- Permite una mayor flexibilidad en cómo y dónde se maneja este tipo de error en la aplicación.

### 2. Clase Producto
Implementa la clase `Producto.java` con los siguientes elementos:
- Atributos: codigo (String), nombre (String), cantidad (int), precio (double)
- Constructor y métodos getter/setter
- Método `actualizarStock(int cantidad)` que lance `StockInsuficienteException` si la cantidad resultante es negativa

### 3. Clase Inventario
Crea la clase `Inventario.java` que maneje un conjunto de productos:
- Utiliza un array de `Producto` para almacenar hasta 10 productos
- Constructor que inicialice el array con un tamaño específico
- Método `agregarProducto(Producto producto)` que añada un producto al array
  - Debe manejar el caso en que el array esté lleno
- Método `buscarProducto(String codigo)` que lance `ProductoNoEncontradoException` si el producto no existe
- Método `listarProductos()` que muestre todos los productos en el inventario

Ejemplos de implementación:

```java
public class Inventario {
    private Producto[] productos;
    private int cantidadActual;
    private final int CAPACIDAD_MAXIMA;

    public Inventario(int capacidad) {
        CAPACIDAD_MAXIMA = capacidad;
        productos = new Producto[CAPACIDAD_MAXIMA];
        cantidadActual = 0;
    }

    public void agregarProducto(Producto producto) throws Exception {

    }

    public Producto buscarProducto(String codigo) throws ProductoNoEncontradoException {

    }

    // Otros métodos...
}

```

### 4. Clase Principal (SistemaInventario.java)
En el método `main`, demuestra el uso del sistema de inventario:
- Crea una instancia de `Inventario` con un tamaño específico (por ejemplo, 5)
- Agrega varios productos al inventario
- Intenta agregar más productos de los que permite el array para provocar un error
- Busca productos existentes y no existentes
- Actualiza el stock de algunos productos, incluyendo un caso que debería lanzar `StockInsuficienteException`
- Utiliza la clase `RegistroInventario` para guardar y cargar el inventario
- Maneja todas las excepciones posibles con bloques try-catch apropiados
- Implementa al menos un bloque try-catch-finally para demostrar su uso, por ejemplo, al abrir y cerrar un scanner para entrada de usuario

Ejemplo de uso en la clase principal:

```java
public class SistemaInventario {
    public static void main(String[] args) {
        Inventario inventario = new Inventario(5);  // Crea un inventario con capacidad para 5 productos

        // Resto de la implementación...
    }
}
```



## Pistas para el Uso del Array Fijo
- Al crear la instancia de `Inventario`, especifica el tamaño máximo: `Inventario inventario = new Inventario(5);`
- En la clase `Inventario`, usa un contador para llevar la cuenta de cuántos productos se han agregado
- Antes de agregar un nuevo producto, verifica si hay espacio disponible en el array
- Si el array está lleno, puedes lanzar una excepción o simplemente no agregar el producto e informar al usuario

## Instrucciones de Ejecución
1. Implementa todas las clases mencionadas
2. Compila los archivos Java: `javac *.java`
3. Ejecuta el programa principal: `java SistemaInventario`

## Entrega
- Completa todos los ejercicios en el tiempo asignado (2 horas)
- Asegúrate de que tu código esté bien comentado y maneje las excepciones de manera efectiva
- Incluye al menos un ejemplo de uso de try-catch-finally y un ejemplo de try-with-resources

## Evaluación
Se evaluará la correcta implementación de los mecanismos de manejo de excepciones, incluyendo:
- Uso apropiado de try-catch
- Implementación de bloques finally para limpieza de recursos
- Uso de try-with-resources donde sea apropiado
- Claridad del código y capacidad para manejar situaciones de error de manera efectiva y elegante
- Correcta implementación de excepciones personalizadas
- Manejo adecuado de excepciones en la clase principal y en métodos que propagan excepciones
