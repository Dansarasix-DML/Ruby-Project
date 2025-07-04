# 2. Sintaxis y estructuras fundamentales

En Ruby, la sintaxis y las estructuras fundamentales están diseñadas para la **legibilidad y la sencillez**, buscando que el código se lea casi como una oración en inglés. A diferencia de PHP, Ruby no usa etiquetas `<?php` para delimitar el código, ni símbolos `$` para las variables. Aunque Ruby es muy flexible y permite el uso de puntos y coma al final de las líneas, la **mejor práctica en Ruby es omitirlos**.

### 2.1. Variables, tipos de datos, operadores

**Variables**
Las variables en Ruby son **contenedores mutables** para valores, similares a otros lenguajes de programación. No es necesario declarar explícitamente el tipo de una variable antes de usarla; Ruby es un **lenguaje de tipado dinámico** (o "duck typing"), lo que significa que el intérprete infiere el tipo de dato en tiempo de ejecución. Una variable puede cambiar de tipo durante la ejecución sin generar errores.

Ruby distingue varios tipos de variables por su prefijo:
*   **Variables locales**: No tienen prefijo. Su alcance está limitado al bloque o contexto donde se declaran. Sin embargo, las variables locales declaradas en bloques `if` o `case` pueden usarse en el ámbito padre.
*   **Variables de instancia**: Se prefijan con `@` (por ejemplo, `@first_name`). Estas variables pertenecen a una instancia específica de una clase y son accesibles solo por los métodos de esa instancia. No se comparten entre diferentes instancias de la misma clase.
*   **Variables de clase**: Se prefijan con `@@` (por ejemplo, `@@count`). Son compartidas por **todas las instancias de una clase** y sus subclases, lo que las hace útiles para almacenar información relevante para todos los objetos de esa clase.
*   **Variables globales**: Se prefijan con `$` (por ejemplo, `$total_animals`). Tienen un **alcance global** y pueden ser utilizadas en cualquier parte del programa, independientemente de dónde se definan.

La **interpolación de variables** es una característica útil para incrustar el valor de una variable dentro de una cadena. Esto se logra usando la sintaxis `#{variable}` dentro de comillas dobles.

**Tipos de datos**
Ruby incluye varios tipos de datos fundamentales. Los más comunes son:
*   **Números**: Incluyen enteros (`Integer`) y números de punto flotante (`Float`). Ruby determina automáticamente si un número es entero o flotante según su valor. Se pueden escribir enteros en diferentes bases (hexadecimal, binario, octal) usando prefijos como `0x`, `0b`, `0` respectivamente. Para mayor legibilidad, se pueden usar guiones bajos como separadores de miles (`1_000`).
*   **Cadenas (Strings)**: Secuencias de caracteres encerradas en comillas simples (`'`) o dobles (`"`). Las comillas dobles permiten la interpolación de cadenas y secuencias de escape. Ruby proporciona métodos para manipular cadenas, como `upcase()`, `downcase()`, `capitalize()` para cambiar el caso, y métodos con `!` (como `upcase!`) que modifican la cadena original de forma permanente. Otros métodos útiles incluyen `strip()` (para eliminar espacios en blanco), `start_with?()` y `end_with?()`. Se puede obtener la longitud de una cadena con `size()` o `length()`. Las cadenas se pueden **concatenar** con el operador `<<`. El método `split()` divide una cadena en un array basado en un delimitador.
*   **Booleanos**: Representados por `true` y `false`. En Ruby, solo `false` y `nil` (nulo) se consideran "falsy"; **todos los demás valores son "truthy"** (incluyendo 0, cadenas vacías y arrays/hashes vacíos).
*   **Arrays**: Colecciones ordenadas de elementos, indexados por enteros que comienzan en 0. Un array puede contener valores de cualquier tipo, incluso mezclados. Métodos comunes para arrays incluyen `size()`, `length()`, `first()` y `last()`. Se pueden crear arrays de cadenas con la sintaxis `%w()` que no interpreta interpolaciones, o `%W()` que sí lo hace.
*   **Hashes**: Similares a los arrays asociativos de PHP, son colecciones de pares clave-valor donde las claves pueden ser cualquier tipo de objeto (comúnmente cadenas o símbolos). Se accede a los valores mediante su clave.
*   **Símbolos (Symbols)**: Identificadores ligeros e **inmutables**, prefijados con dos puntos (`:`) (por ejemplo, `:name`). Se utilizan cuando la identidad de un objeto es más importante que su contenido. Son especialmente eficientes para usar como claves en hashes, ya que se almacenan una sola vez en memoria, ofreciendo un mejor rendimiento que las cadenas mutables.

