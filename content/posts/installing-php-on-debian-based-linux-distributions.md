+++
date = "2020-01-06"
title = "Instalando o PHP em distribuições Linux baseadas em Debian"
description = "Coisas simples e chatas que precisam ser feitas de vez em quando..."
tags = ["personal", "me-to-me", "php"]
categories = ["configs", "php"]

#images = ["/images/N90.jpg"]
#math = true
#series = ["Theme", "Hugo"]
+++

As distros que eu uso atualmente são o Fedora e o Ubuntu, o Fedora me deixa muito feliz com a forma como ele gerencia suas dependências de forma organizada e inteligente. É uma distro muito boa pra se trabalhar com desenvolvimento, as configurações são simples, o sitema não é cheio de coisas mirabolantes que só servem pra atrapalhar e você tem autonomia pra bagunçar bastante o S.O e errar pra aprender. Aliás, no meu ponto de vista o Fedora tem umas das melhores [documentações](https://docs.fedoraproject.org/en-US/docs/) que um S.O pode ter nos dias de hoje. O [DNF](https://fedoraproject.org/wiki/DNF) sem sombra de dúvidas é muito melhor que o [Aptitude](https://help.ubuntu.com/lts/serverguide/aptitude.html). Porém, por questões de usabilidade e ferramentas específicas eu preciso usar o Ubuntu. Eu estou muito esperançoso em me "livrar" do Ubuntu graças ao Arch Linux, meus testes têm sido promissores e o Arch é uma distro muito boa mesmo.

Mesmo hoje em dia existindo Docker pra tudo, eu gosto de ter uma instalação do PHP no meu S.O por questões de conveniência. Eu uso Docker somente dentro dos projetos em que eu trabalho e não para deixar meu ambiente de trabalho totalmente dockerizado, que é o que eu quero que seja no futuro.

Por isso que eu prefiro sempre instalar o PHP no meu S.O: só por conveniência. Na verdade, até se eu precisar criar uma imagem do PHP usando docker para algo específico, como já precisei, para instalar o driver do SQL Server por exemplo, talvez seja necessário, dentro desta imagem instalar o PHP, obviamente se não for uma imagem do PHP nativa.

### Fedora

**Abrindo um parênteses para o Fedora.**

O Fedora sempre trás a última versão do PHP disponível nos repositórios oficiais. Por isso para instalar o PHP na última versão, basta executar:

`sudo dnf install php`

Para instalar as extensões, basta fazer:

`sudo dnf install php-extension-name`

Se existir mais de uma versão do PHP instalado no Fedora, o comando acima pode trazer problemas pois ele não especifica a versão do PHP para qual a extensão deve ser instalada, assim o fedora vai instalar o pacote para a versão do PHP que estiver ativa no S.O. Para especificar a versão do PHP para a qual o pacote deve ser instalado, basta executar da seguinte maneira:

`sudo dnf install php7.3-extension-name`

ex: `sudo dnf install php7.3-fpm`

### Ubuntu

Para instalar o PHP na versão 7.3 no Ubuntu 18.04, o processo é um pouco mais burocrático, mas não tão complicado. Primeiro é sempre importante atualizar os repositórios e também os pacotes que porventura possam estar desatualizados:

`sudo apt-get update && sudo apt-get upgrade`

Depois disso é necessario adicionar o repositório do PHP 7.3 que contém as dependências e extensões também. Este repositório é o [ondrej/php](https://launchpad.net/~ondrej/+archive/ubuntu/php) PPA.

```
sudo add-apt-repository ppa:ondrej/php
sudo apt update
```

Uma vez que o repositório foi adicionado, agora sim, é possível instalar o PHP 7.3:

`sudo apt-get install php7.3`

É possível verificar a versão instalada com o seguinte comando: `php -v`

#### Instalando extensões

A forma de instalar extensões para o PHP no Ubuntu é semelhante ao Fedora.

Eu sempre que preciso, instalo as seguintes extensões:

`sudo apt-get install php7.3-cli php7.3-fpm php7.3-json php7.3-pdo php7.3-mysql php7.3-zip php7.3-gd  php7.3-mbstring php7.3-curl php7.3-xml php7.3-bcmath php7.3-json php7.3-sqlite3 php7.3-pgsql php-xdebug`

Massa demais! Agora é só codar com alegria. :)
