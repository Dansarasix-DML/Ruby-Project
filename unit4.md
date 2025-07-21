# **4. Programación Orientada a Objetos (OOP) en Ruby**

Ruby es, por diseño, un lenguaje de programación fundamentalmente orientado a objetos (OOP). Esto significa que, a diferencia de algunos otros lenguajes que han evolucionado para incluir OOP, Ruby fue concebido con este paradigma en su núcleo, haciendo que **casi todo en Ruby sea un objeto**. Esta filosofía impregna la forma en que los desarrolladores de Ruby piensan y escriben código.

---

### 4.1. Clases, objetos, `self`, variables de instancia

En el corazón de la OOP están las **clases** y los **objetos**.

*   **Clases:**
    Una clase es un **"plano" (blueprint) o una abstracción** de una entidad del mundo real llevada al mundo de la programación. Define las características (atributos) y los comportamientos (métodos) que tendrán los objetos creados a partir de ella. En Ruby, las clases se definen usando la palabra clave `class` seguida del nombre de la clase, que **debe comenzar con una letra mayúscula** (convención conocida como CamelCase). La definición de la clase se cierra con la palabra clave `end`.

*   **Objetos:**
    Un objeto es una **"instancia" específica** de una clase. Mientras que la clase es la definición genérica, el objeto es la implementación concreta con sus propios datos. Por ejemplo, `String`, `Integer`, `Float`, `TrueClass` y `Array` son tipos de objetos en Ruby. Para crear un nuevo objeto a partir de una clase, se utiliza el método `.new`. Las clases también pueden crearse dinámicamente utilizando `Class.new`.

*   **`self`:**
    La palabra clave `self` en Ruby es crucial para entender el contexto de ejecución del código. **Siempre hay un "receptor implícito"** para todas las llamadas a métodos en Ruby, y `self` hace referencia a este receptor actual.
    *   Dentro de un método de instancia, `self` se refiere al **objeto actual** que invocó el método.
    *   Dentro de un método de clase o directamente en la definición de una clase (fuera de cualquier método de instancia), `self` se refiere a la **clase misma**.
    *   `self` ayuda a **desambiguar** cuándo se está llamando a un método o a una variable local con el mismo nombre. También se utiliza para **cambiar el receptor** y definir métodos de clase directamente en la clase.

*   **Variables de instancia:**
    Las variables de instancia son contenedores que **almacenan datos únicos para cada objeto** (instancia) de una clase. Se definen prefijándolas con el símbolo **`@`** (por ejemplo, `@nombre_completo`). Solo son accesibles mediante métodos dentro de la propia clase o a través de "métodos de acceso" (accessors). Si una variable de instancia no ha sido definida, su valor será `nil`. Las variables de instancia no se comparten entre diferentes objetos de la misma clase.

---

### 4.2. Métodos de instancia y de clase, inicialización (`initialize`)

*   **Métodos de instancia:**
    Son los **comportamientos o acciones que un objeto puede realizar**. Se definen dentro de la clase usando las palabras clave `def` y `end`, como cualquier otra función en Ruby. Se invocan directamente sobre una instancia específica de la clase (por ejemplo, `mi_objeto.metodo_instancia`).

*   **Métodos de clase:**
    También conocidos como métodos estáticos, son **métodos que pertenecen a la clase misma**, no a una instancia particular de ella. Se definen anteponiendo `self.` o el nombre de la clase al nombre del método (por ejemplo, `def self.mi_metodo_clase` o `def MyClass.mi_metodo_clase`). Son útiles para funcionalidades que son relevantes para la clase en su conjunto, como un contador de instancias creadas (`@@count`).

*   **Inicialización (`initialize`):**
    El método `initialize` es el **constructor especial de una clase en Ruby**. **Se invoca automáticamente cada vez que se crea una nueva instancia** de la clase utilizando `.new`. Su propósito principal es configurar el estado inicial del objeto, generalmente asignando los argumentos pasados a las variables de instancia del objeto. Aunque puede aceptar parámetros, el valor de retorno de `initialize` se descarta; el objeto recién creado es lo que se devuelve.

