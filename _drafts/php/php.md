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
