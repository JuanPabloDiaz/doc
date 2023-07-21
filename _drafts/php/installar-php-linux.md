---
layout: post
title: "Instalación de PHP en Linux"
categories: php
tags: draft
---

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
