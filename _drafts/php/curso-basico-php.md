---
layout: post
title: "Curso Basico PHP"
categories: php
tags: draft
---

## [Clase 7](https://platzi.com/clases/2646-php/44435-hackea-tu-miedo-a-la-terminal/): Comandos básicos en la terminal 💻

- `mkdir`: Crea una carpeta (directorio).
- `touch`: Crea un archivo. Es importante colocarle la extensión al archivo.
- `cat`: Nos sirve para ver el contenido de un archivo.
- `rm`: Con este comando podemos eliminar un archivo.
- `rm -r`: Útil para eliminar una carpeta (directorio).
- `nano`: Editar archivos
  - Es básico saber las siguientes combinaciones de teclas para guardar y salir de nano:
    - Guardar cambios: `Ctrl + O`. Luego presionamos la tecla Enter para confirmar las modificaciones.
    - Salir del editor: `Ctrl + X`.
- `Ctrl + L`: Limpiar la consola más rápido.

### Como Usar PHP en la terminal?

1. Instalar alguna version de Linux on Windows con WSL
   - abrir Microsoft Store y buscar "Windows subsystem". o buscar "ubuntu"
2. installar PHP:
   - $ `sudo apt update`
   - $ `sudo apt install php`
   - $ `php -version`
3. Inizializar PHP (**habilitando el modo interactivo de PHP**):
   - `php -a`
4. Escribir en PHP:
   ```php
   echo "Estoy aprendiendo PHP";
   echo 4+4;
   ```

## [Clase 8](https://platzi.com/clases/2646-php/44436-como-ejecutar-tus-programas-escritos-con-php/): Cómo ejecutar tus archivos PHP en Linux

1. Debo dirigirme a: **`cd /var/www/html`**
2. Borrar `rm index.html`
3. Crear archivo PHP" `touch index.php`
   > Si no puedo crear el archivo. `access denied error`, Run: `sudo chmod 777 html`.
4. Abrir VS code en esa carpeta: `code .`
5. Correr Apache: `sudo systemctl start apache2`
   > si estoy en Windows usando WSL, correr este codigo en lugar: `sudo /etc/init.d/apache2 start` (debo tener Wamp apagado)

## [Clase 9](https://platzi.com/clases/2646-php/44437-sintaxis-basica-de-php/): Sintaxis básica de PHP

```php
<?php
$firstName = "Juan";
$lastName = "Diaz";

echo $firstName . " " . $lastName . "\n";
or
echo "Yo soy $firstName $lastName \n";
```

## [Clase 10](https://platzi.com/clases/2646-php/44438-debugging-y-comentarios/): Debugging

### var_dump

Nos permite inspeccionar la variable y nos da información acerca de ella. Por ejemplo, en un array nos dice el número de elementos del array y el tipo que es cada elemento.

```php
<?php

$personas = [
"Carlos" => 22,
"Mr. Michi" => 15,
"Juan" => 65
];

//
var_dump( $personas );
```

Salida:

```php
array(3) {
["Carlos"]=>
int(22)
["Mr. Michi"]=>
int(15)
["Juan"]=>
int(65)
}
```

### print_r

Nos imprime la variable de una forma más limpia y con menos informacion.

```php
<?php

$personas = [
"Carlos" => 22,
"Mr. Michi" => 15,
"Juan" => 65
];

//
print_r( $personas );
```

Salida:

```php
Array
(
[Carlos] => 22
[Mr. Michi] => 15
[Juan] => 65
)
```

## [Clase 11](https://platzi.com/clases/2646-php/44439-variables-y-constantes/): Variables y constantes

### Varible

empieza simpre con un signo de $ y podemos cambiar su valor:

```php
$numero_1 = 8;
$numero_2 = 7;

echo $numero_1 + $numero2;
```

### Constante

**no se puede cambiar su valor**, como buena practica se crea en mayuscula y se define de la siguiente forma:

```php
define("NUMERO_PI", 3.14);

echo NUMERO_PI;
```

## [Clase 12](https://platzi.com/clases/2646-php/44440-tipos-de-datos/): Tipos de datos

