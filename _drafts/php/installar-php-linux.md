---
layout: post
title: "Instalación de PHP en Linux"
categories: php
tags: draft
---

Recomiendo ver el video en [Platzi](https://platzi.com/clases/2646-php/44433-instalacion-de-php-en-linux/)

## Agregamos el repositorio

```bash
sudo add-apt-repository ppa:ondrej/php
```

## Actualizamos los repositorios:

```bash
sudo apt update
```

## Actualizamos los paquetes

```bash
sudo apt upgrade
```

## Instalación de php y apache

```bash
sudo apt install php8.0 apache2
```

## Podemos revisar que versiones de php tenemos instaladas con

```bash
sudo dpkg --get-selections | grep php
```

## Para saver que versión de php tenemos ejecutando podemos utilizar el comando

```bash
php --version
```

## How to Install PHP on Kali Linux?

```bash
sudo apt install php-all-dev
```
