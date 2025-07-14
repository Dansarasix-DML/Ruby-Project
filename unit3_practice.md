### Ejercicios de Programación Procedural y Modular en Ruby:

1.  **Definir y Usar un Método Simple**
    *   **Tarea**: Crea un método llamado `saludar_mundo` que no reciba ningún parámetro y simplemente imprima la cadena "¡Hola, Ruby!". Luego, llama a este método para ejecutarlo.
    *   **Conceptos cubiertos**: Definición básica de métodos, invocación de métodos.

2.  **Método con Parámetros**
    *   **Tarea**: Modifica el método `saludar_mundo` del ejercicio anterior para que se llame `saludar_persona`. Este método debe aceptar un parámetro `nombre` y, al ser llamado, imprimir un saludo personalizado como "¡Hola, [nombre]!".
    *   **Conceptos cubiertos**: Paso de parámetros a métodos.

3.  **Método con Valor de Retorno Explícito**
    *   **Tarea**: Escribe un método llamado `calcular_suma(a, b)` que acepte dos números `a` y `b` como parámetros. El método debe **retornar explícitamente** la suma de estos dos números utilizando la palabra clave `return`. Imprime el resultado de la llamada al método.
    *   **Conceptos cubiertos**: Valores de retorno explícitos en métodos.

4.  **Método con Valor de Retorno Implícito**
    *   **Tarea**: Crea un método llamado `obtener_producto(x, y)` que reciba dos números. Este método debe calcular el producto de `x` y `y` y **retornar implícitamente** este valor (es decir, sin usar la palabra clave `return`, confiando en la última expresión evaluada). Muestra el valor retornado.
    *   **Conceptos cubiertos**: Valores de retorno implícitos en métodos.

5.  **Alcance de Variables Locales**
    *   **Tarea**: Define un método `demostrar_local` que declare una variable local `mensaje_interno` dentro de su cuerpo. Intenta acceder a `mensaje_interno` fuera de este método y observa el error. Explica por qué ocurre.
    *   **Conceptos cubiertos**: Alcance de variables locales, visibilidad.

6.  **Uso de Variables Globales**
    *   **Tarea**: Declara una variable global `$contador_global` con un valor inicial. Crea dos métodos, `incrementar_global` y `mostrar_global`, que modifiquen e impriman el valor de `$contador_global`, respectivamente. Llama a estos métodos para demostrar que el valor es compartido y persistente.
    *   **Conceptos cubiertos**: Variables globales, su alcance y uso compartido.

7.  **Variables de Instancia y Accesores**
    *   **Tarea**: Define una clase `Libro` con un método `initialize` que acepte `titulo` y `autor` como parámetros, asignándolos a variables de instancia `@titulo` y `@autor`. Utiliza `attr_reader` para crear métodos de acceso (getters) para estas variables de instancia y luego crea una instancia de `Libro` e imprime sus atributos.
    *   **Conceptos cubiertos**: Clases, objetos, variables de instancia, métodos `initialize`, `attr_reader`/`attr_accessor`.

8.  **Variables de Clase**
    *   **Tarea**: Añade una variable de clase `@@cantidad_libros` a la clase `Libro` (del ejercicio anterior) que se incremente cada vez que se crea una nueva instancia de `Libro`. Crea un método de clase `self.total_libros` que retorne el valor de `@@cantidad_libros`.
    *   **Conceptos cubiertos**: Variables de clase, métodos de clase.

9.  **Módulos como Mixins (`include`)**
    *   **Tarea**: Crea un módulo `Auditable` con un método de instancia `registrar_accion(accion)`. Luego, define una clase `GestorTareas` e **incluye** el módulo `Auditable`. Crea una instancia de `GestorTareas` y llama al método `registrar_accion` para demostrar su uso como mixin.
    *   **Conceptos cubiertos**: Módulos, mixins (`include`), métodos de instancia.

10. **Módulos como Mixins (`extend`)**
    *   **Tarea**: Modifica el módulo `Auditable` del ejercicio anterior para incluir un método de clase `self.auditoria_general(mensaje)`. En la clase `GestorTareas`, usa `extend` para que este método de clase sea accesible directamente desde la clase `GestorTareas`.
    *   **Conceptos cubiertos**: Módulos, mixins (`extend`), métodos de clase.

