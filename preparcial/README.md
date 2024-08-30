# Taller de Palíndromos y Manejo de Productos en C++

## Parte 1: Palíndromos

### Descripción

Esta parte del taller se centra en la implementación de funciones en C++ para trabajar con palíndromos. Un palíndromo es una palabra o frase que se lee igual de izquierda a derecha que de derecha a izquierda, ignorando espacios y signos de puntuación.

### Objetivos

Desarrollar tres funciones principales que trabajen con palíndromos, cumpliendo con restricciones específicas de implementación.

### Funciones a Implementar

#### 1. Eliminación de Espacios (5 puntos)

Desarrolle una función que reciba una cadena de caracteres, elimine los espacios que contiene la cadena y retorne la cadena sin ningún espacio.

**Prototipo sugerido:**
```cpp
char* eliminarEspacios(const char* cadena, int longitud, int& nuevaLongitud);
```

#### 2. Verificación de Palíndromo (15 puntos)

Desarrolle una función que reciba una frase cualquiera (que puede o no contener espacios) y que retorne verdadero si la frase es palíndroma o falso si no lo es.

**Prototipo sugerido:**
```cpp
bool esPalindromo(const char* frase, int longitud);
```

#### 3. Conteo de Palíndromos en Archivo (10 puntos)

Desarrolle una función que reciba la ruta a un archivo de texto y que retorne la cantidad de líneas en ese archivo que son palíndromos.

**Prototipo sugerido:**
```cpp
int contarPalindromosEnArchivo(const char* rutaArchivo);
```

### Restricciones

- No se puede usar el tipo de datos `string`.
- Los arreglos deben ser dinámicos.
- Los arreglos deben recorrerse con aritmética de apuntadores.

### Ejemplos

- La palabra "reconocer" es un palíndromo.
- La frase "anita lava la tina" es un palíndromo (ignorando espacios).

### Notas Adicionales

- Asegúrese de manejar correctamente la memoria dinámica para evitar fugas de memoria.
- Considere casos extremos como cadenas vacías o archivos que no existen.
- La implementación debe ser eficiente y seguir las mejores prácticas de programación en C++.

## Parte 2: Manejo de Productos y Fechas

### Descripción

Esta parte del taller se centra en el manejo de información de productos almacenada en un archivo binario, incluyendo comparación de fechas, búsqueda de productos y ordenamiento.

### Estructura de Datos

Se utiliza la siguiente estructura para representar un producto:

```cpp
struct Producto {
    char NombreTienda[100];
    char URLTienda[200];
    char NombreProducto[300];
    char FechaVigenciaPromocion[10]; //Formato dd/mm/yyyy
    double Precio;
};
```

### Funciones a Implementar

#### 1. Comparación de Fechas (5 puntos)

Desarrolle una función que compare dos fechas en formato "dd/mm/yyyy".

**Prototipo:**
```cpp
bool EsMayor(char *fecha1, char *fecha2);
```

- **Entrada:** Dos cadenas de caracteres representando fechas.
- **Salida:** `true` si la primera fecha es mayor que la segunda, `false` en caso contrario.

#### 2. Búsqueda de Productos (15 puntos)

Desarrolle una función que busque productos en el archivo `productos.dat` basándose en una fecha y un nombre de producto.

**Prototipo:**
```cpp
struct Producto *BuscarProductos(char *FechaBuscar, char *Nombre);
```

- **Entrada:** 
  - Una fecha en formato "dd/mm/yyyy".
  - Un nombre de producto.
- **Salida:** Un arreglo dinámico de `Producto` que cumpla con los criterios de búsqueda.
- **Criterios:** 
  - El nombre del producto contiene el nombre buscado.
  - La fecha de vigencia de la promoción es mayor o igual a la fecha buscada.

#### 3. Ordenamiento y Grabación de Mejores Productos (20 puntos)

Desarrolle una función que ordene el arreglo generado por la función anterior y grabe los mejores productos en un archivo.

**Prototipo:** No especificado, pero se puede sugerir:
```cpp
void OrdenarYGrabarMejores(struct Producto *productos, int cantidad);
```

- **Funcionalidad:**
  - Ordena el arreglo de productos de menor a mayor por precio.
  - Graba los 5 primeros productos del arreglo ordenado en un archivo llamado "Mejores.txt".
  - Cada producto se graba con todos sus campos separados por comas.

### Restricciones y Consideraciones

- El archivo de entrada `productos.dat` es un archivo binario.
- El formato de fecha utilizado es "dd/mm/yyyy".
- Se debe manejar correctamente la memoria dinámica.
- Considere casos extremos como archivos vacíos o menos de 5 productos.

### Ejemplo de Datos

```
Tiendas Jupiter,www.jupiter.com,Parlantes tipo 1,30/03/2023,175000
Yelao,yelao.com,Llantas marca a,13/02/2023,400000
Logro,logro.com,Parlantes tipo 1,28/03/2023,172000
Llanticas.com,www.llanticas.com,Llantas marca a,16/02/2023,412000
```

### Notas Adicionales

- Asegúrese de manejar correctamente la lectura y escritura de archivos binarios.
- La comparación de fechas debe ser precisa, considerando año, mes y día.
- En la búsqueda de productos, considere una comparación parcial del nombre del producto.
- Para el ordenamiento, puede utilizar cualquier algoritmo eficiente.
