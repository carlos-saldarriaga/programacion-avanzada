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


# Ejemplos de Manejo de Excepciones en Java

## 1. Excepciones Checked vs Unchecked

### Ejemplo de Excepción Checked
```java
// Definición de una excepción checked personalizada
public class ArchivoNoEncontradoException extends Exception {
    public ArchivoNoEncontradoException(String mensaje) {
        super(mensaje);
    }
}

// Uso de la excepción checked
public class LectorArchivos {
    // El método declara que puede lanzar una excepción checked
    public String leerContenido(String ruta) throws ArchivoNoEncontradoException {
        if (!existeArchivo(ruta)) {
            throw new ArchivoNoEncontradoException("El archivo en la ruta " + ruta + " no existe.");
        }
        // Lógica para leer el archivo
        return "Contenido del archivo";
    }
    
    private boolean existeArchivo(String ruta) {
        // Lógica para verificar si existe el archivo
        return false; // Simulamos que no existe
    }
}

// Ejemplo de uso y manejo obligatorio
public class EjemploChecked {
    public static void main(String[] args) {
        LectorArchivos lector = new LectorArchivos();
        
        try {
            String contenido = lector.leerContenido("datos.txt");
            System.out.println(contenido);
        } catch (ArchivoNoEncontradoException e) {
            System.err.println("Error: " + e.getMessage());
            // Realizar acciones de recuperación
        }
    }
}
```

### Ejemplo de Excepción Unchecked
```java
// Definición de una excepción unchecked personalizada
public class FormatoInvalidoException extends RuntimeException {
    public FormatoInvalidoException(String mensaje) {
        super(mensaje);
    }
}

// Uso de la excepción unchecked
public class ValidadorDatos {
    // El método no necesita declarar que lanza la excepción
    public void validarFormato(String dato) {
        if (dato == null || dato.isEmpty()) {
            throw new FormatoInvalidoException("El dato no puede estar vacío");
        }
        
        if (!dato.matches("[0-9]+")) {
            throw new FormatoInvalidoException("El dato debe contener solo números");
        }
    }
}

// Ejemplo de uso (el manejo es opcional)
public class EjemploUnchecked {
    public static void main(String[] args) {
        ValidadorDatos validador = new ValidadorDatos();
        
        // Opción 1: Sin try-catch (la excepción se propagará y terminará el programa)
        // validador.validarFormato("abc123");
        
        // Opción 2: Con try-catch (manejo explícito)
        try {
            validador.validarFormato("abc123");
        } catch (FormatoInvalidoException e) {
            System.err.println("Error de formato: " + e.getMessage());
            // Realizar acciones de recuperación
        }
    }
}
```

## 2. Try-Catch-Finally

```java
import java.util.Scanner;

public class EjemploTryCatchFinally {
    public static void main(String[] args) {
        Scanner scanner = null;
        
        try {
            scanner = new Scanner(System.in);
            System.out.print("Ingrese un número: ");
            int numero = scanner.nextInt();
            System.out.println("El número ingresado es: " + numero);
            
            // Simulamos un posible error
            int resultado = 100 / numero;
            System.out.println("100 dividido por " + numero + " es: " + resultado);
            
        } catch (ArithmeticException e) {
            System.err.println("Error aritmético: " + e.getMessage());
            System.err.println("No se puede dividir por cero");
            
        } catch (Exception e) {
            System.err.println("Error inesperado: " + e.getMessage());
            
        } finally {
            System.out.println("Bloque finally: Este código siempre se ejecuta");
            
            // Cerrar recursos en el bloque finally
            if (scanner != null) {
                scanner.close();
                System.out.println("Scanner cerrado correctamente");
            }
        }
        
        System.out.println("Programa finalizado");
    }
}
```

## 3. Try-With-Resources

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class EjemploTryWithResources {
    public static void main(String[] args) {
        // Forma tradicional (pre-Java 7)
        BufferedReader lectorTradicional = null;
        try {
            lectorTradicional = new BufferedReader(new FileReader("archivos/datos.txt"));
            String linea = lectorTradicional.readLine();
            System.out.println("Primera línea: " + linea);
        } catch (IOException e) {
            System.err.println("Error al leer el archivo: " + e.getMessage());
        } finally {
            try {
                if (lectorTradicional != null) {
                    lectorTradicional.close();
                }
            } catch (IOException e) {
                System.err.println("Error al cerrar el lector: " + e.getMessage());
            }
        }
        
        // Forma moderna con try-with-resources (Java 7+)
        try (BufferedReader lectorModerno = new BufferedReader(new FileReader("archivos/datos.txt"))) {
            String linea = lectorModerno.readLine();
            System.out.println("Primera línea: " + linea);
        } catch (IOException e) {
            System.err.println("Error al leer el archivo: " + e.getMessage());
            // No es necesario cerrar el recurso, se cierra automáticamente
        }
    }
}
```

## 4. Propagación de Excepciones con Throws

```java
import java.io.FileInputStream;
import java.io.IOException;

public class EjemploPropagacionExcepciones {
    
