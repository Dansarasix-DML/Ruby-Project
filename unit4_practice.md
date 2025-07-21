# Ejercicios de Programación Orientada a Objetos (POO) en Ruby

---

#### 1. Clases y Objetos: Definición Básica y Atributos
**Ejercicio:** Crea una clase llamada `Mascota`. Define su constructor (`initialize`) para que acepte un `nombre` y una `especie`. Almacena estos como variables de instancia (`@nombre`, `@especie`). Luego, crea una instancia de `Mascota` (un objeto) para tu mascota favorita y muestra su nombre y especie.

**Solución:**
```ruby
class Mascota
  def initialize(nombre, especie) # Constructor
    @nombre = nombre   # Variable de instancia
    @especie = especie # Variable de instancia
  end

  def info
    puts "Mi mascota se llama #{@nombre} y es un/a #{@especie}."
  end
end

mi_mascota = Mascota.new("Fido", "perro") # Creación de objeto (instancia)
mi_mascota.info # Llamada a método de instancia
```

#### 2. Clases y Objetos: Métodos de Instancia
**Ejercicio:** Extiende la clase `Mascota` del ejercicio anterior. Añade un método de instancia llamado `hacer_sonido` que imprima un sonido específico para la especie. Por ejemplo, si la especie es "perro", imprime "¡Guau!".

**Solución:**
```ruby
class Mascota
  def initialize(nombre, especie)
    @nombre = nombre
    @especie = especie
  end

  def info
    puts "Mi mascota se llama #{@nombre} y es un/a #{@especie}."
  end

  def hacer_sonido # Método de instancia
    case @especie
    when "perro"
      puts "¡Guau!"
    when "gato"
      puts "¡Miau!"
    when "pajaro"
      puts "¡Pío pío!"
    else
      puts "La mascota no hace un sonido conocido."
    end
  end
end

mi_perro = Mascota.new("Max", "perro")
mi_gato = Mascota.new("Luna", "gato")

mi_perro.hacer_sonido
mi_gato.hacer_sonido
```

#### 3. Clases y Objetos: Variables y Métodos de Clase
**Ejercicio:** Modifica la clase `Mascota` para que mantenga un registro del **número total de mascotas creadas** utilizando una variable de clase (`@@conteo_total_mascotas`). Crea un método de clase (`self.total_mascotas`) que devuelva este conteo.

**Solución:**
```ruby
class Mascota
  @@conteo_total_mascotas = 0 # Variable de clase

  def initialize(nombre, especie)
    @nombre = nombre
    @especie = especie
    @@conteo_total_mascotas += 1 # Incrementa el contador cada vez que se crea un objeto
  end

  def self.total_mascotas # Método de clase
    @@conteo_total_mascotas
  end

  def info
    puts "Mi mascota se llama #{@nombre} y es un/a #{@especie}."
  end
end

Mascota.new("Bobby", "pez")
Mascota.new("Silvestre", "gato")
Mascota.new("Piolin", "canario")

puts "Total de mascotas creadas: #{Mascota.total_mascotas}" # Acceso al método de clase
```

#### 4. Herencia: Clase Padre y Clase Hija
**Ejercicio:** Crea una clase padre llamada `Vehiculo` con un método `arrancar` que imprima "El vehículo arranca.". Luego, crea una clase hija `Coche` que herede de `Vehiculo`. Instancia un `Coche` y llama a su método `arrancar`.

**Solución:**
```ruby
class Vehiculo # Clase padre
  def arrancar
    puts "El vehículo arranca."
  end
end

class Coche < Vehiculo # Coche hereda de Vehiculo
  # Coche hereda automáticamente el método arrancar
end

mi_coche = Coche.new
mi_coche.arrancar # Llamando al método heredado
```

#### 5. Herencia: Uso de `super` en el Constructor
**Ejercicio:** Expande las clases `Vehiculo` y `Coche`. El constructor de `Vehiculo` debe aceptar y almacenar un `@marca`. El constructor de `Coche` debe aceptar `marca` y `modelo`, y usar `super` para pasar la `marca` al constructor de `Vehiculo`.

**Solución:**
```ruby
class Vehiculo
  def initialize(marca)
    @marca = marca
  end

  def arrancar
    puts "El vehículo #{@marca} arranca."
  end
end

class Coche < Vehiculo
  def initialize(marca, modelo)
    super(marca) # Llama al constructor de la superclase y le pasa 'marca'
    @modelo = modelo
  end

  def info
    puts "Es un coche #{@marca} modelo #{@modelo}."
  end
end

mi_coche_deportivo = Coche.new("Ferrari", "F8 Tributo")
mi_coche_deportivo.info
mi_coche_deportivo.arrancar
```

