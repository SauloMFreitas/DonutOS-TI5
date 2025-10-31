# DonutOS

DonutOS é um sistema operacional que começou como um projeto de diversão com o objetivo apenas de rodar o codigo [donut.c](https://www.a1k0n.net/2021/01/13/optimizing-donut.html) mas evoluiu pra um projeto maior. O objetivo é ser um sistema operacional portátil que sirva como um sniffer de rede, onde seria necessário apenas plugar o sistema em um dispositivo através de um pendrive e já seria possível monitorar a rede como um wireshark.

## Alunos integrantes da equipe

* Bernardo Marques Fernandes
* Bruno Santiago de Oliveira
* Fabio Freire Kochem
* Marcos Antônio Lommez Candido Ribeiro
* Saulo de Moura Zandona Freitas

## Professores responsáveis

* Felipe Domingos da Cunha
* Matheus Alcântara Souza
* Pedro Henrique Ramos Costa
* Ricardo Carlini Sperandio

## Instruções de utilização

### Dependencies
Foi usado um [tutorial](https://youtube.com/playlist?list=PLm3B56ql_akNcvH8vvJRYOc7TbYhRs19M&si=2bToaSQWffHsuESF) que mostra como montar um bootloader para começar a fazer um sistema operacional de fato. Nesse tutorial, foi disponibilizado um [shell script](https://github.com/mell-o-tron/MellOs/blob/main/A_Setup/setup-gcc-debian.sh) com a instalação de todas as dependências. A dependência mais trabalhosa de instalar é o cross compiler, então é recomendado rodar o script pra isso, as outras dependências são mais fáceis de instalar.

Ainda sobre o cross compiler, ainda é possível usar o gcc pra compilar porém não é recomendado. Enquanto é possível colocar flags indicanto a máquina target que o gcc deve compilar, algumas coisas podem não funcionar, por exemplo, ao forçar um erro de divisão por 0, o cross compiler roda o código normalmente enquanto o gcc causa algum problema nos interrupts e o erro não é detectado. Use o cross compiler se possível e o gcc como um plano B. O makefile ja está tratando a escolha de compiladores.

Finalmente, para o network sniffer, nota-se um arquivo `tap0.sh` na pasta raíz, que é uma placa de rede virtual que vai recebr pacotes e enviá-los à máquina virtual do QEMU. Esse arquivo precisa ser rodado antes de rodar o SO.


**TL;DR**

você vai precisar de:
- nasm
- qemu
- gcc cross compiler

### Como usar
#### Linux:
Como o OS precisa receber pacotes é necessário usar `sudo` quando for rodar.

Abra na pasta raíz do projeto e
- `make all` para compilar
- `make run` para compilar e rodar
- `make clean` para deletar binários

#### Windows:
Boa sorte!