Conversión de tipos automática

```php
<?php
$numerito = "23"; // String
$numerito = $numerito + 2 ; // Le sumamos al String un número

var_dump($numerito); // var_dump() nos inmprimirá información

echo "\n"; // Salto de línea
```

## [Clase 15](https://platzi.com/clases/2646-php/44443-operadores-logicos-que-son-las-tablas-de-verdad/): Operadores Lógicos

Son los operadores que nos ayudan a combinar dos o mas afirmaciones para definir si una oración es cierta o falsa. Su uso esta basado en tablas de verdad.

AND (y)
Se usa para verificar si dos afirmaciones son ciertas, entonces la oración completa es cierta. Si una de ellas es falsa, entonces, la oración completa es falsa.

true AND true = True

false AND true = False

true AND false = False

false AND false = False

Se escribe así:

$valor_1 and $valor_2
$valor_1 && $valor_2
OR (o)
Si una de las 2 afirmaciones es cierta, entonces la oración completa es cierta. Si solo una de ellas es falsa, entonces, la oración completa es cierta.

true OR true = True

false OR true = True

true OR false = True

false OR false = False

Se escribe así:

$valor_1 or $valor_2
$valor_1 || $valor_2
NOT (no)

Se usa para invertir el significado de una oración

NOT True ⇒ False

NOT False ⇒ True

### Ejercicio

```php
<?php
$es_michi_grande = true;
$le_gusta_comer = true;
$sabe_volar = false;
$tiene_2_patas = false;

//AND
var_dump($es_michi_grande && $le_gusta_comer);
bool(true)

//OR
var_dump($es_michi_grande || $sabe_volar);
bool(true)

//OR
var_dump($sabe_volar || $tiene_2_patas);
bool(false)

//NOT
var_dump(!$le_gusta_comer);
bool(false)

//NOT+AND
var_dump(!$le_gusta_comer && $es_michi_grande);
bool(false)

echo ("\n");

```

## [Clase 17](https://platzi.com/clases/2646-php/44445-operadores-aritmeticos/): Operadores Aritméticos

<table>
<thead>
<tr>
<th>Tipo</th>
<th>Descripción</th>
<th>Operador</th>
<th>Ejemplo</th>
</tr>
</thead>
<tbody>
<tr>
<td>Adición</td>
<td>Suma dos o más números.</td>
<td>+</td>
<td><code>$a + $b + $c</code></td>
</tr>
<tr>
<td>Sustracción</td>
<td>Resta dos o más números.</td>
<td>-</td>
<td><code>$a - $b - $c</code></td>
</tr>
<tr>
<td>Multiplicación</td>
<td>Multiplica dos o más números.</td>
<td>*</td>
<td><code>$a * $b * $c</code></td>
</tr>
<tr>
<td>División</td>
<td>Divide dos o más números.</td>
<td>/</td>
<td><code>$a / $b / $c</code></td>
</tr>
<tr>
<td>Módulo</td>
<td>Devuelve el residuo de una división.</td>
<td>%</td>
<td><code>$a % $b</code></td>
</tr>
<tr>
<td>Potenciación</td>
<td>Eleva un número al exponente dado.</td>
<td>**</td>
<td><code>$a ** $b</code></td>
</tr>
<tr>
<td>Identidad</td>
<td>Convierte un string a int o float, según sea el caso.</td>
<td>+</td>
<td><code>+$a</code></td>
</tr>
<tr>
<td>Negación</td>
<td>Convierte un número a positivo o negativo.</td>
<td>-</td>
<td><code>-$a</code></td>
</tr>
</tbody>
</table>

- Adición ⇒ `+`
- Sustracción ⇒ `-`
- Multiplicación ⇒ `*`
- División ⇒ `/`
- Modulo ⇒ `%` ⇒ Se usa para conocer el residuo de una división ⇒ `$a % $b`
- Potenciación ⇒ `**` ⇒ `$a ** $b`
- Identidad ⇒ Sirve para convertir un string a un **int** o **float**, según sea el caso ⇒ `+` ⇒ `+$a`
- Negación ⇒ Convierte un numero positivo a negativo ⇒ `-$a`