#### 6. Herencia: Sobreescritura de Métodos
**Ejercicio:** En la clase `Coche` (o una nueva clase `Moto` que también herede de `Vehiculo`), **sobrescribe** el método `arrancar` para que imprima un mensaje más específico para un coche/moto. Mantén el método original en `Vehiculo`.

**Solución:**
```ruby
class Vehiculo
  def arrancar
    puts "El vehículo arranca de forma genérica."
  end
end

class Coche < Vehiculo
  def arrancar # Sobreescribe el método arrancar de Vehiculo
    puts "El coche enciende el motor con la llave."
  end
end

class Moto < Vehiculo
  def arrancar # Sobreescribe el método arrancar de Vehiculo
    puts "La moto se enciende con el botón."
  end
end

vehiculo_generico = Vehiculo.new
vehiculo_generico.arrancar

coche_especifico = Coche.new
coche_especifico.arrancar

moto_especifica = Moto.new
moto_especifica.arrancar
```

#### 7. Herencia: Jerarquía de Clases
**Ejercicio:** Diseña una jerarquía de clases para `Animal`, `Mamifero` (hereda de `Animal`), y `Perro` (hereda de `Mamifero`). Cada clase debe tener un método `presentarse` que imprima su tipo (e.g., "Soy un animal", "Soy un mamífero", "Soy un perro"). Demuestra cómo se llaman estos métodos a través de la jerarquía.

**Solución:**
```ruby
class Animal # Clase más genérica
  def presentarse
    puts "Soy un animal."
  end
end

class Mamifero < Animal # Mamifero hereda de Animal
  def presentarse # Sobreescribe el método de Animal
    puts "Soy un mamífero."
  end
end

class Perro < Mamifero # Perro hereda de Mamifero
  def presentarse # Sobreescribe el método de Mamifero
    puts "Soy un perro."
  end
end

mi_animal = Animal.new
mi_mamifero = Mamifero.new
mi_perro = Perro.new

mi_animal.presentarse
mi_mamifero.presentarse
mi_perro.presentarse
```

#### 8. Métodos de Acceso: `attr_reader`
**Ejercicio:** Crea una clase `Usuario` con atributos `@nombre_usuario` y `@email`. Usa `attr_reader` para que solo se puedan leer estos atributos desde fuera de la clase. Intenta modificarlos después de la creación para ver el error.

**Solución:**
```ruby
class Usuario
  attr_reader :nombre_usuario, :email # Crea métodos 'getter' para :nombre_usuario y :email

  def initialize(nombre_usuario, email)
    @nombre_usuario = nombre_usuario
    @email = email
  end
end

usuario = Usuario.new("john_doe", "john.doe@example.com")
puts "Nombre de usuario: #{usuario.nombre_usuario}" # Acceso de lectura
puts "Email: #{usuario.email}" # Acceso de lectura

# Intento de modificación (generará un error NoMethodError)
# usuario.nombre_usuario = "jane_doe" # Esto causaría un error porque no hay attr_writer
```

#### 9. Métodos de Acceso: `attr_writer`
**Ejercicio:** Crea una clase `Articulo` con un atributo `@stock` inicializado en 0. Usa `attr_writer` para permitir solo la modificación (escritura) de `stock` desde fuera de la clase. Demuestra cómo se puede cambiar el `stock`.

**Solución:**
```ruby
class Articulo
  attr_writer :stock # Crea un método 'setter' para :stock
  attr_reader :nombre # Para poder leer el nombre

  def initialize(nombre, stock_inicial = 0)
    @nombre = nombre
    @stock = stock_inicial
  end

  def mostrar_stock
    puts "El artículo #{@nombre} tiene #{@stock} unidades en stock."
  end
end

manzanas = Articulo.new("Manzanas")
manzanas.mostrar_stock

manzanas.stock = 50 # Modifica el valor de @stock usando el setter
manzanas.mostrar_stock
```

#### 10. Métodos de Acceso: `attr_accessor`
**Ejercicio:** Crea una clase `Configuracion` con un atributo `@idioma`. Usa `attr_accessor` para permitir tanto la lectura como la escritura de `idioma`. Demuestra ambas operaciones.

