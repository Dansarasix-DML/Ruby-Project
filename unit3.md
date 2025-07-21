# 3. Programación procedural y modular

Ruby es un lenguaje de programación dinámico y de código abierto con énfasis en la simplicidad y la productividad. Es un lenguaje multiparadigma que soporta programación procedural, orientada a objetos y funcional. La programación procedural en Ruby se centra en el uso de métodos (funciones) para organizar el código en tareas específicas, mientras que la modularidad se logra a través de clases y módulos.

### 3.1. Definir y usar métodos
En Ruby, los métodos son bloques de código organizados y reutilizables diseñados para realizar tareas específicas. Simplifican el proceso de codificación, previenen la lógica redundante y hacen que el código sea más fácil de seguir.

Para **definir un método**, se utiliza la palabra clave `def` seguida del nombre del método y una lista opcional de nombres de parámetros entre paréntesis. El cuerpo del método se escribe entre `def` y la palabra clave `end`.

**Ejemplo de definición de método:**
 ```ruby
 def hello(name) #
   "Hello, #{name}" #
 end #
 ```

Para **usar o invocar un método**, se especifica el nombre del método, el objeto sobre el que se invoca (conocido como *receiver*), y cero o más valores de argumento que se asignan a los parámetros del método. Cuando el *receiver* no se especifica explícitamente, se asume que es `self`. Ruby viene con varios métodos incorporados, como `puts` (para imprimir texto en la consola), `gets` (para aceptar la entrada del usuario) y `to_i` (para convertir cadenas a enteros).

**Ejemplo de invocación de método:**
```ruby
  hello("World") # => "Hello, World"
```
Si defines un método pero no lo llamas, no se ejecutará.

### 3.2. Paso de parámetros, valores por defecto y retorno
*   **Paso de parámetros:** Los métodos pueden aceptar **parámetros** para recibir datos. Estos parámetros actúan como variables dentro del cuerpo del método, y sus valores provienen de los argumentos pasados durante la invocación del método. Se pueden pasar múltiples parámetros separándolos con comas.
    **Ejemplo de paso de parámetros:**
    ```ruby
    def demoMethod(msg1, msg2, msg3) #
      puts "\nMessage 1: #{msg1}\nMessage 2: #{msg2}\nMessage 3: #{msg3}" #
    end #
    demoMethod "This is", "another method demo", "these messages are passed arguments" #
    ```

*   **Valores por defecto:** Los parámetros pueden tener **valores por defecto**. Si no se proporciona un valor para un parámetro con valor por defecto durante la llamada al método, se usará su valor por defecto. Si se proporciona, el valor por defecto se anula. Los parámetros por defecto se pueden establecer de derecha a izquierda en la definición del método. Ruby 2.0 introdujo los *keyword arguments* (argumentos de palabra clave), que permiten el nombramiento explícito de los parámetros, mejorando la legibilidad.
    **Ejemplo de parámetros con valores por defecto:**
    ```ruby
    def say(message: "Hello World", before: "<p>", after: "</p>") #
      puts "#{before}#{message}#{after}" #
    end #
    say # => "<p>Hello World</p>"
    say message: "Today is Monday" # => "<p>Today is Monday</p>"
    ```

*   **Retorno de valores:** Un método puede **devolver valores** a la declaración que lo invocó utilizando la palabra clave `return`. Sin `return` explícito, Ruby devuelve el valor de la última expresión evaluada en el método. Un método puede devolver múltiples valores, los cuales se empaquetan implícitamente en un array en el lado del receptor.
    **Ejemplo de retorno de valores:**
    ```ruby
    def concatenate(text1, text2) #
      puts text1 + " " + text2 #
    end #

    def to_upper(text) #
      return text.upcase() # (explicit return)
    end #

    def getSum(x, y) #
      x + y # (implicit return)
    end #
    ```

### 3.3. Concepto de alcance (scope), variables locales, globales, de instancia, de clase
En Ruby, el **alcance (scope)** determina la accesibilidad de las variables y la **visibilidad** dicta cómo y dónde se puede acceder a esas variables dentro del código.

*   **Variables locales:** No tienen ningún prefijo. Su alcance está limitado al "contenedor de declaración" donde se definen, como un método o un bloque `do...end` o corchetes `{}`. Las variables locales declaradas dentro de un bloque son locales a ese bloque y mueren una vez que el bloque se ejecuta. Sin embargo, las variables locales pueden "ocultar" variables previamente definidas con el mismo nombre dentro del alcance del bloque, sin sobrescribirlas permanentemente fuera del bloque.
    **Ejemplo de variable local:**
    ```ruby
    local_variable = "local" #
    p local_variable # => local
    ```

*   **Variables globales:** Se prefijan con el símbolo `$`. Son accesibles desde cualquier parte del programa Ruby, lo que las hace muy flexibles pero también potencialmente riesgosas debido a su alcance sin restricciones. Si se llama a una variable global "indefinida", devolverá `nil` en lugar de generar un error. Aunque son fáciles de usar, se desaconseja fuertemente su uso en favor de las constantes.
    **Ejemplo de variable global:**
    ```ruby
    $total_animals = 0 #
    class Cat #
    def initialize #
      $total_animals += 1 #
    end #
    end #
    bob = Cat.new() #
    puts $total_animals #=> 1
    ```

*   **Variables de instancia:** Se prefijan con el símbolo `@`. Se inicializan al crear un objeto y son accesibles a través de métodos de instancia. Cada objeto tiene su propia copia de las variables de instancia, lo que significa que no se comparten entre instancias de la misma clase. Ruby proporciona métodos de acceso (`attr_reader`, `attr_writer`, `attr_accessor`) que generan automáticamente métodos *getter* y *setter* para las variables de instancia.
    **Ejemplo de variable de instancia:**
    ```ruby
    class Person #
      def initialize(first_name, last_name) #
        @first_name = first_name #
        @last_name = last_name #
      end #
      def full_name #
        puts "#{@first_name} #{@last_name}" #
      end #
    end #
    ```

*   **Variables de clase:** Se prefijan con el símbolo `@@`. Son variables que se comparten entre todas las instancias de una clase e incluso las subclases. Son útiles para almacenar información relevante para todos los objetos de una clase. Es necesario tener precaución al usarlas debido a su naturaleza compartida, lo que puede llevar a resultados inesperados si no se gestionan correctamente.
    **Ejemplo de variable de clase:**
    ```ruby
    class Vehicle #
      @@number_of_vehicles = 0 #
      def initialize #
        @@number_of_vehicles += 1 #
      end #
      def self.total_vehicles #
        @@number_of_vehicles #
      end #
    end #
    car = Vehicle.new #
    truck = Vehicle.new #
    puts Vehicle.total_vehicles # Output: 2
    ```
