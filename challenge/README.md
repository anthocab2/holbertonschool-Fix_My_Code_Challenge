# Fix My Code — Challenge

Cinco ejercicios de depuración del código inicial de
[hs-hq/0x00-Fix_My_Code_Challenge](https://github.com/hs-hq/0x00-Fix_My_Code_Challenge/tree/84bffbd71a31cbd94fcd1ef3b3d2f9a269b66a22).
Se conservan las funciones, los mensajes de uso, los algoritmos y las pruebas
originales. Los cambios de formato se limitan a espacios finales y saltos de
línea que faltaban.

## Tareas y correcciones

| Tarea | Lenguaje | Defecto y corrección |
| --- | --- | --- |
| [0-fizzbuzz.py](./0-fizzbuzz.py) | Python | El caso divisible por 3 ocultaba `FizzBuzz`. Ahora se comprueba primero la divisibilidad por 3 y 5. |
| [1-print_square.js](./1-print_square.js) | JavaScript | El tamaño se interpretaba en hexadecimal. Ahora `parseInt` usa base 10 y la variable se declara con `const`. |
| [2-sort.rb](./2-sort.rb) | Ruby | La inserción usaba `i - 1`. Ahora usa `i`, conservando el filtro de enteros y el algoritmo de inserción. |
| [3-user.py](./3-user.py) | Python | El setter escribía un atributo distinto y los hashes usaban distinta capitalización. Ahora se escribe `__password` y ambas representaciones usan minúsculas. |
| [4-delete_dnodeint](./4-delete_dnodeint/) | C | Faltaban guardas y se reconectaban mal los nodos, con lecturas después de `free`. Ahora se valida el nodo, se actualizan ambos enlaces y después se libera. |

## Herramientas

- Ubuntu 20.04 LTS como entorno objetivo.
- Python 3, Node.js y Ruby.
- GCC y las cabeceras de C, disponibles en `build-essential`.

Todos los ejemplos siguientes parten de este directorio, `challenge/`.

## 0. FizzBuzz

```bash
./0-fizzbuzz.py 50
```

Imprime los números del 1 al argumento recibido, separados por espacios.
Sustituye los múltiplos de 3 por `Fizz`, los de 5 por `Buzz` y los de ambos
por `FizzBuzz`. En el ejemplo hay 50 elementos; las posiciones 15, 30 y 45
son `FizzBuzz`. Para números menores que 1 conserva la salida vacía.

## 1. Print square

```bash
./1-print_square.js 4
./1-print_square.js 10
```

El tamaño 4 produce cuatro filas de cuatro caracteres `#`; el tamaño 10,
diez filas de diez caracteres. El tamaño cero no imprime nada. Se conservan
los bucles y los mensajes originales cuando falta el argumento.

## 2. Sort

```bash
ruby 2-sort.rb 12 41 2 C 9 -9 31 fun -1 32
```

Salida:

```text
-9
-1
2
9
12
31
32
41
```

Se admiten negativos y duplicados. Los argumentos que no cumplen el filtro
original de enteros, como `C` y `fun`, se descartan.

## 3. User password

```bash
./3-user.py
```

Las pruebas originales deben imprimir únicamente:

```text
Test User
```

Cada usuario mantiene su UUID y su contraseña por separado. La propiedad
devuelve el hash; `is_valid_password` comprueba la contraseña recibida sin
modificarla. Asignar `None` o un valor que no sea string borra la contraseña.
La cadena vacía sigue siendo un string válido. MD5 se conserva como parte
del contrato del ejercicio.

## 4. Double linked list

Desde el subdirectorio C, compila el programa de prueba original fuera del
repositorio:

```bash
cd 4-delete_dnodeint
fix_code_test_dir=$(mktemp -d)
gcc -Wall -pedantic -Werror -Wextra -std=gnu89 \
  main.c free_dlistint.c print_dlistint.c add_dnodeint_end.c \
  delete_dnodeint_at_index.c -o "$fix_code_test_dir/delete_dnodeint"
"$fix_code_test_dir/delete_dnodeint"
```

La función elimina el nodo situado en un índice desde cero. Devuelve `1`
en caso de éxito y `-1` si el puntero, la lista o el índice no permiten la
operación. Una eliminación inválida conserva la lista. Al borrar la cabeza
se actualiza `*head`; al borrar el único nodo la lista queda vacía.

La primera lista del ejemplo es `0, 1, 2, 3, 4, 98, 402, 1024`. Tras borrar
el índice 5 queda `0, 1, 2, 3, 4, 402, 1024`. Las eliminaciones de la cabeza
la acortan hasta vaciarla, conservando los separadores del `main.c` original.

## Comprobaciones realizadas

| Componente | Resultado |
| --- | --- |
| Sintaxis | Python, `node --check` y `ruby -c` correctos. |
| FizzBuzz | Salida exacta de 50 elementos; cero, negativo y argumento ausente correctos. |
| Square | Tamaños 4, 10 y 0 correctos; mensaje y código de salida por argumento ausente conservados. |
| Sort | Ejemplo exacto; negativos, duplicados, argumentos no enteros y entrada vacía correctos. |
| User | Pruebas originales correctas; contraseña válida e inválida, borrado, string vacío, hash y usuarios independientes comprobados. |
| Lista C | Compilación con todos los flags y secuencia original correctas. |
| Casos límite C | Puntero nulo, lista vacía, un nodo, eliminación al principio/medio/final e índices iguales o mayores que la longitud correctos; enlaces comprobados en ambos sentidos. |
| Memoria C | AddressSanitizer con detección de fugas no informó errores en los casos adicionales. |

Entorno utilizado: Ubuntu 24.04.4 bajo WSL2, Python 3.12.3, Node.js 18.19.1,
Ruby 3.2.3 y GCC 13.3.0. Ruby se ejecutó desde paquetes extraídos en un
directorio auxiliar, con `--disable-gems`; estos ejercicios no necesitan gems.
Ubuntu 20.04 y el checker privado de Holberton no se ejecutaron.

Los fuentes y ambos README usan LF y terminan con un salto de línea. Los
Python y JavaScript tienen modo Git `100755`; los demás archivos, `100644`.
Los binarios, las cachés y las pruebas temporales quedan fuera de la entrega.
