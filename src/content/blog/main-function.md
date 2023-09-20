---
title: 'Como definir correctamente una funcion main en C++'
description: 'Como definir una funcion principal como se debe hacer correctamente'
pubDate: 'Jul 01 2022'
heroImage: '/category/cpp.jpg'
category: 'c++'
---

todos alguna vez cuando programamos en C++ empezamos por la funcion principal, que es una funcion en la cual nosotros ejecutamos nuestro codigo pero alguna mas de alguna vez
te ha tocado ver codigos como


Con el parametro void.
```cpp

int main(void) {
    return 0;
}

```
Como procedimiento y parametro void
```cpp

void main(void) {
    return 0;
}

```
Solo procedimiento

```cpp

void main() {
    return 0;
}

```


```cpp

void main() {
}

```

Estos codigos son totalmente posibles en lenguaje C usando un compilador de C, pero no es una buena practica se espera que devuelva un valor en este caso 0, ahora los compiladores de C++ restringen
los procedimientos pero debemos retornar un valor 0 en este caso un codigo correcto en lenguaje C++ seria asi.
```cpp
#include <iostream>
using namespace std;

int main() {
    return 0;
}
```
En C seria asi
```cpp
int main(void) {
    return 0;
}
```