**Solución:**
```ruby
class Configuracion
  attr_accessor :idioma # Crea métodos 'getter' y 'setter' para :idioma

  def initialize(idioma_defecto = "es")
    @idioma = idioma_defecto
  end

  def mostrar_idioma
    puts "El idioma actual es: #{@idioma}"
  end
end

mi_config = Configuracion.new
mi_config.mostrar_idioma # Lee el valor (getter)

mi_config.idioma = "en" # Modifica el valor (setter)
mi_config.mostrar_idioma # Lee el nuevo valor
```

#### 11. Módulos y Mixins: `include` para Métodos de Instancia
**Ejercicio:** Define un módulo `Saludable` con un método de instancia `esta_sano?` que imprima "Me siento bien!". Incluye este módulo en una clase `Persona` y en una clase `Vegetal` (¡sí, un vegetal puede sentirse "sano" en un contexto de juego!). Demuestra su uso en ambas.

**Solución:**
```ruby
module Saludable # Definición de un módulo
  def esta_sano?
    puts "Me siento bien!"
  end
end

class Persona
  include Saludable # Incluye el módulo, sus métodos se vuelven de instancia
  attr_accessor :nombre

  def initialize(nombre)
    @nombre = nombre
  end

  def saludar
    puts "Hola, soy #{@nombre}."
    esta_sano? # Llama al método del mixin
  end
end

class Vegetal
  include Saludable
  attr_accessor :tipo

  def initialize(tipo)
    @tipo = tipo
  end

  def describir
    puts "Soy un vegetal tipo #{@tipo}."
    esta_sano? # Llama al método del mixin
  end
end

juan = Persona.new("Juan")
juan.saludar

zanahoria = Vegetal.new("Zanahoria")
zanahoria.describir
```

#### 12. Módulos y Mixins: `extend` para Métodos de Clase
**Ejercicio:** Crea un módulo `ContadorDeCreaciones` con un método de clase `conteo_creaciones` (que podría llevar un conteo global, por ejemplo). Usa `extend` para añadir este método como un método de clase a una clase `FactoriaDeObjetos`.

**Solución:**
```ruby
module ContadorDeCreaciones
  def conteo_creaciones
    # Esto es solo un ejemplo, un contador real necesitaría una variable de clase
    puts "Se han realizado muchas creaciones aquí."
  end
end

class FactoriaDeObjetos
  extend ContadorDeCreaciones # Añade los métodos del módulo como métodos de clase
  # ... otros métodos de factoría
end

FactoriaDeObjetos.conteo_creaciones # Llamada al método de clase del módulo
```

#### 13. Módulos y Mixins: Módulo `Comparable`
**Ejercicio:** Crea una clase `Cancion` con atributos `titulo` y `duracion_segundos`. Incluye el módulo `Comparable`. Define el operador `pack <=> other` para comparar canciones basándose en su `duracion_segundos`. Luego, compara varias canciones usando `<`, `>`, `==`, etc.

**Solución:**
```ruby
class Cancion
  include Comparable # Habilita operadores de comparación como <, >, ==

  attr_reader :titulo, :duracion_segundos

  def initialize(titulo, duracion_segundos)
    @titulo = titulo
    @duracion_segundos = duracion_segundos
  end

  # Define el operador de comparación para Comparable
  def <=>(other)
    duracion_segundos <=> other.duracion_segundos
  end

  def info
    "\"#{@titulo}\" (#{duracion_segundos} segundos)"
  end
end

cancion1 = Cancion.new("Bohemian Rhapsody", 354) # 5:54
cancion2 = Cancion.new("Stairway to Heaven", 482) # 8:02
cancion3 = Cancion.new("Imagine", 183) # 3:03
cancion4 = Cancion.new("Bohemian Rhapsody (Live)", 354)

puts "#{cancion1.info} < #{cancion2.info}: #{cancion1 < cancion2}"
puts "#{cancion2.info} > #{cancion3.info}: #{cancion2 > cancion3}"
puts "#{cancion1.info} == #{cancion4.info}: #{cancion1 == cancion4}"
puts "#{cancion1.info} >= #{cancion3.info}: #{cancion1 >= cancion3}"
```

#### 14. Módulos y Mixins: Módulo `Enumerable`
**Ejercicio:** Crea una clase `ListaDeTareas` que contenga una colección interna de tareas (e.g., un Array). Incluye el módulo `Enumerable`. Implementa el método `each` para que `Enumerable` pueda operar sobre tu colección. Luego, utiliza métodos de `Enumerable` como `map` o `select` en una instancia de `ListaDeTareas`.

