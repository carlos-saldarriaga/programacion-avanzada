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
- `leerArchivoScanner(String rutaArchivo)`: Lee un archivo utilizando Scanner
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

## Ejemplos de Implementación

### Ejemplo 1: Lectura de archivo con try-with-resources (BufferedReader)

```java
/**
 * Lee un archivo utilizando BufferedReader con try-with-resources.
 * 
 * @param rutaArchivo Ruta completa del archivo a leer
 * @return Contenido del archivo como una cadena
 * @throws ArchivoNoEncontradoException Si el archivo no existe
 * @throws IOException Si ocurre un error al leer el archivo
 */
public String leerArchivoBufferedReader(String rutaArchivo) throws ArchivoNoEncontradoException, IOException {
    File archivo = new File(rutaArchivo);
    
    if (!archivo.exists()) {
        throw new ArchivoNoEncontradoException("El archivo no existe: " + rutaArchivo);
    }
    
    StringBuilder contenido = new StringBuilder();
    
    // try-with-resources garantiza que el BufferedReader se cerrará automáticamente al final
    try (BufferedReader reader = new BufferedReader(new FileReader(archivo))) {
        String linea;
        while ((linea = reader.readLine()) != null) {
            contenido.append(linea).append("\n");
        }
    }
    
    return contenido.toString();
}
```

### Ejemplo 2: Escritura de archivo con try-catch-finally (BufferedWriter)

```java
/**
 * Escribe en un archivo utilizando BufferedWriter con try-catch-finally.
 * 
 * @param rutaArchivo Ruta completa del archivo donde escribir
 * @param contenido Contenido a escribir en el archivo
 * @param append Si es true, añade al final del archivo; si es false, sobrescribe
 * @throws IOException Si ocurre un error al escribir en el archivo
 */
public void escribirArchivoBufferedWriter(String rutaArchivo, String contenido, boolean append) throws IOException {
    BufferedWriter writer = null;
    
    try {
        writer = new BufferedWriter(new FileWriter(rutaArchivo, append));
        writer.write(contenido);
        System.out.println("Contenido escrito correctamente.");
    } catch (IOException e) {
        System.err.println("Error al escribir en el archivo: " + e.getMessage());
        throw e; // Re-lanzamos la excepción para que se maneje en un nivel superior
    } finally {
        // El bloque finally se ejecuta siempre, haya o no excepciones
        if (writer != null) {
            try {
                writer.close(); // Cerramos el recurso manualmente
                System.out.println("Recurso cerrado correctamente.");
            } catch (IOException e) {
                System.err.println("Error al cerrar el writer: " + e.getMessage());
            }
        }
    }
}
```

### Ejemplo 3: Lectura de archivo con try-with-resources (Scanner)

```java
/**
 * Lee un archivo utilizando Scanner con try-with-resources.
 * 
 * @param rutaArchivo Ruta completa del archivo a leer
 * @return Contenido del archivo como una cadena
 * @throws ArchivoNoEncontradoException Si el archivo no existe
 * @throws IOException Si ocurre un error al leer el archivo
 */
public String leerArchivoScanner(String rutaArchivo) throws ArchivoNoEncontradoException, IOException {
    File archivo = new File(rutaArchivo);
    
    if (!archivo.exists()) {
        throw new ArchivoNoEncontradoException("El archivo no existe: " + rutaArchivo);
    }
    
    StringBuilder contenido = new StringBuilder();
    
    // try-with-resources con Scanner
    try (Scanner scanner = new Scanner(archivo)) {
        // Configuramos el delimitador para leer línea por línea
        scanner.useDelimiter("\n");
        
        while (scanner.hasNext()) {
            contenido.append(scanner.next()).append("\n");
        }
    } catch (FileNotFoundException e) {
        // Esta excepción no debería ocurrir porque ya verificamos la existencia del archivo
        throw new ArchivoNoEncontradoException("El archivo no existe: " + rutaArchivo, e);
    }
    
    return contenido.toString();
}
```

### Ejemplo 4: Manejo de múltiples excepciones

```java
/**
 * Ejemplo de manejo de múltiples excepciones al leer un archivo.
 */
public void ejemploMultiplesExcepciones(String rutaArchivo) {
    try {
        File archivo = new File(rutaArchivo);
        
        // Posible FileNotFoundException
        FileInputStream fis = new FileInputStream(archivo);
        
        // Posible IOException
        byte[] datos = new byte[1024];
        int bytesLeidos = fis.read(datos);
        
        // Trabajo con los datos leídos
        String contenido = new String(datos, 0, bytesLeidos);
        System.out.println("Contenido: " + contenido);
        
        fis.close();
        
    } catch (FileNotFoundException e) {
        System.err.println("No se encontró el archivo: " + e.getMessage());
        
    } catch (IOException e) {
        System.err.println("Error de lectura/escritura: " + e.getMessage());
        
    } catch (Exception e) {
        System.err.println("Error inesperado: " + e.getMessage());
        
    }
}
```

### Ejemplo 5: Verificación de existencia de archivo con manejo de excepciones

```java
/**
 * Verifica si un archivo existe y tiene permisos de lectura.
 */
public void verificarArchivo(String rutaArchivo) throws ArchivoNoEncontradoException {
    File archivo = new File(rutaArchivo);
    
    if (!archivo.exists()) {
        throw new ArchivoNoEncontradoException("El archivo no existe: " + rutaArchivo);
    }
    
    if (!archivo.canRead()) {
        throw new ArchivoNoEncontradoException("No tienes permisos de lectura sobre el archivo: " + rutaArchivo);
    }
    
    System.out.println("El archivo existe y se puede leer.");
}
```

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
