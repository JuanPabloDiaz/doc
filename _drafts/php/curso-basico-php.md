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