**Solución:**
```ruby
class ListaDeTareas
  include Enumerable # Permite usar métodos como map, select, etc.

  def initialize
    @tareas = [] # Colección interna de tareas
  end

  def agregar_tarea(tarea)
    @tareas << tarea
  end

  # Implementación requerida por Enumerable
  def each(&block)
    @tareas.each(&block)
  end
end

mi_lista = ListaDeTareas.new
mi_lista.agregar_tarea("Comprar leche")
mi_lista.agregar_tarea("Pagar facturas")
mi_lista.agregar_tarea("Estudiar Ruby POO")
mi_lista.agregar_tarea("Llamar a mamá")

# Usando métodos de Enumerable
puts "Tareas con más de 10 caracteres:"
mi_lista.select { |tarea| tarea.length > 10 }.each { |tarea| puts "- #{tarea}" }

puts "\nTodas las tareas en mayúsculas:"
mi_lista.map { |tarea| tarea.upcase }.each { |tarea| puts "- #{tarea}" }
```

#### 15. Módulos y Mixins: Módulos como Espacios de Nombres (`Namespace`)
**Ejercicio:** Crea dos módulos anidados, `MiApp::Controladores` y `MiApp::Modelos`. Dentro de `Controladores`, define una clase `DashboardController`. Dentro de `Modelos`, define una clase `Usuario`. Demuestra cómo se accede a estas clases usando el operador `::` para evitar conflictos de nombres.

**Solución:**
```ruby
module MiApp # Módulo principal como espacio de nombres
  module Controladores # Módulo anidado para controladores
    class DashboardController
      def initialize
        puts "DashboardController inicializado."
      end

      def mostrar_panel
        puts "Mostrando el panel de control."
      end
    end
  end

  module Modelos # Módulo anidado para modelos
    class Usuario
      def initialize(nombre)
        @nombre = nombre
        puts "Usuario #{@nombre} del modelo inicializado."
      end

      def obtener_nombre
        @nombre
      end
    end
  end
end

# Accediendo a las clases usando los espacios de nombres
dashboard = MiApp::Controladores::DashboardController.new
dashboard.mostrar_panel

usuario_app = MiApp::Modelos::Usuario.new("Alice")
puts "Nombre obtenido: #{usuario_app.obtener_nombre}"
```

