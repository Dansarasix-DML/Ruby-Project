# 1. Introducción a Ruby y configuración del entorno
---

### 1.1. ¿Qué es Ruby? Historia, filosofía y comunidad actual
Ruby es un lenguaje de programación dinámico, de código abierto y de propósito general, que se centra en la simplicidad y la productividad.

### 1.2. Historia
Ruby fue creado por el informático japonés Yukihiro "Matz" Matsumoto a mediados de los años 90. La primera versión estable de Ruby se lanzó en 1995. 
El diseño de Ruby está influenciado por lenguajes como Perl, Smalltalk, Eiffel, Ada, Basic y Lisp.

### 1.3. Filosofía
* Programación con Alegría: Ruby fue diseñado con la idea de ser un lenguaje fácil de leer, flexible y orientado a objetos. A menudo se le denomina el "mejor amigo del programador" debido a su facilidad de aprendizaje, lectura, comprensión y escritura.
* Principio de "Menos Sorpresa" (Principle of Least Surprise): Un concepto fundamental en Ruby es que el lenguaje debe comportarse de una manera que minimice la confusión para los usuarios experimentados, garantizando que el lenguaje siga siendo consistente y predecible.
* Convención sobre Configuración (Convention over Configuration): La flexibilidad de Ruby se equilibra con un fuerte énfasis en la convención sobre configuración, lo que promueve que los desarrolladores sigan convenciones de programación estandarizadas a menos que tengan una razón imperiosa para desviarse. Esto fomenta una cultura de desarrollo innovadora y eficiente.
* Comunidad Actual: La comunidad Ruby es conocida por su naturaleza acogedora y su amplio sistema de soporte. Incluye foros en línea (como Ruby Forum, Stack Overflow, Reddit, GitHub), conferencias internacionales (RubyConf, RailsConf, RubyKaigi) y contribuciones activas a proyectos de código abierto (como Ruby on Rails, Jekyll y Discourse) [7-10]. La comunidad hace hincapié en la legibilidad, mantenibilidad y reducción de errores del código a través de convenciones de codificación y guías de estilo.

### 1.4. Instalación en Windows, macOS y Linux
Ruby es un lenguaje multiplataforma, lo que significa que un script de Ruby escrito en una plataforma compatible generalmente funcionará en otra sin problemas, 
siempre que no contenga código específico de la plataforma. Para ejecutar scripts de Ruby, se necesita un intérprete de Ruby.

#### 1.4.1. macOS
* La mayoría de los Macs ya vienen con Ruby preinstalado, pero suele ser una versión desactualizada.
* La forma más conveniente de instalar Ruby es mediante el gestor de paquetes brew.
* También se requieren las herramientas de línea de comandos de Xcode.
* Para gestionar múltiples versiones de Ruby, se recomienda instalar rbenv. Puedes instalar rbenv usando brew install rbenv. Después de la instalación, es necesario inicializar rbenv y añadirlo a tu perfil de shell.

#### 1.4.2. Windows
* La forma más sencilla de instalar Ruby es utilizando un instalador desde https://rubyinstaller.org/downloads/.
* Se recomienda descargar el instalador que incluye MSYS2-Devkit, ya que es necesario para compilar "gems" de Ruby con extensiones C, aunque no es imprescindible para principiantes.
* Durante la instalación, asegúrate de marcar la opción "Add Ruby executables to your PATH" para que Ruby sea accesible desde la línea de comandos.
* Después de la instalación, puedes verificar la versión de Ruby escribiendo ruby -v en el Símbolo del Sistema o PowerShell.
* También existe rbenv-for-windows, pero puede tener limitaciones con ciertas versiones de Ruby.

#### 1.4.3. Linux
* Algunas distribuciones de Linux pueden tener Ruby preinstalado. Puedes verificarlo ejecutando ruby -v en la terminal.
* Si no está instalado, se puede instalar usando el gestor de paquetes de tu distribución. Por ejemplo, en Ubuntu o Debian, usa sudo apt install ruby. En Red Hat, CentOS o Fedora, se usa sudo yum install ruby.
* Para la instalación de rbenv en Linux, se puede clonar el repositorio de rbenv y ruby-build en el directorio principal y luego inicializar rbenv en el perfil de shell.
* Uso del intérprete IRB y ejecución de scripts .rb

