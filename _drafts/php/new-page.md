---
layout: post
title: "My PHP Project"
categories: php
tags: draft
---

I will use jpdiaz.work or jpdiaz.design for this project

- I need to find out where to host this site.
- Not sure where to host php sites.

## COMO CONECTARSE a una BASE DE DATOS con PHP | CONEXION DE PHP Y MYSQL

[Video conect](https://www.youtube.com/watch?v=T8aiRfPtqiU&list=PLPY4vb-8wE-VeSAOjRlJzjCjpgQ_j8aVQ&index=2)

## COMO HACER un LOGIN en PHP y MYSQL | COMO HACER un REGISTRO en PHP y MYSQL

[Video Login](https://www.youtube.com/watch?v=KBskeBtQNOw&t=323s)

My project is located in `C:\wamp64\www\tutorioz`

- usar un Do...while en PHP para evitar que se repitan usernames a la hora de pedirle al usuario que se registre.

  ```php
  <?php

  $usernames = ["Pepito123", "Mr.Michi", "RetaxMain"];

  do {

  	$username = readline("Por favor, ingresa tu nuevo nombre de usuario: ");

  	echo "\n";

  } while( in_array($username, $usernames) );

  echo "\n";
  ```
