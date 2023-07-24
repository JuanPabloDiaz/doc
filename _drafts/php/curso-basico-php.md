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
3. Inizializar PHP:
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