## [Clase 18](https://platzi.com/clases/2646-php/44446-operadores-relacionales/): Operadores relacionales

<table>
<thead>
<tr>
<th>Nombre</th>
<th>Descripción</th>
<th>Operador</th>
<th>Ejemplo</th>
<th>Resultado</th>
</tr>
</thead>
<tbody>
<tr>
<td>Igual</td>
<td>Compara si 2 variables son iguales en cuanto a sus valores más NO respecto a sus tipos de datos.</td>
<td>==</td>
<td><code>$a == $b</code></td>
<td><code>true</code> si <code>$a</code> es igual a <code>$b</code></td>
</tr>
<tr>
<td>Idéntico</td>
<td>Compara si 2 variables son iguales respecto a sus valores y tipos de datos.</td>
<td>===</td>
<td><code>$a === $b</code></td>
<td><code>true</code> si <code>$a</code> es igual a <code>$b</code>, y son del mismo tipo.</td>
</tr>
<tr>
<td>Diferente #1</td>
<td>Compara si 2 variables NO son iguales en cuanto a sus valores más NO respecto a sus tipos de datos.</td>
<td>!=</td>
<td><code>$a != $b</code></td>
<td><code>true</code> si <code>$a</code> no es igual a <code>$b</code></td>
</tr>
<tr>
<td>Diferente #2</td>
<td>Compara si 2 variables NO son iguales en cuanto a sus valores más NO respecto a sus tipos de datos.</td>
<td>&lt;&gt;</td>
<td><code>$a &lt;&gt; $b</code></td>
<td><code>true</code> si <code>$a</code> no es igual a <code>$b</code></td>
</tr>
<tr>
<td>No idéntico</td>
<td>Compara si 2 variables NO son iguales en cuanto a sus valores o tipos de datos.</td>
<td>!==</td>
<td><code>$a !== $b</code></td>
<td><code>true</code> si <code>$a</code> no es igual a <code>$b</code>, o si no son del mismo tipo.</td>
</tr>
<tr>
<td>Menor que</td>
<td>Evalúa si un número es menor que otro.</td>
<td>&lt;</td>
<td><code>$a &lt; $b</code></td>
<td><code>true</code> si <code>$a</code> es estrictamente menor que <code>$b</code>.</td>
</tr>
<tr>
<td>Mayor que</td>
<td>Evalúa si un número es mayor que otro.</td>
<td>&gt;</td>
<td><code>$a &gt; $b</code></td>
<td><code>true</code> si <code>$a</code> es estrictamente mayor que <code>$b</code>.</td>
</tr>
<tr>
<td>Menor o igual que</td>
<td>Evalúa si un número es menor o igual que otro.</td>
<td>&lt;=</td>
<td><code>$a &lt;= $b</code></td>
<td><code>true</code> si <code>$a</code> es menor o igual que <code>$b</code>.</td>
</tr>
<tr>
<td>Mayor o igual que</td>
<td>Evalúa si un número es mayor o igual que otro.</td>
<td>&gt;=</td>
<td><code>$a &gt;= $b</code></td>
<td><code>true</code> si <code>$a</code> es mayor o igual que <code>$b</code>.</td>
</tr>
</tbody>
</table>

### Operadores en PHP

<table>
<thead>
<tr>
<th>Operador</th>
<th>Descripción</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>=</code></td>
<td><em>Asignación</em></td>
</tr>
<tr>
<td><code>+=</code></td>
<td><em>Incremento</em></td>
</tr>
<tr>
<td><code>++</code></td>
<td><em>Incremento</em></td>
</tr>
<tr>
<td><code>-=</code></td>
<td><em>Decremento</em></td>
</tr>
<tr>
<td><code>--</code></td>
<td><em>Decremento</em></td>
</tr>
<tr>
<td><code>*=</code></td>
<td><em>Multiplicación</em></td>
</tr>
<tr>
<td><code>/=</code></td>
<td><em>División</em></td>
</tr>
<tr>
<td><code>.=</code></td>
<td><em>Concatenación</em></td>
</tr>
</tbody>
</table>

