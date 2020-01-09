+++
date = "2020-01-09"
title = "Verificando se determinada porta está em uso no seu sistema operacional"
description = "Coisas simples e chatas que precisam ser feitas de vez em quando..."
tags = ["personal", "me-to-me", "linux"]
categories = ["configs", "linux"]

#images = ["/images/N90.jpg"]
#math = true
#series = ["Theme", "Hugo"]
+++

*Considerações iniciais: as informações contidas neste texto, só funcionam para sistemas baseados no Unix.*

Já passou por aquela situação de ter vários containers docker *startados* em portas diferentes, aí você tenta subir um novo containar e o terminal joga na sua cara que a porta já está em uso? Ou mesmo os *built-in web servers* do PHP, Node ou Python, já estão usando portas que vocês gostaria de usar?

Eu também já passei por isso, há uma forma de saber se a porta já está sendo usada e/ou algumas informações sobre ela. No Linux, basta utilizar o seguinte comando:

`lsof -i TCP:PORT`

ex: `lsof -i TCP:1313`

Se porta estiver sendo utilizada o comando irá retornar algumas informações sobre ela. O comando irá retornar uma saída semelhante a esta:

```
COMMAND   PID     USER FD TYPE DEVICE SIZE/OFF NODE NAME
hugo    28013 atmosmps 9u IPv4 141117      0t0  TCP localhost:xtel (LISTEN)
```

Com isto você pode identificar quem está usando a porta finalizar o processo, ou você pode simplesmente matar o processo da seguinte maneira: `kill -9 PID`.

**O que significa lsof?**

`lsof` siginifica *List Of Open File*. Arquivos são muito importantes no Unix, toda vez que estiver trabalhando no Linux/Unix poderá haver vários arquivos e pastas que estarão sendo utilizadas. Este comando fornece uma lista de arquivos que estão abertos. Basicamente, fornece as informações para descobrir os arquivos que estão abertos e por qual processo. De uma só vez, lista todos os arquivos abertos no console de saída.

Aqui você encontra mais informações sobre o [lsof e formas de utilizá-lo](https://www.geeksforgeeks.org/lsof-command-in-linux-with-examples/).

É isso.
