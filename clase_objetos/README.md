# Ejercicio Práctico: Sistema de Gestión de Biblioteca

## Descripción
En este ejercicio, crearás un sistema simple de gestión de biblioteca utilizando clases en Java. Implementarás una clase `Libro` con atributos tanto privados como públicos, métodos getters y setters, y constructores. Luego, crearás una clase principal para probar la funcionalidad.

## Archivos a Crear
1. `Libro.java`: Contiene la definición de la clase Libro.
2. `SistemaBiblioteca.java`: Contiene el método main para ejecutar el programa.

## Requisitos de la Clase Libro

### Atributos
- `titulo` (privado): String que representa el título del libro.
- `autor` (privado): String que representa el autor del libro.
- `anioPublicacion` (privado): int que representa el año de publicación.
- `disponible` (privado): boolean que indica si el libro está disponible para préstamo.
- `numPaginas` (público): int que representa el número de páginas del libro.
- `genero` (público): String que representa el género del libro.

### Métodos
- Constructor que inicialice todos los atributos.
- Getters y setters para los atributos privados.
- Método `prestar()`: cambia el estado de disponibilidad a false.
- Método `devolver()`: cambia el estado de disponibilidad a true.
- Método `obtenerInformacion()`: retorna un String con toda la información del libro.

## Instrucciones

### Paso 1: Crear la clase Libro
En el archivo `Libro.java`, define la clase Libro con los elementos especificados en los requisitos.

### Paso 2: Crear la clase principal
En el archivo `SistemaBiblioteca.java`, crea la clase principal con el método main:

```java
public class SistemaBiblioteca {
    public static void main(String[] args) {
        // TODO: Crea al menos tres objetos Libro con diferentes características

        // TODO: Muestra la información de todos los libros

        // TODO: Presta al menos un libro y muestra su nuevo estado

        // TODO: Intenta acceder y modificar los atributos públicos de al menos un libro

        // TODO: Demuestra el uso de los métodos getter y setter para los atributos privados
    }
}
```

### Paso 3: Compilar los archivos
Abre una terminal o línea de comandos y navega hasta el directorio que contiene tus archivos Java. Luego, ejecuta los siguientes comandos para compilar:

```
javac Libro.java
javac SistemaBiblioteca.java
```

### Paso 4: Ejecutar el programa
Una vez compilado, ejecuta el programa con el siguiente comando:

```
java SistemaBiblioteca
```

## Reto Adicional
Modifica la clase `Libro` para incluir un atributo estático que cuente el número total de libros creados. Implementa un método estático que retorne este conteo.

## Entrega
Asegúrate de implementar correctamente la clase `Libro` con todos los atributos y métodos requeridos. Tu programa en `SistemaBiblioteca` debe demostrar el uso de todos los métodos y atributos, incluyendo la distinción entre acceso a atributos públicos y privados.
