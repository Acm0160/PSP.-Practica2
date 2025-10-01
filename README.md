Práctica 2 – Entrada/Salida Estándar y Tuberías en Java
Descripción

El objetivo de esta práctica es adquirir experiencia en la creación y ejecución de aplicaciones que interactúan mediante la entrada y salida estándar en Java.
Se desarrollan tres programas que funcionan de manera independiente y que también pueden encadenarse utilizando el operador de tubería (|) del sistema operativo, lo que permite comprender cómo diferentes procesos pueden comunicarse entre sí.
Las competencias que se trabajan en esta práctica son:
Implementación de programas que lean y escriban datos desde la consola.
Generación y manipulación de información automática.
Documentación del código mediante comentarios y Javadoc.
Uso del operador de tubería para enlazar aplicaciones.
Elaboración de un manual de uso con pruebas y ejemplos.

Estructura del proyecto
Practica2/
 ├── pom.xml
 ├── entrada.txt
 ├── README.md
 └── src/
     └── main/
         └── java/
             └── org/
                 └── example/
                     ├── LectorTexto.java
                     ├── FiltraLineas.java
                     └── ContadorPalabras.java

Requisitos

Java 24 o superior
Maven 3.9 o superior
IDE recomendado: IntelliJ IDEA (también válido NetBeans o Eclipse)

Descripción de las aplicaciones
1. LectorTexto
Lee el archivo entrada.txt.
Muestra cada línea por salida estándar.
Si el archivo no existe, muestra un mensaje de error y termina.

2. FiltraLineas
Lee líneas desde la entrada estándar.
Muestra únicamente aquellas con más de 20 caracteres.

3. ContadorPalabras
Lee líneas desde la entrada estándar.
Cuenta y muestra el número total de palabras encontradas.
Se considera palabra cualquier secuencia separada por espacios.
Compilación
Desde la raíz del proyecto:
mvn clean compile

Las clases compiladas se generan en target/classes.
Ejecución
Ejecución independiente
LectorTexto

java -cp target/classes org.example.LectorTexto


FiltraLineas (requiere entrada estándar, por ejemplo, redirección de archivo)
java -cp target/classes org.example.FiltraLineas < entrada.txt


ContadorPalabras
java -cp target/classes org.example.ContadorPalabras < entrada.txt

Ejecución encadenada con tuberías
java -cp target/classes org.example.LectorTexto | java -cp target/classes org.example.FiltraLineas | java -cp target/classes org.example.ContadorPalabras


Flujo de datos:
entrada.txt → LectorTexto → FiltraLineas → ContadorPalabras
Ejemplo de uso

Si el archivo entrada.txt contiene:

Hola Mundo.
Esta frase deberia aparecer porque tiene muchos caracteres.
Esta frase tambien tiene muchos caracteres.
Esta no.


La ejecución encadenada produce:
Esta es una línea de prueba que tiene más de veinte caracteres.
Otra línea muy larga para filtrar correctamente.
Número total de palabras: 18

Generación de documentación
La documentación Javadoc se puede generar con:
mvn javadoc:javadoc

El resultado se guarda en:
target/site/apidocs/index.html
