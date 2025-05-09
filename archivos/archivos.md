# Taller: Manejo de Archivos y Excepciones en Java

## Descripción
Este taller está diseñado para practicar el manejo de archivos en Java y las excepciones asociadas. Aprenderás a crear, leer, escribir y manipular archivos utilizando las clases disponibles en Java, a la vez que implementas un manejo adecuado de excepciones.

## Objetivos
- Comprender las operaciones básicas con archivos en Java
- Implementar y utilizar excepciones personalizadas
- Practicar el uso de bloques try-catch-finally y try-with-resources
- Aplicar el manejo de excepciones en situaciones reales con archivos

## Estructura del Proyecto
El proyecto consta de las siguientes clases:

1. **Excepciones personalizadas:**
   - `ArchivoNoEncontradoException.java`: Excepción checked para cuando un archivo no existe
   - `FormatoArchivoInvalidoException.java`: Excepción unchecked para cuando el formato del archivo no es el esperado

2. **Clases principales:**
   - `Archivo.java`: Representa un archivo con sus atributos y métodos básicos
   - `GestorArchivos.java`: Contiene operaciones para manipular archivos (crear, leer, escribir, etc.)
   - `MainGestorArchivos.java`: Clase principal con el método main

## Tareas a Implementar

### 1. Completar la clase GestorArchivos.java
En esta clase deberás implementar los siguientes métodos:

- `leerArchivoBufferedReader(String rutaArchivo)`: Lee un archivo utilizando BufferedReader
- `leerArchivoPrintReader(String rutaArchivo)`: Lee un archivo utilizando PrintReader
- `escribirArchivoBufferedWriter(String rutaArchivo, String contenido, boolean append)`: Escribe en un archivo utilizando BufferedWriter
- `escribirArchivoPrintWriter(String rutaArchivo, String contenido, boolean append)`: Escribe en un archivo utilizando PrintWriter

### 2. Implementar el manejo de excepciones
Para cada método deberás:
- Utilizar try-catch para manejar las excepciones que puedan ocurrir
- Lanzar `ArchivoNoEncontradoException` cuando corresponda
- Implementar al menos un ejemplo de try-with-resources
- Usar bloques finally cuando sea necesario

### 3. Probar las funcionalidades en MainGestorArchivos
- Crear un menú simple que permita al usuario elegir qué operación realizar
- Implementar cada operación del menú utilizando los métodos de GestorArchivos
- Manejar adecuadamente las excepciones en la clase principal

## Entrega
- Implementa todos los métodos requeridos
- Asegúrate de manejar correctamente las excepciones
- Demuestra el uso de try-with-resources y try-catch-finally
- Realiza pruebas para verificar que todo funcione correctamente

## Evaluación
Se evaluará:
- Correcta implementación de los métodos de manejo de archivos
- Manejo adecuado de excepciones
- Uso apropiado de try-with-resources y try-catch-finally
- Claridad y organización del código
