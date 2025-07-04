# 1. Ejercicios Básicos de Ruby

1. "¡Hola, mundo!"
  * Descripción: Escribe un script de Ruby que imprima "¡Hola, mundo!" en la consola.
  * Pista: Utiliza el método puts.
2. Declaración y Uso de Variables
  * Descripción: Declara variables para almacenar tu nombre (cadena), tu edad (entero) y tu altura en metros (flotante). Luego, imprime estas variables en la consola, incluyendo un mensaje descriptivo para cada una.
  * Pista: Ruby es un lenguaje de tipado dinámico, lo que significa que el tipo de una variable se infiere automáticamente cuando le asignas un valor. No necesitas usar el símbolo $ para las variables locales, a diferencia de PHP.
  * Concepto clave: La interpolación de cadenas (#{variable}) se utiliza dentro de cadenas con comillas dobles para incrustar el valor de una expresión Ruby.
3. Entrada de Usuario: Tu Nombre
  * Descripción: Pide al usuario que introduzca su nombre y luego salúdalo usando el nombre que ingresó.
  * Pista: Usa gets para obtener la entrada y chomp para eliminar el carácter de nueva línea al final.
4. Entrada de Usuario: Suma de Números
  * Descripción: Pide al usuario dos números enteros, súmalos y muestra el resultado.
  * Pista: Después de usar gets.chomp, convierte la cadena a entero usando .to_i.
5. Condicional if-else
  * Descripción: Pide al usuario un número y determina si es par o impar.
  * Pista: El operador % (módulo) te dará el resto de una división. Si el resto de dividir por 2 es 0, es par. Las sentencias if-else en Ruby terminan con end.
6. Condicional unless
  * Descripción: Pide al usuario que introduzca si tiene alergia al chocolate (sí/no). Muestra un mensaje que diga "Esta persona no es alérgica al chocolate" a menos que la respuesta sea "sí".
  * Pista: unless ejecuta el bloque de código si la condición es falsa.
7. Bucle while
  * Descripción: Imprime los números del 1 al 5 usando un bucle while.
  * Pista: Asegúrate de incrementar la variable del contador dentro del bucle para evitar un bucle infinito.
8. Bucle until
  * Descripción: Imprime los números del 5 al 1 (descendente) usando un bucle until.
  * Pista: until continúa ejecutándose mientras la condición sea falsa, y se detiene cuando la condición se vuelve verdadera.
9. Iteración con each en un Array
  * Descripción: Crea un array de tus tres frutas favoritas. Luego, itera sobre el array e imprime cada fruta.
  * Pista: El método each es la forma más idiomática de iterar sobre colecciones en Ruby.
10. Manipulación de Cadenas: Mayúsculas y Minúsculas
  * Descripción: Pide al usuario una palabra y luego imprímela en mayúsculas y en minúsculas.
  * Pista: Usa los métodos upcase y downcase.
11. Manipulación de Cadenas: Capitalizar
  * Descripción: Pide al usuario su nombre y apellido por separado. Imprime su nombre completo con la primera letra de cada palabra en mayúscula.
  * Pista: El método capitalize pone la primera letra en mayúscula y el resto en minúsculas.
12. Longitud de una Cadena
  * Descripción: Pide al usuario una frase y luego imprime cuántos caracteres tiene esa frase.
  * Pista: Usa el método length o size.
13. Acceso a Elementos de un Array
  * Descripción: Crea un array con algunos números. Imprime el primer elemento, el último elemento y el elemento en un índice específico (por ejemplo, el tercer elemento).
  * Pista: Los arrays se indexan desde 0. Puedes usar first, last y [indice].
14. Creación de Arrays con Rangos
  * Descripción: Crea un array que contenga los números del 1 al 10. Luego, crea otro array que contenga las letras de la 'a' a la 'e'. Imprime ambos arrays.
  * Pista: Usa la notación de rango (inicio..fin) para incluir el final o (inicio...fin) para excluirlo, y el método .to_a para convertir el rango en un array.
15. Creación y Acceso a Hashes
  * Descripción: Crea un hash para representar a una persona con las claves :nombre, :edad y :ciudad. Asigna valores a estas claves y luego imprime la edad de la persona.
  * Pista: Los hashes son similares a los arrays asociativos de PHP. Se pueden definir con llaves {} y pares clave-valor.
16. Definición y Llamada de Métodos Simples
  * Descripción: Define un método llamado saludar que acepte un nombre como argumento e imprima un saludo personalizado. Luego, llama a este método con tu propio nombre.
  * Pista: Los métodos se definen con def y terminan con end. Los paréntesis en la llamada al método son opcionales.
17. Métodos con Retorno Automático
  * Descripción: Define un método sumar_numeros que tome dos números, los sume y retorne automáticamente el resultado sin usar la palabra clave return. Luego, imprime el resultado de llamar a este método.
  * Pista: En Ruby, la última expresión evaluada en un método se devuelve automáticamente.
18. Introducción a Clases y Objetos (Parte 1)
  * Descripción: Define una clase Coche con un método initialize que acepte un modelo y un año. Este método debe establecer variables de instancia para el modelo y el año. Luego, crea un objeto de la clase Coche e imprime sus atributos.
  * Pista: Las clases se definen con class y terminan con end. El constructor es el método initialize. Las variables de instancia comienzan con @.
19. Introducción a Clases y Objetos (Parte 2): attr_accessor
  * Descripción: Modifica la clase Coche del ejercicio anterior para usar attr_accessor para los atributos modelo y año. Esto te permitirá acceder y modificar estos atributos directamente. Luego, crea un objeto, modifica su año y vuelve a imprimir la información.
  * Pista: attr_accessor crea automáticamente métodos de lectura (getters) y escritura (setters) para tus variables de instancia.
20. Usando IRB para Experimentar
  * Descripción: Abre la Interactive Ruby Shell (IRB) y experimenta con algunos de los comandos y conceptos que has aprendido. Por ejemplo, realiza operaciones matemáticas, define variables y prueba métodos de cadena.
  * Pista: Inicia IRB escribiendo irb en tu terminal. Puedes escribir cualquier comando de Ruby y verás el resultado de inmediato. Para salir, escribe exit o quit.
