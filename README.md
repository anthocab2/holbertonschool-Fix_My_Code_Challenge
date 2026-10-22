# Holberton School — Fix My Code Challenge

Correcciones de cinco programas existentes en Python, JavaScript, Ruby y C.
El objetivo es localizar los defectos y repararlos conservando las funciones,
los algoritmos y las pruebas del código inicial.

Los ejercicios y sus instrucciones están en
[challenge/README.md](./challenge/README.md).

## Estructura

```text
holbertonschool-Fix_My_Code_Challenge/
├── README.md
└── challenge/
    ├── README.md
    ├── 0-fizzbuzz.py
    ├── 1-print_square.js
    ├── 2-sort.rb
    ├── 3-user.py
    └── 4-delete_dnodeint/
        ├── add_dnodeint_end.c
        ├── delete_dnodeint_at_index.c
        ├── free_dlistint.c
        ├── lists.h
        ├── main.c
        └── print_dlistint.c
```

## Requisitos y uso

El entorno objetivo del proyecto es Ubuntu 20.04 LTS, con Python 3, Node.js,
Ruby y GCC. Para preparar esas herramientas en Ubuntu:

```bash
sudo apt-get update
sudo apt-get install python3 nodejs ruby build-essential
git clone https://github.com/anthocab2/holbertonschool-Fix_My_Code_Challenge.git
cd holbertonschool-Fix_My_Code_Challenge/challenge
```

Los archivos Python y JavaScript tienen permiso ejecutable. Ruby se ejecuta
con `ruby 2-sort.rb`. Los comandos completos, incluido el de compilación C,
están en el [README del proyecto](./challenge/README.md).

## Validación

Se comprobaron las cinco tareas y la sintaxis de Python, JavaScript y Ruby.
El código C compiló con `-Wall -pedantic -Werror -Wextra -std=gnu89`; las
pruebas adicionales de la lista pasaron AddressSanitizer con detección de
fugas. Los binarios y las pruebas temporales se guardaron fuera del repositorio.

La verificación se realizó en Ubuntu 24.04.4 bajo WSL2 con Python 3.12.3,
Node.js 18.19.1, Ruby 3.2.3 y GCC 13.3.0. No se ejecutó Ubuntu 20.04 ni el
checker privado de Holberton.

## Procedencia

Código inicial de
[hs-hq/0x00-Fix_My_Code_Challenge](https://github.com/hs-hq/0x00-Fix_My_Code_Challenge),
revisión [84bffbd](https://github.com/hs-hq/0x00-Fix_My_Code_Challenge/tree/84bffbd71a31cbd94fcd1ef3b3d2f9a269b66a22).
Las correcciones mantienen las interfaces y el planteamiento de esa base.