## Precedencia de operadores

La precedencia de un operador indica qué tan "estrechamente" se unen dos expresiones juntas. Por ejemplo, en la expresión 1 + 5 _ 3 , la respuesta es 16 y no 18 porque el operador de multiplicación ("_") tiene una precedencia mayor que el operador de adición ("+"). Los paréntesis pueden ser usados para forzar la precedencia, si es necesario. Por ejemplo: (1 + 5) \* 3 se evalúa como 18.

Cuando los operadores tienen igual precedencia su asociatividad decide cómo se agrupan. Por ejemplo "-" tiene asociatividad a izquierda, así 1 - 2 - 3 se agrupa como (1 - 2) - 3 y se evalúa a -4. "=", por otra parte, tiene asociatividad a derecha, así $a = $b = $c se agrupa como $a = ($b = $c).

Los operadores de igual precedencia que no son asociativos no pueden usarse unos junto a otros, por ejemplo, 1 < 2 > 1 es ilegal en PHP. La expresión 1 <= 1 == 1, por otro lado, es legal, ya que el operador == tiene menos precedencia que el operador <=.

El uso de paréntesis, incluso cuando no es estrictamente necesario, a menudo puede aumentar la legibilidad del código haciendo grupos explícitamente en lugar de confiar en la precedencia y asociatividad implícitas del operador.

La siguiente tabla enumera los operadores en orden de precedencia, con los de más alta precedencia al inicio. Los operadores en la misma línea tienen igual precedencia, en cuyo caso la asociatividad decide el agrupamiento.