    // Este método propaga la excepción IOException al llamador
    public static void leerArchivo(String ruta) throws IOException {
        FileInputStream fis = new FileInputStream(ruta);
        
        byte[] datos = new byte[100];
        fis.read(datos);
        
        fis.close();
        
        System.out.println("Archivo leído correctamente");
    }
    
    // Este método maneja la excepción internamente
    public static void leerArchivoSeguro(String ruta) {
        try {
            leerArchivo(ruta);
        } catch (IOException e) {
            System.err.println("Error controlado: " + e.getMessage());
        }
    }
    
    public static void main(String[] args) {
        // Forma 1: Manejar la excepción propagada
        try {
            leerArchivo("archivo_inexistente.txt");
        } catch (IOException e) {
            System.err.println("Error al leer el archivo: " + e.getMessage());
        }
        
        // Forma 2: Llamar a un método que maneja internamente la excepción
        leerArchivoSeguro("archivo_inexistente.txt");
    }
}
```

## 5. Captura de Múltiples Excepciones

```java
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.util.Scanner;

public class EjemploMultiplesExcepciones {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        try {
            // Posible NumberFormatException
            System.out.print("Ingrese un número: ");
            String entrada = scanner.nextLine();
            int numero = Integer.parseInt(entrada);
            
            // Posible FileNotFoundException
            FileInputStream fis = new FileInputStream("datos.txt");
            
            // Posible ArithmeticException
            int resultado = 100 / numero;
            System.out.println("Resultado de 100/" + numero + " = " + resultado);
            
            // Posible IOException
            fis.read();
            fis.close();
            
        } catch (NumberFormatException e) {
            System.err.println("Error: Debe ingresar un número válido.");
            
        } catch (FileNotFoundException e) {
            System.err.println("Error: No se encontró el archivo.");
            
        } catch (ArithmeticException e) {
            System.err.println("Error: Operación aritmética inválida.");
            
        } catch (IOException e) {
            System.err.println("Error de E/S: " + e.getMessage());
            
        } catch (Exception e) {
            // Captura cualquier otra excepción no contemplada antes
            System.err.println("Error inesperado: " + e.getMessage());
            
        } finally {
            scanner.close();
        }
    }
}
```

## 6. Multicatch (Java 7+)

```java
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

public class EjemploMulticatch {
    public static void main(String[] args) {
        try {
            // Código que puede generar varias excepciones
            String valor = args[0]; // Posible ArrayIndexOutOfBoundsException
            int numero = Integer.parseInt(valor); // Posible NumberFormatException
            FileInputStream fis = new FileInputStream("datos.txt"); // Posible FileNotFoundException
            
        } catch (ArrayIndexOutOfBoundsException | NumberFormatException e) {
            // Manejo común para problemas con argumentos o conversión
            System.err.println("Error en los argumentos de entrada: " + e.getMessage());
            
        } catch (FileNotFoundException | SecurityException e) {
            // Manejo común para problemas con archivos
            System.err.println("Error al acceder al archivo: " + e.getMessage());
            
        } catch (Exception e) {
            // Captura cualquier otra excepción
            System.err.println("Error inesperado: " + e.getMessage());
        }
    }
}
```

## 7. Excepciones Encadenadas

```java
import java.io.IOException;
import java.sql.SQLException;

public class EjemploExcepcionesEncadenadas {
    
    public static void procesarDatos() throws IOException {
        try {
            // Simulamos una SQLException en una capa de datos
            throw new SQLException("Error al acceder a la base de datos");
            
        } catch (SQLException sqlEx) {
            // Convertimos la SQLException en una IOException, pero conservamos la causa original
            IOException ioEx = new IOException("Error al procesar los datos");
            ioEx.initCause(sqlEx); // Encadenamos la excepción original como causa
            throw ioEx;
        }
    }
    
    public static void main(String[] args) {
        try {
            procesarDatos();
            
        } catch (IOException e) {
            System.err.println("Error capturado: " + e.getMessage());
            
            // Accedemos a la causa original
            Throwable causa = e.getCause();
            if (causa != null) {
                System.err.println("Causa original: " + causa.getMessage());
                System.err.println("Tipo de causa: " + causa.getClass().getName());
            }
            
            // Imprimimos la pila de llamadas completa
            System.err.println("\nDetalle completo del error:");
            e.printStackTrace();
        }
    }
}
```

## 8. Bloque try-catch con Recursos en Inventario

```java
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
import java.util.Date;

public class RegistroInventario {
    
    // Método para registrar una operación en un archivo de log
    public static void registrarOperacion(String operacion, String productoId) {
        // Usando try-with-resources para manejar automáticamente el cierre del BufferedWriter
        try (BufferedWriter writer = new BufferedWriter(new FileWriter("inventario_log.txt", true))) {
            Date fecha = new Date();
            String registro = fecha + " | " + operacion + " | Producto: " + productoId;
            
            writer.write(registro);
            writer.newLine();
            
            System.out.println("Operación registrada correctamente.");
            
        } catch (IOException e) {
            System.err.println("Error al registrar la operación: " + e.getMessage());
        }
    }
    
    public static void main(String[] args) {
        // Ejemplo de uso
        registrarOperacion("VENTA", "P001");
        registrarOperacion("REPOSICIÓN", "P002");
    }
}
```
