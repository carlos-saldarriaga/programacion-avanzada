# Pontificia Universidad Javeriana
## Departamento de Ingeniería de Sistemas
### Programación Avanzada
# Taller 3 - Apuntadores Básicos en C++

## Objetivos
- Practicar el uso básico de apuntadores en C++
- Aplicar conceptos de referencias y operador de indirección
- Utilizar apuntadores en funciones

## Duración: 2 horas

## Instrucciones
Implementa las siguientes funciones en C++. Asegúrate de utilizar apuntadores, referencias y el operador de indirección según se indique en cada ejercicio.

1. **Intercambio de valores**
   Escribe una función llamada `intercambiar` que tome dos enteros como parámetros por referencia y los intercambie.
   ```cpp
   void intercambiar(int& a, int& b);
   ```

2. **Modificación a través de apuntador**
   Implementa una función llamada `duplicar` que tome un apuntador a un entero y duplique el valor al que apunta.
   ```cpp
   void duplicar(int* num);
   ```

3. **Cálculo con referencias**
   Crea una función llamada `calcularCuadradoYCubo` que tome un número entero por referencia y dos parámetros adicionales por referencia para almacenar el cuadrado y el cubo del número.
   ```cpp
   void calcularCuadradoYCubo(const int& num, int& cuadrado, int& cubo);
   ```

4. **Operaciones con apuntadores**
   Desarrolla una función llamada `operacionesBasicas` que tome dos apuntadores a enteros y realice las siguientes operaciones:
   - Suma los valores y almacena el resultado en el primer apuntador
   - Resta los valores y almacena el resultado en el segundo apuntador
   ```cpp
   void operacionesBasicas(int* a, int* b);
   ```

5. **Función con retorno de apuntador**
   Implementa una función llamada `encontrarMayor` que tome tres enteros como parámetros y devuelva un apuntador al mayor de ellos.
   ```cpp
   int* encontrarMayor(int& a, int& b, int& c);
   ```

6. **Manipulación de cadenas con apuntadores**
   Escribe una función llamada `contarVocales` que tome un apuntador a una cadena de caracteres (C-string) y devuelva el número de vocales en la cadena.
   ```cpp
   int contarVocales(const char* str);
   ```


## Programa Principal
Implementa un programa principal (función `main`) que demuestre el uso de todas las funciones anteriores. Incluye ejemplos de llamadas a cada función y muestra los resultados.

## Requisitos Adicionales
- Utiliza comentarios para explicar el funcionamiento de cada función.
- Incluye validaciones básicas donde sea necesario (por ejemplo, comprobar si un apuntador es nulo antes de dereferenciarlo).
- No utilices arreglos de apuntadores ni conceptos avanzados que no se hayan cubierto en clase.


## Reto Adicional (Punto Extra)

1. **Rotación de valores con apuntadores**
   Implementa una función llamada `rotarValores` que tome tres apuntadores a enteros y realice una rotación de sus valores hacia la derecha. Es decir, el valor del tercer apuntador debe pasar al segundo, el del segundo al primero, y el del primero al tercero.
   ```cpp
   void rotarValores(int* a, int* b, int* c);
   ```
   
   Ejemplo de uso:
   ```cpp
   int x = 1, y = 2, z = 3;
   rotarValores(&x, &y, &z);
   // Después de la llamada: x = 3, y = 1, z = 2
   ```

   Restricciones:
   - No puedes usar variables adicionales para almacenar los valores.
   - Debes realizar la rotación utilizando únicamente operaciones con apuntadores.
   - No puedes usar el operador de indirección (*) más de tres veces en total en la función.

   Pista: Considera cómo podrías usar la aritmética de apuntadores de manera creativa para resolver este problema.


## Entrega
Entrega un único archivo .cpp que contenga todas las funciones implementadas y el programa principal. Nombra tu archivo de la siguiente manera:

NOMBRE1_APELLIDO1_NOMBRE2_APELLIDO2_taller_apuntadores_basicos.cpp

Sube el archivo a la asignación en Campus Virtual.

¡Buena suerte!