**Operadores**
Ruby soporta una variedad de operadores, organizados por precedencia:
*   **Aritméticos**: `+` (suma), `-` (resta), `*` (multiplicación), `/` (división), `%` (módulo), `**` (exponenciación).
*   **De asignación**: `=` (asignación simple), `+=`, `-=`, `*=` (asignación abreviada). Ruby permite la **asignación paralela**, como `x, y = y, x`, que es útil para intercambiar valores.
*   **De comparación**: `==` (igual a), `!=` (no igual a), `<` (menor que), `>` (mayor que), `<=` (menor o igual que), `>=` (mayor o igual que). El operador `**<=>**` (operador de comparación combinada o "spaceship") devuelve -1, 0 o 1 si el operando izquierdo es menor, igual o mayor que el derecho, respectivamente.
*   **Lógicos**: `and` (`&&`), `or` (`||`), `not` (`!`). Se recomienda usar `&&` y `||` para expresiones booleanas y `if`/`unless` para el flujo de control.
*   **Operador de igualdad de casos (`===`)**: También conocido como "triple igual". Este operador no prueba la igualdad estricta, sino que verifica si el operando derecho "es un" tipo o miembro del operando izquierdo (subsunción). Es fundamental para el funcionamiento de las sentencias `case`.
*   **Operador de navegación segura (`&.`)**: Introducido en Ruby 2.3.0, permite llamar a un método solo si el objeto no es `nil`, evitando errores `NoMethodError`.

### 2.2. Expresiones, comentarios y estructuras de control (if, case, while, for)

**Expresiones**
Una expresión en Ruby es una combinación de operadores y operandos que Ruby evalúa para producir un valor. La **precedencia de operadores** determina el orden en que se evalúan las operaciones. Los paréntesis se pueden usar para alterar esta precedencia. En Ruby, **cada línea de código intenta devolver un valor**, y los métodos devuelven implícitamente el resultado de la última expresión evaluada.

**Comentarios**
Los comentarios son esenciales para la claridad del código. En Ruby:
*   Los **comentarios de una sola línea** comienzan con el símbolo de almohadilla (`#`).
*   Los **comentarios multilínea** se definen entre las palabras clave `=begin` y `=end`. Sin embargo, la comunidad Ruby rara vez usa esta notación, priorizando la legibilidad del código sin necesidad de comentarios extensos. La recomendación es que los comentarios expliquen el "por qué" de una decisión de diseño, no el "qué" hace el código, ya que este debe ser autoexplicativo.