[Mas informacion](https://www.php.net/manual/es/language.operators.precedence.php)

<table>
   <caption><strong>Precedencia de operadores</strong></caption>
     <thead>
      <tr>
       <th>Asociatividad</th>
       <th>Operadores</th>
       <th>Información adicional</th>
      </tr>
     </thead>
     <tbody>
      <tr>
       <td>no asociativo</td>
       <td>
        <code class="literal">clone</code>
        <code class="literal">new</code>
       </td>
       <td><a href="language.oop5.cloning.php" class="link">clone</a> and <a href="language.oop5.basic.php#language.oop5.basic.new" class="link">new</a></td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td><code class="literal">[</code></td>
       <td><span class="function"><a href="function.array.php" class="function">array()</a></span></td>
      </tr>
      <tr>
       <td>derecha</td>
       <td><code class="literal">**</code></td>
       <td><a href="language.operators.arithmetic.php" class="link">aritmética</a></td>
      </tr>
      <tr>
       <td>derecha</td>
       <td>
        <code class="literal">++</code>
        <code class="literal">--</code>
        <code class="literal">~</code>
        <code class="literal">(int)</code>
        <code class="literal">(float)</code>
        <code class="literal">(string)</code>
        <code class="literal">(array)</code>
        <code class="literal">(object)</code>
        <code class="literal">(bool)</code>
        <code class="literal">@</code>
       </td>
       <td>
        <a href="language.types.php" class="link">tipos</a> e <a href="language.operators.increment.php" class="link">incremento/decremento</a>
       </td>
      </tr>
      <tr>
       <td>no asociativo</td>
       <td><code class="literal">instanceof</code></td>
       <td>
        <a href="language.types.php" class="link">tipos</a>
       </td>
      </tr>
      <tr>
       <td>derecha</td>
       <td><code class="literal">!</code></td>
       <td>
        <a href="language.operators.logical.php" class="link">lógico</a>
       </td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td>
        <code class="literal">*</code>
        <code class="literal">/</code>
        <code class="literal">%</code>
       </td>
       <td>
        <a href="language.operators.arithmetic.php" class="link">aritmética</a>
       </td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td>
        <code class="literal">+</code>
        <code class="literal">-</code>
        <code class="literal">.</code>
       </td>
       <td>
        <a href="language.operators.arithmetic.php" class="link">aritmética</a> y
        <a href="language.operators.string.php" class="link">string</a></td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td>
        <code class="literal">&lt;&lt;</code>
        <code class="literal">&gt;&gt;</code>
       </td>
       <td>
        <a href="language.operators.bitwise.php" class="link">bit a bit</a>
       </td>
      </tr>
      <tr>
       <td>no asociativo</td>
       <td>
        <code class="literal">&lt;</code>
        <code class="literal">&lt;=</code>
        <code class="literal">&gt;</code>
        <code class="literal">&gt;=</code>
       </td>
       <td>
        <a href="language.operators.comparison.php" class="link">comparación</a>
       </td>
      </tr>
      <tr>
       <td>no asociativo</td>
       <td>
        <code class="literal">==</code>
        <code class="literal">!=</code>
        <code class="literal">===</code>
        <code class="literal">!==</code>
        <code class="literal">&lt;&gt;</code>
        <code class="literal">&lt;=&gt;</code>
       </td>
       <td>
        <a href="language.operators.comparison.php" class="link">comparación</a>
       </td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td><code class="literal">&amp;</code></td>
       <td>
        <a href="language.operators.bitwise.php" class="link">bit a bit</a> y
        <a href="language.references.php" class="link">referencias</a></td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td><code class="literal">^</code></td>
       <td>
        <a href="language.operators.bitwise.php" class="link">bit a bit</a>
       </td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td><code class="literal">|</code></td>
       <td>
        <a href="language.operators.bitwise.php" class="link">bit a bit</a>
       </td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td><code class="literal">&amp;&amp;</code></td>
       <td>
        <a href="language.operators.logical.php" class="link">lógico</a>
       </td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td><code class="literal">||</code></td>
       <td>
        <a href="language.operators.logical.php" class="link">lógico</a>
       </td>
      </tr>
      <tr>
       <td>derecha</td>
       <td><code class="literal">??</code></td>
       <td>
        <a href="language.operators.comparison.php" class="link">comparación</a>
       </td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td><code class="literal">? :</code></td>
       <td>
        <a href="language.operators.comparison.php#language.operators.comparison.ternary" class="link">ternario</a>
       </td>
      </tr>
      <tr>
       <td>derecha</td>
       <td>
        <code class="literal">=</code>
        <code class="literal">+=</code>
        <code class="literal">-=</code>
        <code class="literal">*=</code>
        <code class="literal">**=</code>
        <code class="literal">/=</code>
        <code class="literal">.=</code>
        <code class="literal">%=</code>
        <code class="literal">&amp;=</code>
        <code class="literal">|=</code>
        <code class="literal">^=</code>
        <code class="literal">&lt;&lt;=</code>
        <code class="literal">&gt;&gt;=</code>
       </td>
       <td>
        <a href="language.operators.assignment.php" class="link">asignación</a>
       </td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td><code class="literal">and</code></td>
       <td>
        <a href="language.operators.logical.php" class="link">lógico</a>
       </td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td><code class="literal">xor</code></td>
       <td>
        <a href="language.operators.logical.php" class="link">lógico</a>
       </td>
      </tr>
      <tr>
       <td>izquierda</td>
       <td><code class="literal">or</code></td>
       <td>
        <a href="language.operators.logical.php" class="link">lógico</a>
       </td>
      </tr>
     </tbody>
   </table>

## Programa del curso

Para ver el programa es necesario correr en la terminal `php fileName.php`

```php
<?php
$segundos = readline("Ingresa el tiempo en segundos: ");

$horas = (int) ($segundos / 3600);
$segundos = (int) ($segundos % 3600);
$minutos = (int) ($segundos / 60);
$segundos = (int) ($segundos % 60);

echo "Son $horas horas, $minutos minutos y $segundos segundos.";
echo "\n";
```

## Reto del curso

Lo logre!!

```php
<?php
$horas = readline("Ingresa el tiempo en horas: ");
$minutos = readline("Ingresa el tiempo en minutos: ");
$segundos = readline("Ingresa el tiempo en segundos: ");

$resultado = ($horas * 3600);      //horas a segundos
$resultado += ($minutos * 60);    //minutos a segundos
$resultado += $segundos;

echo "El valor en segundos es: $resultado";
echo "\n";
```