### 1.5. IRB (Interactive Ruby Shell)
* IRB es una aplicación REPL (read-eval-print-loop) que permite interactuar con el intérprete de Ruby en tiempo real.
* Es una herramienta invaluable para la experimentación, depuración y comprensión del código Ruby.
* Viene incluido con la distribución estándar de Ruby. Para iniciar una sesión IRB, simplemente escribe irb en tu shell.
* Una vez dentro de IRB, puedes escribir comandos de Ruby, que serán interpretados y ejecutados inmediatamente, mostrando el resultado.
* IRB soporta casi todos los aspectos de la sintaxis de Ruby, incluyendo la asignación de variables, la definición de métodos e incluso la inclusión de módulos.
* Para salir de la sesión IRB, puedes usar los comandos exit o quit.

### 1.6. Ejecución de scripts .rb:
* Un script de Ruby es un archivo de texto plano con la extensión .rb que contiene instrucciones que el intérprete de Ruby puede entender.
* Para ejecutar un script de Ruby, usa el comando ruby <nombre_del_script.rb> en tu terminal o línea de comandos. El intérprete de Ruby compila y ejecuta el archivo .rb en tiempo de ejecución, sin necesidad de compilación previa.
* En sistemas basados en Unix (Linux, macOS), puedes hacer que un script sea auto-ejecutable añadiendo una línea "shebang" (#!/usr/bin/env ruby o #!/usr/bin/ruby) al principio del archivo y dándole permisos de ejecución (chmod u+x <nombre_del_script.rb>).

#### 1.6.1. Primeros programas: “¡Hola, mundo!” y ejemplos básicos
Aquí hay algunos ejemplos de programas básicos en Ruby:
1. "¡Hola, mundo!"
  * El programa más simple para imprimir "Hello World" en Ruby se vería así:
  * Al ejecutar ruby hello.rb en la terminal, la salida será Hello World.
  * La función puts imprime su argumento y añade automáticamente un salto de línea.
  * Si no deseas un salto de línea, puedes usar print en su lugar.

2. Variables
  * En Ruby, las variables se declaran en el momento en que se les asigna un valor (por ejemplo, nombre = "Oscar").
  * Ruby es un lenguaje de tipado dinámico, lo que significa que el tipo de datos se infiere automáticamente en tiempo de ejecución.

3. Comentarios
* Los comentarios de una sola línea comienzan con el símbolo de almohadilla (#).
* Los comentarios de varias líneas se encierran entre =begin y =end.

4. Sentencias
* En Ruby, una sentencia generalmente termina con un carácter de nueva línea.
* Aunque puedes tener múltiples sentencias en una sola línea separadas por un punto y coma (;), no es la mejor práctica y se recomienda evitarlo para mejorar la legibilidad.

5. Métodos (Funciones)
* Los métodos se definen usando la palabra clave def y terminan con end.
* Se invocan simplemente llamando a su nombre.
* Los paréntesis alrededor de los argumentos del método son opcionales en muchos casos, especialmente si no hay argumentos o si mejora la legibilidad.

6. Interpolación de Cadenas
* Para incrustar expresiones de Ruby dentro de una cadena de texto, se utiliza la sintaxis #{expresión} dentro de cadenas entre comillas dobles.

7. Entrada de Usuario
* El método gets lee la entrada del usuario desde el teclado, devolviéndola como una cadena de texto que incluye un carácter de nueva línea.
* El método chomp se utiliza para eliminar el carácter de nueva línea final de la entrada de gets, lo cual es útil para comparaciones precisas de cadenas.
* Para convertir la entrada de cadena a un número entero, puedes usar .to_i.

8. Sentencias Condicionales
* if: Ejecuta un bloque de código si una condición es verdadera.
* if-else: Proporciona una alternativa para cuando la condición if es falsa.
* unless: Es lo opuesto a if; ejecuta un bloque de código si una condición es falsa.
* Operador ternario: Una forma concisa de escribir una sentencia if-else en una sola línea (condicion ? valor_si_verdadero : valor_si_falso).

9. Bucles:
* Ruby ofrece varias formas de repetir código, incluyendo while, until y for.
* Los bucles for son útiles para iterar sobre rangos o colecciones, pero each es más idiomático en Ruby.
* El comando loop do ... end con break permite crear un bucle infinito que se detiene con la palabra clave break.
* Ruby también proporciona las palabras clave break, next y redo para controlar el flujo de ejecución dentro de los bucles.