**Estructuras de control**
Las estructuras de control modifican el flujo de ejecución secuencial de un script, introduciendo condicionalidad o repetición.
*   **Sentencia `if`**: Permite ejecutar un bloque de código si una condición es verdadera. Puede ir acompañada de una cláusula `else` para el caso en que la condición sea falsa, y `elsif` para verificar múltiples condiciones alternativas.
*   **Sentencia `unless`**: Una "sentencia if negativa", ejecuta el código solo cuando la condición **no se cumple**. No puede tener una cláusula `else`.
*   **Operador ternario**: Una forma concisa de condicionales en una sola línea: `condición ? valor_si_verdadero : valor_si_falso`. Útil para asignar un valor basado en una condición.
*   **Sentencia `case`**: Evalúa una expresión y la compara con varias condiciones definidas por `when`. El bloque de código de la primera condición `when` que coincide se ejecuta. Si ninguna coincide, se ejecuta el bloque `else` (si está presente). La comparación se realiza usando el operador `===` (igualdad de casos). Las condiciones `when` pueden ser rangos, expresiones regulares o clases.
*   **Bucles (Loops)**: Permiten la ejecución repetida de un bloque de código.
    *   **Bucle `while`**: Ejecuta el bloque de código mientras una condición es verdadera.
    *   **Bucle `until`**: Ejecuta el bloque de código mientras una condición es falsa.
    *   **Bucle `for`**: Itera sobre rangos o tipos de datos iterables como arrays.
    *   **Bucle `do`**: Un bucle `loop do...end` es un bucle infinito que debe ser terminado explícitamente con la palabra clave `break`.
    *   **Palabras clave de control de bucle**:
        *   `break`: Sale inmediatamente del bucle.
        *   `next`: Omite el resto de la iteración actual y pasa a la siguiente.
        *   `redo`: Reinicia la ejecución de la iteración actual desde el principio.
*   **Bloque `begin...end`**: Agrupa múltiples sentencias. Se utiliza con frecuencia para el manejo de excepciones (`rescue`, `ensure`) y para encapsular lógica con asignaciones condicionales (`||=`). A diferencia de los bloques pasados a métodos con `{}` o `do..end`, los bloques `begin...end` no se pueden pasar como argumentos a funciones.

### 2.3. Bloques, iteradores (each, map, select), enumerables

**Bloques**
Los bloques son **fragmentos de código** que se encierran entre llaves (`{}`) para bloques de una sola línea, o entre `do...end` para bloques de varias líneas. Los bloques se pueden pasar implícitamente a métodos usando la palabra clave `yield` dentro del método. Los bloques pueden recibir parámetros del método que los llama y tienen acceso a las variables locales del contexto donde fueron definidos. A diferencia de los Procs y Lambdas, los bloques no se pueden guardar directamente como objetos.

**Procs y Lambdas**
Ambos son mecanismos para encapsular bloques de código en objetos que pueden ser almacenados en variables y pasados como argumentos, mejorando la reutilización y flexibilidad del código.
*   **Procs**: Son una forma de procedimiento encapsulado en un objeto de la clase `Proc`. Son más **flexibles** con el manejo de argumentos (no verifican la cantidad de argumentos pasados) y una sentencia `return` dentro de un Proc **sale del método** que contiene el Proc.
*   **Lambdas**: Son una variante de Proc. Se definen con una sintaxis concisa (`-> {}`) y son más **estrictas** con el manejo de argumentos (lanzan un error si la cantidad no coincide). Una sentencia `return` dentro de una Lambda solo sale de la Lambda, no del método que la contiene.

El operador `&` se utiliza para **convertir un bloque en un objeto Proc** (cuando se pasa a un parámetro de método) o para convertir un objeto Proc/Lambda de nuevo en un bloque (cuando se llama a un método que espera un bloque).

**Iteradores (`each`, `map`, `select`) y el módulo Enumerable**
El **módulo `Enumerable`** es fundamental en Ruby para operaciones basadas en colecciones. Proporciona una gran cantidad de métodos para recorrer, buscar, ordenar y manipular colecciones, como Arrays, Hashes y Ranges. Para usar estos métodos, una clase debe incluir el módulo `Enumerable` e implementar su propio método `each`.
*   **`each`**: Es el iterador más básico y fundamental. Permite recorrer cada elemento de una colección. También existe `each_with_index` que, además del elemento, proporciona su índice en la colección.
*   **`map`**: Transforma cada elemento de una colección aplicando un bloque de código y devuelve un **nuevo array** con los resultados transformados. No modifica la colección original.
*   **`select`**: Filtra una colección, devolviendo una **nueva colección** que contiene solo los elementos para los cuales el bloque de código devuelve un valor "truthy". No modifica la colección original. Su opuesto es `reject`, que devuelve los elementos para los que el bloque evalúa a "falsy".
*   **`reduce` (o `inject`)**: Acumula un solo valor a través de los elementos de una colección aplicando una operación binaria definida en un bloque.
