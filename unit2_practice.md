# 2. Ejercicios de Sintaxis y Fundamentos de Ruby

**1. Variables y Tipos de Datos (Básico)**
*   **Tarea**: Declara una variable local `nombre_usuario` con tu nombre. Luego, dentro de una clase `MiClase`, declara una variable de instancia `@saludo` con el valor "Hola" y una variable de clase `@@conteo_objetos` inicializada en 0. Incrementa `@@conteo_objetos` cada vez que se "crea" una instancia de `MiClase`. Finalmente, declara una variable global `$version_app` con el valor "1.0". Imprime todas estas variables para verificar sus valores (para las de instancia y clase, necesitarás un método o una simulación de instancia).
*   **Conceptos involucrados**: Variables locales, variables de instancia, variables de clase, variables globales, impresión con `puts`.

**2. Interpolación de Variables y Cadenas**
*   **Tarea**: Usando las variables `nombre_usuario` y `$version_app` del ejercicio anterior, construye una cadena que diga: "Bienvenido, [nombre_usuario] a la aplicación en su versión [1.0]". Asegúrate de usar la interpolación de variables.
*   **Conceptos involucrados**: Interpolación de variables, cadenas de texto.

**3. Manipulación de Cadenas**
*   **Tarea**: Toma la cadena `frase = "   ruby es DIVERTIDO!   "`. Realiza las siguientes operaciones e imprime el resultado de cada una:
    *   Convierte la frase a todo mayúsculas.
    *   Convierte la frase a todo minúsculas.
    *   Capitaliza la primera letra de la frase (manteniendo el resto en minúsculas).
    *   Elimina los espacios en blanco al inicio y al final de la frase.
    *   Verifica si la frase (sin espacios) termina con "VIDO!".
*   **Conceptos involucrados**: Métodos de string `upcase()`, `downcase()`, `capitalize()`, `strip()`, `end_with?()`.

**4. Arrays Básicos**
*   **Tarea**: Crea un array llamado `ciudades` con los elementos "Madrid", "Barcelona", "Valencia", "Sevilla". Imprime el array completo. Luego, imprime el primer y el último elemento. Añade "Bilbao" al final del array y "Alicante" al inicio. Finalmente, imprime el tamaño del array.
*   **Conceptos involucrados**: Arrays, acceso a elementos (`first()`, `last()`), añadir elementos (`push()`, `unshift()`, `<<`), `size()` o `length()`.

**5. Hashes y Símbolos**
*   **Tarea**: Crea un hash llamado `configuracion` usando símbolos como claves para representar opciones de un programa: `:tema` con valor "oscuro", `:idioma` con valor "español", y `:notificaciones` con valor `true`. Imprime el hash completo. Luego, accede e imprime el valor asociado a la clave `:idioma`.
*   **Conceptos involucrados**: Hashes, símbolos como claves, acceso a valores de hash.

**6. Conversión de Tipos y Entrada de Usuario**
*   **Tarea**: Pide al usuario que ingrese su edad y su peso (ej. "65.5"). Ambos inputs serán cadenas. Convierte la edad a un entero y el peso a un flotante. Realiza una operación aritmética simple (ej. `peso / edad`) e imprime el resultado.
*   **Conceptos involucrados**: Entrada de usuario `gets`, `chomp()`, conversión de tipos `to_i()` y `to_f()`.

**7. Operadores Aritméticos y Asignación Paralela**
*   **Tarea**: Declara `x = 7` e `y = 2`. Calcula `x` elevado a la potencia de `y` (`**`). Incrementa `x` en 5 usando el operador de asignación abreviada `+=`. Finalmente, intercambia los valores de `x` e `y` utilizando la asignación paralela. Imprime los valores de `x` e `y` después de cada operación.
*   **Conceptos involucrados**: Operadores aritméticos (`**`), operadores de asignación (`=`, `+=`), asignación paralela.

**8. Operadores de Comparación y Espacial (`<=>`)**
*   **Tarea**: Dadas dos variables `a = 100` y `b = 50`. Comprueba si `a` es mayor que `b`, si `a` es igual a `b`, y si `a` es diferente de `b`. Imprime los resultados booleanos. Luego, utiliza el operador combinado (`<=>`) para comparar `a` y `b`, y también `b` y `a`, e imprime ambos resultados.
*   **Conceptos involucrados**: Operadores de comparación, operador `spaceship` (`<=>`).

**9. Operadores Lógicos y Valores "Truthy" / "Falsy"**
*   **Tarea**: Demuestra el comportamiento de los operadores lógicos `and`, `or`, `not` con las siguientes expresiones:
    *   `true and false`
    *   `false or true`
    *   `not true`
    *   `nil or "Hola"` (Demostrando "truthy" para strings no vacías)
    *   `0 and "Cero"` (Demostrando "truthy" para 0)
    Imprime el resultado de cada expresión.