*   **Métodos de acceso (Accessors):**
    Ruby proporciona una forma concisa de crear métodos para leer y/o escribir directamente variables de instancia.
    *   `attr_reader :variable_name`: Crea un método de lectura (getter) para `@variable_name`, permitiendo obtener su valor fuera de la clase.
    *   `attr_writer :variable_name`: Crea un método de escritura (setter) para `@variable_name`, permitiendo modificar su valor fuera de la clase.
    *   `attr_accessor :variable_name`: Combina ambos, creando un getter y un setter para la variable de instancia, permitiendo tanto leer como modificarla. Estos métodos son un atajo para definir manualmente los `getters` y `setters`.

---

### 4.3. Herencia, módulos, mixins, visibilidad de métodos (public, private, protected)

*   **Herencia:**
    La herencia es un concepto fundamental en OOP que permite a una clase (la subclase o clase hija) **adquirir propiedades y métodos de otra clase** (la superclase o clase padre). Esto facilita la **reutilización de código** y el establecimiento de una jerarquía de clases. En Ruby, la herencia se indica con el operador **`<`** (por ejemplo, `class Hijo < Padre`). Una subclase puede utilizar las funcionalidades de su clase padre, añadir nuevas características o personalizar las heredadas. El método `super()` se utiliza para llamar a un método con el mismo nombre en la superclase, incluyendo el constructor `initialize`. Es importante destacar que **Ruby solo admite herencia simple**, lo que significa que una clase solo puede heredar directamente de una única clase padre.

