# Parcial Práctico: Programación Orientada a Objetos
Tiempo: 2 horas
Puntaje total: 100 puntos

## Diagrama de Clases
```
                   +---------------+
                   |   Vehiculo   |
                   +---------------+
                   | -marca: String|
                   | -modelo: String|
                   | -año: int     |
                   +---------------+
                   | +getMarca()   |
                   | +getModelo()  |
                   | +getAño()     |
                   | +toString()   |
                   +---------------+
                          ↑
          +---------------+---------------+
          |                             |
    +-----------+                 +-----------+
    |   Auto    |                 |   Moto    |
    +-----------+                 +-----------+
    | -puertas  |                 | -cilindrada|
    +-----------+                 +-----------+
    | +acelerar()|                 | +acelerar()|
    +-----------+                 +-----------+

```

## Consignas (100 puntos totales)

1. **(30 puntos) Implementación de Clases y Herencia:**
   - Crear la clase abstracta `Vehiculo` con los atributos y métodos mostrados en el diagrama
   - Implementar las clases `Auto` y `Moto` que hereden de `Vehiculo`
   - Definir un método abstracto `acelerar()` en `Vehiculo` que sea implementado de manera diferente en cada subclase

2. **(20 puntos) Polimorfismo:**
   - Crear una clase `Concesionaria` que maneje un array de `Vehiculo`
   - Implementar un método que recorra el array y llame al método `acelerar()` de cada vehículo
   - Demostrar el uso del polimorfismo mediante un método que procese diferentes tipos de vehículos

3. **(20 puntos) Excepciones:**
   - Crear una excepción personalizada llamada `VehiculoException`
   - En el constructor de `Vehiculo`, lanzar esta excepción si:
     * El año es menor a 1900 o mayor al año actual
     * La marca o modelo están vacíos
   - Manejar apropiadamente estas excepciones en el código

4. **(15 puntos) Serialización:**
   - Hacer que todas las clases sean serializables
   - Implementar métodos para:
     * Guardar un array de vehículos en un archivo
     * Cargar los vehículos desde el archivo

5. **(15 puntos) Sobrecarga de métodos:**
   - En la clase `Concesionaria`, implementar el método `agregarVehiculo` con las siguientes sobrecargas:
     * `agregarVehiculo(Vehiculo v)`
     * `agregarVehiculo(String marca, String modelo, int año)`
     * `agregarVehiculo(Auto a)`
     * `agregarVehiculo(Moto m)`

## Criterios de Evaluación:
- Correcta implementación de la herencia y clases abstractas
- Uso apropiado del polimorfismo
- Manejo adecuado de excepciones
- Implementación correcta de la serialización
- Sobrecarga de métodos implementada correctamente
- Código limpio y bien documentado

## Bonus (10 puntos extra):
- Implementar un método que permita ordenar los vehículos por año
- Agregar pruebas unitarias para las principales funcionalidades

## Notas:
- El código debe estar correctamente indentado y comentado
- Se evaluará el manejo de casos borde y validaciones
- Debe incluir un programa principal que demuestre todas las funcionalidades