*   **Conceptos involucrados**: Operadores lógicos (`and`, `or`, `not`), valores `truthy` y `falsy`.

**10. Sentencia `if`/`elsif`/`else` y Operador de Navegación Segura**
*   **Tarea**: Pide al usuario que ingrese un número. Si es positivo, imprime "Es positivo". Si es negativo, imprime "Es negativo". Si es cero, imprime "Es cero". Luego, crea un objeto `usuario` que a veces puede ser `nil`. Intenta acceder a `usuario.perfil.nombre` usando el operador de navegación segura `&.` para evitar errores si `usuario` o `usuario.perfil` son `nil`.
*   **Conceptos involucrados**: Sentencia `if`/`elsif`/`else`, operador de navegación segura `&.`.

**11. Sentencia `case` con Rangos y Strings**
*   **Tarea**: Pide al usuario que ingrese un mes (como número del 1 al 12). Usa una sentencia `case` con rangos para clasificar el mes como "Primavera" (3-5), "Verano" (6-8), "Otoño" (9-11) o "Invierno" (12, 1-2). Si ingresa "Enero", "Febrero" o "Diciembre", clasifícalo como "Invierno" (puedes usar múltiples condiciones en el `when`).
*   **Conceptos involucrados**: Sentencia `case`, rangos inclusivos `..`, múltiples condiciones en `when`.

**12. Bucle `while` y Control de Bucle `break`**
*   **Tarea**: Escribe un bucle `while` que comience con `contador = 1`. El bucle debe imprimir `contador` en cada iteración y aumentarlo en 1. Si `contador` llega a 7, el bucle debe terminar (`break`).
*   **Conceptos involucrados**: Bucle `while`, `break`.

**13. Bucle `until` y Control de Bucle `next`**
*   **Tarea**: Escribe un bucle `until` que comience con `numero = 1`. El bucle debe imprimir `numero` si es impar. Si `numero` es par, debe saltar la impresión y pasar a la siguiente iteración (`next`). El bucle debe continuar hasta que `numero` sea 11.
*   **Conceptos involucrados**: Bucle `until`, `next`, `odd?()`.

**14. Bucle `for` con Rangos y Comentarios**
*   **Tarea**: Escribe un bucle `for` que itere a través de un rango de letras de 'a' a 'e' (inclusive). Dentro del bucle, imprime cada letra. Agrega un comentario de una sola línea explicando el propósito del bucle y un comentario multilínea al inicio del script con tu nombre y la fecha.
*   **Conceptos involucrados**: Bucle `for`, rangos, comentarios de una sola línea y multilínea.

**15. Uso Básico de Bloques y `times`**
*   **Tarea**: Usa el método `times` para imprimir los números del 0 al 4. Cada número debe ir precedido por el texto "Iteración: ".
*   **Conceptos involucrados**: Bloques `do..end`, método `times`.

**16. Iterador `each` con Arrays y Hashes**
*   **Tarea**: Crea un array de números `calificaciones =`. Itera sobre él usando `each` e imprime cada calificación. Luego, crea un hash `inventario = { "manzanas" => 10, "naranjas" => 5, "peras" => 8 }`. Itera sobre el hash usando `each` e imprime cada par clave-valor.
*   **Conceptos involucrados**: Iterador `each`, bloques.

**17. Transformación con `map`**
*   **Tarea**: Dado un array de números `precios = [10.5, 20.0, 5.75]`, usa el método `map()` para crear un nuevo array donde cada precio tenga un impuesto del 10% aplicado (multiplica por 1.10). Imprime el array original y el nuevo array con los precios con impuestos.
*   **Conceptos involucrados**: Método `map()`, transformación de colecciones.

**18. Filtrado con `select` y `reject`**
*   **Tarea**: Dado el array `numeros =`.
    *   Usa `select()` para obtener solo los números mayores que 10.
    *   Usa `reject()` para obtener solo los números divisibles por 5.
    Imprime ambos resultados como nuevos arrays.
*   **Conceptos involucrados**: Método `select()`, método `reject()`.

**19. `each_with_index`**
*   **Tarea**: Itera sobre el array `elementos = ["agua", "tierra", "fuego", "aire"]` utilizando `each_with_index`. Para cada elemento, imprime su índice y el elemento en el formato "Elemento en índice [índice]: [elemento]".
*   **Conceptos involucrados**: Iterador `each_with_index`.

**20. Concepto de Procs y Lambdas**
*   **Tarea**: Describe brevemente las principales diferencias entre `Proc` y `Lambda` en Ruby, enfocándote en cómo manejan los argumentos y la sentencia `return`.
*   **Conceptos involucrados**: `Procs` y `Lambdas`, manejo de argumentos, comportamiento de `return`.