11. **Declaraciones Condicionales (`if-else` y `elsif`)**
    *   **Tarea**: Pide al usuario que ingrese una calificación numérica (0-100). Utiliza una estructura `if-elsif-else` para imprimir "Aprobado" si la calificación es 60 o más, "Reprobado" si es menor de 60, y "Excelente" si es 90 o más.
    *   **Conceptos cubiertos**: `if-elsif-else`, operadores de comparación, entrada de usuario.

12. **Bucle `each` con Arrays y Hashes**
    *   **Tarea**:
        *   Crea un array de tus frutas favoritas y usa `each` para imprimir cada una.
        *   Crea un hash que represente la información de un producto (e.g., `{nombre: "Laptop", precio: 1200, stock: 50}`). Usa `each` para iterar sobre las pares clave-valor e imprimirlas.
    *   **Conceptos cubiertos**: Arrays, Hashes, iteración con `each`.

13. **Bucle `while` y Control de Bucle**
    *   **Tarea**: Utiliza un bucle `while` para simular una cuenta regresiva desde 10 hasta 1. Dentro del bucle, usa `break` para detener la cuenta si el número llega a 5 (e imprime un mensaje indicando que se detuvo).
    *   **Conceptos cubiertos**: Bucle `while`, control de flujo (`break`).

14. **Sentencia `unless`**
    *   **Tarea**: Pide al usuario que ingrese una contraseña. Si la contraseña no está vacía (usa `unless`), imprime "Contraseña configurada". Si está vacía, imprime "La contraseña no puede estar vacía".
    *   **Conceptos cubiertos**: `unless` (inverso de `if`), entrada de usuario (`gets`, `chomp`).

15. **Entrada de Usuario y Manipulación de Cadenas**
    *   **Tarea**: Solicita al usuario que ingrese su nombre completo. Captura la entrada usando `gets` y `chomp`. Luego, divide la cadena en nombre y apellido, capitaliza cada parte (`capitalize`) e imprime el nombre completo formateado correctamente.
    *   **Conceptos cubiertos**: `gets`, `chomp`, métodos de cadena (`split`, `capitalize`, `join`), variable interpolation.

16. **Manejo de Archivos (Escritura)**
    *   **Tarea**: Escribe un script que cree o sobrescriba un archivo llamado `registro_acciones.txt`. En este archivo, añade la línea "La aplicación se inició a las [fecha y hora actual]". Utiliza `File.write` con el modo de escritura apropiado.
    *   **Conceptos cubiertos**: `File.write`, manejo de archivos.

17. **Manejo de Archivos (Lectura)**
    *   **Tarea**: Lee el contenido completo del archivo `registro_acciones.txt` creado en el ejercicio anterior e imprímelo en la consola.
    *   **Conceptos cubiertos**: `File.read`, manejo de archivos.

18. **Argumentos de Línea de Comandos (`ARGV`)**
    *   **Tarea**: Crea un script Ruby que acepte dos números como argumentos de línea de comandos. El script debe sumar estos dos números y mostrar el resultado. Asegúrate de convertir los argumentos a enteros o flotantes antes de realizar la operación.
    *   **Conceptos cubiertos**: `ARGV`, conversión de tipos (`to_i`).

19. **Hashes (Diccionarios/Arrays Asociativos)**
    *   **Tarea**: Crea un hash llamado `inventario` que almacene el stock de diferentes artículos. Por ejemplo: `inventario = { "manzanas" => 100, "naranjas" => 50, "bananas" => 75 }`. Accede al valor de "manzanas" e imprímelo. Luego, agrega un nuevo artículo al inventario y actualiza el stock de otro.
    *   **Conceptos cubiertos**: Hashes, creación, acceso y modificación de valores.

20. **Exploración con Interactive Ruby Shell (IRB)**
    *   **Tarea**: Abre una sesión de IRB desde tu terminal (`irb`).
        *   Define una variable.
        *   Realiza una operación aritmética.
        *   Define un método simple y llámalo.
        *   Prueba una declaración condicional (`if` o `unless`).
        *   Experimenta con un bucle `times` o `each`.
        *   Explora el valor de `self` en la sesión principal.
    *   **Conceptos cubiertos**: IRB como herramienta interactiva para probar código y depurar.
