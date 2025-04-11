# Taller 8: Profundizando en Clases, Atributos y Métodos en Java

## Descripción
Este taller está diseñado para profundizar en conceptos avanzados de Programación Orientada a Objetos en Java, centrándose en la implementación de un Sistema de Gestión de Empleados para una empresa ficticia.

## Objetivos
- Implementar y utilizar atributos de clase (estáticos) y atributos final
- Crear y aplicar diferentes tipos de métodos: instancia, estáticos y finales
- Practicar el encapsulamiento y la sobrecarga de métodos
- Utilizar la propiedad this y la notación punto (.) correctamente
- Resolver problemas complejos utilizando objetos y sus interacciones

## Contenido del Taller

### 1. Clase Empleado
Crea la clase `Empleado.java` con los siguientes elementos:
- Atributos de instancia (privados): nombre, id, salario
- Atributo de clase (estático): contadorEmpleados
- Atributo final: SALARIO_BASE
- Métodos getters y setters apropiados
- Constructor que inicialice los atributos y actualice el contador

### 2. Métodos de Instancia
Implementa los siguientes métodos en la clase `Empleado`:
- `calcularSalarioAnual()`: método público que retorna el salario anual
- `aumentarSalario(double porcentaje)`: método privado para aumentar el salario

### 3. Sobrecarga de Métodos
Crea múltiples versiones del método `calcularBono`:
- `calcularBono()`: sin parámetros, retorna un bono estándar
- `calcularBono(double porcentaje)`: calcula el bono basado en un porcentaje del salario
- `calcularBono(int aniosServicio)`: calcula el bono basado en los años de servicio

### 4. Métodos Estáticos
Agrega los siguientes métodos estáticos a la clase `Empleado`:
- `obtenerTotalEmpleados()`: retorna el número total de empleados
- `compararSalarios(Empleado emp1, Empleado emp2)`: compara los salarios de dos empleados

### 5. Métodos y Atributos Finales
Implementa un método final `obtenerDetallesContrato()` que retorne información sobre el contrato del empleado.

### 6. Clase Departamento
Crea la clase `Departamento.java` que contenga:
- Una lista de empleados
- Métodos para agregar empleados, calcular la nómina total, y encontrar el empleado con mayor salario

### 7. Clase Principal
En `SistemaGestionEmpleados.java`, crea el método `main` para demostrar todas las funcionalidades implementadas.

## Reto Adicional
Implementa un sistema de reportes que utilice la propiedad `this` y la notación punto para navegar entre objetos `Empleado` y `Departamento`.

## Instrucciones de Ejecución
1. Clona este repositorio
2. Navega al directorio del proyecto
3. Compila los archivos Java:
   ```
   javac *.java
   ```
4. Ejecuta el programa principal:
   ```
   java SistemaGestionEmpleados
   ```

## Entrega
- Completa todos los ejercicios en el tiempo asignado (2 horas)
- Sube tu código a este repositorio antes de la medianoche del día del taller
- Asegúrate de que tu código esté bien comentado y siga las mejores prácticas de Java

## Evaluación
Se evaluará la correcta implementación de los conceptos solicitados, la eficiencia del código, y la capacidad para resolver problemas utilizando programación orientada a objetos.



Este README proporciona una descripción detallada del taller, incluyendo los objetivos, el contenido, las instrucciones para cada ejercicio, cómo ejecutar el programa, y los criterios de entrega y evaluación. Está estructurado de manera que sea fácil de leer y seguir para los estudiantes.