#### 16. Módulos y Mixins: Aplicando el Principio DRY con Mixins
**Ejercicio:** Considera dos clases, `Gato` y `Perro`, que tienen en común un método `dormir` que imprime "Zzzzz...". Refactoriza este comportamiento en un módulo `Dormilon` y utiliza `include` en ambas clases para aplicar el principio DRY (Don't Repeat Yourself).

**Solución:**
```ruby
module Dormilon # Módulo para el comportamiento de dormir
  def dormir
    puts "Zzzzz..."
  end
end

class Gato
  include Dormilon # Incluye el mixin para el comportamiento de dormir
  attr_accessor :nombre

  def initialize(nombre)
    @nombre = nombre
  end

  def ronronear
    puts "#{@nombre} está ronroneando."
  end
end

class Perro
  include Dormilon # Incluye el mixin
  attr_accessor :nombre

  def initialize(nombre)
    @nombre = nombre
  end

  def ladrar
    puts "#{@nombre} está ladrando."
  end
end

mi_gato = Gato.new("Misifu")
mi_perro = Perro.new("Buddy")

mi_gato.ronronear
mi_gato.dormir # Usa el método del mixin

mi_perro.ladrar
mi_perro.dormir # Usa el método del mixin
```

#### 17. Combinación de Conceptos: Clase con Atributos, Métodos y Uso de Módulos
**Ejercicio:** Crea una clase `Punto` con coordenadas `@x` y `@y`. Utiliza `attr_accessor` para ambas. Incluye el módulo `Comparable` y define el operador `<=>` para comparar puntos basándose en su distancia al origen (calcula la distancia usando la fórmula `sqrt(x^2 + y^2)`).

**Solución:**
```ruby
class Punto
  include Comparable
  attr_accessor :x, :y

  def initialize(x, y)
    @x = x
    @y = y
  end

  def distancia_al_origen
    Math.sqrt(x**2 + y**2) # Calcula la distancia
  end

  def <=>(other)
    distancia_al_origen <=> other.distancia_al_origen
  end

  def to_s # Método para representar el objeto como string
    "(#{x}, #{y})"
  end
end

p1 = Punto.new(3, 4) # Distancia: 5
p2 = Punto.new(1, 1) # Distancia: ~1.41
p3 = Punto.new(5, 0) # Distancia: 5

puts "#{p1} vs #{p2}: #{p1 <=> p2}" # 1 (p1 > p2)
puts "#{p1} == #{p3}: #{p1 == p3}" # true
puts "#{p2} < #{p3}: #{p2 < p3}"   # true
```

#### 18. Combinación de Conceptos: Herencia y Atributos
**Ejercicio:** Crea una clase `Empleado` con `nombre` y `salario_base`. Luego, crea una clase `Gerente` que herede de `Empleado` y añada un atributo `bono`. El método `salario_total` de `Gerente` debe incluir el `salario_base` de `Empleado` y su propio `bono`.

**Solución:**
```ruby
class Empleado
  attr_accessor :nombre, :salario_base

  def initialize(nombre, salario_base)
    @nombre = nombre
    @salario_base = salario_base
  end

  def salario_total
    salario_base
  end
end

class Gerente < Empleado
  attr_accessor :bono

  def initialize(nombre, salario_base, bono)
    super(nombre, salario_base) # Llama al constructor de la clase padre
    @bono = bono
  end

  def salario_total # Sobreescribe el método para incluir el bono
    super + @bono # Llama al salario_total del padre y le suma el bono
  end
end

empleado = Empleado.new("Ana", 50000)
gerente = Gerente.new("Carlos", 70000, 10000)

puts "Salario total de #{empleado.nombre}: $#{empleado.salario_total}"
puts "Salario total de #{gerente.nombre}: $#{gerente.salario_total}"
```

#### 19. Uso de `to_s` para Representación de Objetos
**Ejercicio:** En la clase `Mascota` (del ejercicio 1 o una nueva versión), sobreescribe el método `to_s`. Este método especial se utiliza para obtener una representación de cadena del objeto. Haz que devuelva una cadena legible como "Una mascota llamada [nombre] de especie [especie]".

**Solución:**
```ruby
class Mascota
  attr_accessor :nombre, :especie

  def initialize(nombre, especie)
    @nombre = nombre
    @especie = especie
  end

  def to_s # Sobreescribe el método to_s para una representación legible
    "Una mascota llamada #{@nombre} de especie #{@especie}."
  end
end

mi_tortuga = Mascota.new("Shelly", "tortuga")
puts mi_tortuga # Ruby llamará automáticamente a to_s aquí
```

#### 20. Creación de Objetos a partir de Datos Dinámicos
**Ejercicio:** Simula la creación de objetos `Libro` a partir de un arreglo de hashes. Cada hash contiene `:titulo` y `:autor`. Itera sobre el arreglo y crea una instancia de `Libro` para cada entrada.

**Solución:**
```ruby
class Libro
  attr_accessor :titulo, :autor

  def initialize(titulo, autor)
    @titulo = titulo
    @autor = autor
  end

  def to_s
    "Libro: \"#{@titulo}\" por #{@autor}."
  end
end

datos_libros = [ # Arreglo de hashes
  { titulo: "Cien años de soledad", autor: "Gabriel García Márquez" },
  { titulo: "Don Quijote de la Mancha", autor: "Miguel de Cervantes" },
  { titulo: "El Principito", autor: "Antoine de Saint-Exupéry" }
]

biblioteca = []
datos_libros.each do |data| # Iteración sobre el arreglo
  libro = Libro.new(data[:titulo], data[:autor]) # Creación de objetos Libro
  biblioteca << libro
end

puts "Mi Biblioteca:"
biblioteca.each do |libro|
  puts libro
end
```

---

Para solidificar tu comprensión de la POO en Ruby, piensa en ella como una **fábrica de juguetes modular**. 
Cada **clase** es el plano maestro para construir un tipo específico de juguete (como un "Robot" o una "Muñeca").
Cada vez que ensamblas un juguete, estás creando un **objeto**, una instancia única de ese plano. 
La **herencia** es como si tuvieras un plano base para "Vehículos" y luego crearas planos más específicos como "Coches" y "Camiones" 
que automáticamente heredan características básicas (como "tener ruedas") y luego añaden las suyas propias. 
Los **métodos de acceso** (`attr_reader`, `attr_writer`, `attr_accessor`) son como controles remotos para tus juguetes: 
algunos solo te permiten ver sus características (como el nivel de batería), otros solo te permiten cambiarlas (como el color), 
y otros te permiten ambas cosas (como la velocidad). Finalmente, los **módulos y mixins** son como "kits de mejora" 
que puedes añadir a cualquier juguete, independientemente de su tipo, para darle nuevas habilidades (como un "kit de sonido" que cualquier juguete puede usar para hacer ruidos). 
Estos kits te permiten reutilizar funcionalidades sin tener que rediseñar todo desde cero, haciendo que tu fábrica sea más eficiente y versátil.