*   **Módulos:**
    Los módulos en Ruby son una forma de **agrupar colecciones de métodos y constantes**. A diferencia de las clases, los módulos no pueden ser instanciados directamente. Sirven principalmente para dos propósitos:
    *   **Namespaces:** Permiten organizar el código lógicamente y **evitar conflictos de nombres** entre clases o módulos que puedan tener el mismo nombre pero diferente funcionalidad. Para acceder a una clase dentro de un módulo, se utiliza el operador de resolución de ámbito `::` (por ejemplo, `Modulo::Clase`).
    *   **Mixins:** Son el mecanismo de Ruby para **compartir funcionalidades (métodos) entre múltiples clases** sin recurrir a la herencia clásica, que solo permite una superclase. Esto es clave para adherirse al principio DRY (Don't Repeat Yourself).

*   **Mixins:**
    Para usar un módulo como un mixin, se emplean dos métodos principales:
    *   `include Modulo`: Cuando se usa `include`, los métodos del módulo se convierten en **métodos de instancia** de la clase que lo incluye. Esto permite que todas las instancias de la clase accedan a esos métodos.
    *   `extend Modulo`: Cuando se usa `extend`, los métodos del módulo se convierten en **métodos de clase** de la clase que los extiende. Esto permite llamar a esos métodos directamente sobre la clase misma.

*   **Visibilidad de métodos (public, private, protected):**
    Ruby tiene tres niveles de acceso para los métodos, que controlan cómo y dónde pueden ser llamados.
    *   **`Public`:** Son los métodos predeterminados en Ruby. Describen el comportamiento externo de un objeto y **pueden ser llamados desde cualquier lugar**, tanto dentro como fuera del objeto.

    *   **`Private`:** Los métodos privados **no son accesibles desde fuera del objeto con un receptor explícito** (es decir, no puedes llamar `objeto.metodo_privado`). Solo pueden ser llamados con un **receptor implícito** (es decir, solo `metodo_privado` dentro de la propia clase o subclases). Su propósito es ser utilizados internamente por el objeto, para encapsular lógica que no debería ser expuesta directamente.

    *   **`Protected`:** Los métodos protegidos son similares a los privados en que no pueden ser llamados desde fuera del objeto por cualquier instancia. Sin embargo, a diferencia de los métodos privados, **pueden ser llamados con un receptor explícito si ese receptor es `self` (el objeto actual) o un objeto de la misma clase**. Son útiles para comparaciones o interacciones entre objetos del mismo tipo donde se necesita acceder a la lógica interna de otros objetos relacionados.

---

### 4.4. Buenas prácticas para código reutilizable

La filosofía de Ruby prioriza la **legibilidad y la facilidad de escritura**. Estas son algunas prácticas recomendadas para escribir código Ruby limpio y reutilizable:

*   **Principio DRY (Don't Repeat Yourself):**
    Este principio fundamental en el desarrollo de software establece que **no se debe repetir el código**. En Ruby, esto se fomenta a través de la reutilización de funciones, herramientas y bibliotecas, y refactorizando el código para eliminar duplicidades, como el uso de un solo formulario para múltiples acciones web. Las gems (bibliotecas Ruby) son un excelente ejemplo de reutilización, ya que ofrecen soluciones probadas y optimizadas para problemas comunes.

*   **Foco en la legibilidad del código:**
    *   **Lectura como oración:** El código Ruby está diseñado para leerse de forma natural, casi como una oración.
    *   **Evitar comentarios excesivos:** La comunidad Ruby desaconseja el uso abundante de comentarios, ya que el **código bien escrito debe ser autoexplicativo**. Los comentarios deben usarse para explicar el "por qué" de una decisión de diseño, no el "qué" hace el código.
    *   **Paréntesis opcionales:** El uso de paréntesis en las llamadas a métodos es opcional, lo que contribuye a que el código se lea más como lenguaje natural. Sin embargo, se recomienda usarlos en llamadas de funciones anidadas o cuando pueda generar ambigüedad.
    *   **Nombres de métodos con `?` y `!`:** Los métodos que devuelven un valor booleano convencionalmente terminan con un signo de interrogación (`?`), como `.empty?` o `.odd?`. Los métodos que modifican el objeto (`destructive methods`) suelen terminar con un signo de exclamación (`!`), conocido como "bang" (por ejemplo, `.upcase!`).
    *   **`snake_case`:** Se prefiere el formato `snake_case` (palabras separadas por guiones bajos, todo en minúsculas) para nombres de variables y métodos, ya que mejora la legibilidad. Los desarrolladores Ruby dedican tiempo a nombrar métodos y variables de forma significativa.
    *   **Símbolos para claves de hash:** Usar símbolos como claves en hashes se considera una buena práctica porque son inmutables y eficientes en memoria, lo que conduce a búsquedas más rápidas y código más legible.

*   **Estructura y modularidad:**
    *   **Métodos concisos:** Los métodos deben ser cortos, concisos y tener una única responsabilidad. Si un método excede las 10 líneas, se recomienda dividirlo en métodos auxiliares más pequeños y enfocados.
    *   **Módulos como `namespaces`:** Utilizar módulos para agrupar clases y módulos relacionados ayuda a organizar el código y evitar colisiones de nombres.
    *   **Single Responsibility Principle (SRP):** Los módulos deben adherirse a este principio, enfocándose en una sola preocupación o funcionalidad, lo que asegura que sean reutilizables y fáciles de entender.
    *   **Documentación:** Proporcionar documentación integral para módulos y mixins, explicando su propósito y uso.

*   **Manejo de colecciones:**
    *   **Métodos `Enumerable`:** Utilizar los potentes métodos del módulo `Enumerable` (como `map`, `select`, `each`, `reduce`) para realizar operaciones en colecciones, ya que resultan en código más expresivo y eficiente. `each` es generalmente preferido sobre el `for` loop para iterar.
    *   **Evitar mutación durante la iteración:** Si bien Ruby permite colecciones mutables, es una buena práctica evitar modificarlas mientras se itera sobre ellas para prevenir comportamientos inesperados. Considera duplicar la colección o acumular cambios para aplicarlos después.
    *   **Clase `Set`:** Para colecciones donde la unicidad de los elementos es crucial, la clase `Set` es una opción más eficiente que los arrays.

*   **Manejo de flujo de control:**
    *   Ruby ofrece varias estructuras de control como `if`, `else`, `elsif`, `case`, `while`, `until`. Los "modificadores de declaración" (`if` y `unless` al final de una línea) y los operadores ternarios también mejoran la expresividad.
    *   Las palabras clave `break`, `next` y `redo` permiten un control más preciso de la ejecución dentro de los bucles.
    *   Los `blocks`, `procs` y `lambdas` son herramientas poderosas para la reutilización de código y la flexibilidad, permitiendo encapsular lógica y manejar el comportamiento de variables de manera idiomática en Ruby.

---

**Analogia:**

Piensa en la Programación Orientada a Objetos en Ruby como un gran estudio de cine.

*   Las **Clases** son los **guiones** que describen a los personajes (atributos) y lo que hacen (métodos). Por ejemplo, un guion para un "Héroe" podría definir que tiene un nombre, una fuerza y la capacidad de "salvar el día".
*   Los **Objetos** son los **actores** que interpretan esos guiones. Cada actor (objeto) tiene su propio nombre, fuerza, etc., pero todos siguen el guion del "Héroe" y pueden "salvar el día". Cada actor es único, pero se basa en el mismo "plano" de personaje.
*   **`self`** sería como el **actor diciendo "yo" o "mi personaje"** mientras está interpretando. Cuando el actor dice "yo salto", se refiere a que su personaje salta, no a la persona real que lo interpreta.
*   Las **variables de instancia** son como los **atributos específicos de cada actor en su papel** (su altura en el personaje, el color de su disfraz). Pertenecen a ese actor en ese papel y no son compartidas por otros actores que interpretan el mismo tipo de personaje.
*   Los **métodos de instancia** son las **acciones que el actor realiza en su papel** (luchar, volar, hablar).
*   Los **métodos de clase** son las **capacidades que tiene el propio estudio de cine** (por ejemplo, saber cuántas películas de "Héroe" se han producido).
*   La **inicialización (`initialize`)** es como el **proceso de casting y preparación de un actor para un nuevo papel**. Aquí se le da su nombre de personaje, se le mide para el vestuario, etc., cuando "nace" en ese papel.
*   La **Herencia** es como si un "Guion de Héroe Volador" se basara en el "Guion de Héroe" original, heredando todas las habilidades básicas del héroe y solo añadiendo o modificando la capacidad de volar.
*   Los **Módulos** son como **kits de herramientas o manuales de estilo** que puedes añadir a tus guiones. Por ejemplo, un módulo "Efectos Especiales de Lucha" podría tener métodos para coreografiar escenas de combate. Puedes incluir este manual en varios guiones de "Héroe" o "Villano", y ambos sabrán cómo luchar de la misma manera, sin necesidad de que uno herede del otro.
*   Los **Mixins** son la **aplicación práctica de esos kits de herramientas**. Al "incluir" un manual de "Efectos Especiales de Lucha" en el guion de tu "Héroe", tu actor ahora tiene esos métodos de lucha.
*   La **visibilidad de métodos** (public, private, protected) es como las **reglas de acceso a la información en el estudio**.
    *   **Público** es lo que la audiencia ve en pantalla (la película final).
    *   **Privado** son los secretos del set, solo conocidos por el actor para su propia interpretación (el actor sabe cómo prepararse mentalmente, pero no lo comparte con la audiencia).
    *   **Protegido** es información compartida solo entre miembros del mismo equipo de producción (los actores pueden hablar entre sí sobre cómo interpretar una escena, pero no con la audiencia).
*   Las **buenas prácticas de reutilización de código** son como un director eficiente que no reinventa la rueda: usa el mismo escenario para varias escenas, reutiliza el vestuario si es posible, y adapta los guiones existentes en lugar de escribir uno nuevo desde cero para cada película.

