---
layout: post
title: "Curso de PHP"
categories: php
tags: draft
---

## [Clase 3](https://platzi.com/clases/2794-php-arreglos-funciones/46554-arreglos-asociativos/): Arreglos asociativos

```php
<?php

$cafes = array(
    "Capuccino" => 50,
    "Latte" => 49,
    "Americano" => 70
);

// echo "El precio del cafe Americano es de {$cafes['Americano']}";


$personas = array(

    "Carlos" => array(
        "edad" => 20,
        "apellido" => "Diaz"
    ),

    "Miguel" => array(
        "edad" => 18,
        "apellido" => "Rodriguez"
    ),

);

echo "La informacion de Miguel es: Edad: " . $personas["Miguel"]["edad"] . " Apellido: " . $personas["Miguel"]["apellido"];

echo "\n";
```

## [Clase 4](https://platzi.com/clases/2794-php-arreglos-funciones/46555-manipulando-arreglos/): Manipulando arreglos

[Funciones de Arrays - documentacion](https://www.php.net/manual/es/ref.array.php)

```php
<?php

$edades = [12,14,18,21,24,40];
$nombre = "Nombre";

 // count() : Saber el tamaño de un arreglo
 echo(count($edades));

 /**
  * array_push(): Agregas uno o mas elemntos al final de un array
  */
  array_push($edades,50);
  var_dump($edades);

/**
 * is_array(): La función is_array() verifica si una variable es una matriz o no.
 * Esta función devuelve verdaderosi la variable es una matriz,de lo contrario devuelve falso
 */
if(is_array($nombre)){
    echo "Si es un array";
}else{
    echo "No es un array";
}

/**
 * explode(): Convierte un string en un array
 * explode(separetor,string,limit);
 */
$frase = "Nunca pares de aprender";
var_dump(explode(" ",$frase));

/**
 * implode(): Convierte un array en un string
 * implode(separador,string);
 */
$palabras = ["Me","encanta","platzi","<3"];
var_dump(implode(" ",$palabras));
```

## Reto

```php
<?php

$escuela = array(

    array(
        "Nombre" => "Michijose",
        "Ocupacion" => "Developer increible",
        "Color" => "Naranja con rayitas",
        "Comidas" => array(
            "Favoritas" => "Lasaña, Atun",
            "NoFavoritas" => "Fresas, Cacahuates"
        )
    ),

    array(
        "Nombre" => "Michisancio",
        "Ocupacion" => "jQuery Developer",
        "Color" => "Blanco con manchitas negras",
        "Comidas" => array(
            "Favoritas" => "Pescado, Pollo",
            "NoFavoritas" => "Atun"
        )
    ),

    array(
        "Nombre" => "Mr. Michi",
        "Ocupacion" => "Pro en PHP",
        "Color" => "Blanco",
        "Comidas" => array(
            "Favoritas" => "Pizza",
            "NoFavoritas" => "Pescado"
        )
    ),

);


// $michisancio = $escuela[1];

// echo "Las comidas favoritas de Michisancio son " . $michisancio['Comidas']['Favoritas'];

$mr_michi = $escuela[2];
echo "El color de Mr. Michi es " . $mr_michi["Color"];

echo "\n";
```

## [Clase 6](https://platzi.com/clases/2794-php-arreglos-funciones/46557-aprende-a-tomar-decisiones-con-if-y-else/): If / Else

```php
<?php

$asientos_disponibles = 0;
$es_hijo_de_tom_holland = false;
$conoce_a_tony_stark = true;

if ($asientos_disponibles > 0)
    echo "Puedes ver la pelicula de Spidey";
else if ($es_hijo_de_tom_holland)
    echo "No te creo, pero puedes ver la pelicula";
else if ($conoce_a_tony_stark)
    echo "Bueno, te creo, adelante";
else
    echo "Lo sentimos, te tocara spoilearte";

echo "\n";
```

## [Clase 7](https://platzi.com/clases/2794-php-arreglos-funciones/46558-como-organizar-tu-codigo-con-switch/): Switch

## [Clase 8](https://platzi.com/clases/2794-php-arreglos-funciones/46559-reto-puedo-retirar-mis-donaciones-de-twitch/): Reto IF

```php
<?php

$saldo = readline("Ingrese su saldo: ");

if ($saldo <= 100){
echo "Saldo insuficiente";
}
else {
echo "Aca tiene sus $saldo";
}
echo "\n";
```

## [Clase 9](https://platzi.com/clases/2794-php-arreglos-funciones/46560-ciclo-while/): Ciclo while

```php
<?php

$contador = 1;

while($contador <= 10) {
    echo "Actualmente estamos en la iteración $contador \n";
    $contador++;
}

echo "\n";
```

## [Clase 10](https://platzi.com/clases/2794-php-arreglos-funciones/46561-do-while/): Do while

```php
<?php

$usernames = ["Pepito123", "Mr.Michi", "RetaxMain"];

do {

	$username = readline("Por favor, ingresa tu nuevo nombre de usuario: ");

	echo "\n";

} while( in_array($username, $usernames) );

echo "\n";
```
