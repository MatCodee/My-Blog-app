---
title: 'Funciones por referencia y por valor'
description: 'Se explica como pasar parametos por referencia y valor en C++'
pubDate: 'Jul 01 2022'
heroImage: '/category/cpp.jpg'
category: 'c++'
---

Cuando pasamos parametros en nuestras funciones en los lenguajes actuales algunas vez nos preguntamos cosas como:
Esto que guardo es una copia de mi variable? es el valor de la direccion?

Pues en C y C++ necesitamos estar preocupados por nuestras variables de manera que debemos ser concientes de operadores como **&** y **(*)**

Cosas por ejemplo:
```cpp
int add(int a,int b) {
    return a + b;
}

```
Mira este codigo crees que necesita un **& ?**


##### Paso por valor:
En simples palabras pasar un parametro por valor es pasar una copia de la variable
##### Paso por referencia:
Pasar una parametro por referencia es pasar la variable real es decir la misma que esta en la memoria

#### Explicacion:
Si nos fijamos en el ejemplo anterior, cuando pasamos **a** y **b**, lo que ocurre en el compilador es que copia el valor de esas variables y las envia a esa funcion, esto 
nos indica que gastamos memoria adicional para poder copiar esas variables y devolverlas como parametros.

Seria mejor que pudieramos pasar las variables directamente verdad?
bueno aqui te explico como ser mas eficiente con el codigo en C++

##### Pasar por parametros por valor:
```cpp
int add(int a,int b) {
    return a + b;
}
int main() {
    int num1 = 2;
    int num2 = 3;
    int sum = add(num1,num2);;
    std::cout << "suma: " << sum << std::endl;
}

```
##### Pasar por parametros por referencia:
```cpp
int add(int &a,int &b) {
    return a + b;
}
int main() {
    int num1 = 2;
    int num2 = 3;
    int sum = add(num1,num2);
    std::cout << "suma: " << sum << std::endl;
}

```
No hay cambios aparentemente pero en la memoria del programa no existe una copia adicional ni se crea una memoria extra.

##### Pero que ventajas y desventajas tiene pasar un parametro por referencia
Ya vimos que pasar el **&** ahorramos memoria y operaciones, pero que nos puede pasar si alguien por ejemplo modifica la variable dentro de la funcion que es pasada por referencia.
esto puede ser planeado si usted realmente lo quiere hacer porque quiere, pero si no es planeado puede generar problemas con su codigo a futuro
```cpp
int add(int &a,int &b) {
    a = 999;
    return a + b;
}
int main() {
    int num1 = 2;
    int num2 = 3;
    int sum = add(num1,num2);
    std::cout << "suma: " << sum << std::endl;
}

```
Lo que sucede en este codigo es que ademas de que se le sumara a **a** 999 + 3 = 1002
el valor de num1 de tener un valor de 2 cambiaria a 999.
Es decir, la funcion puede cambiar el valor de variables externas a ellas lo que se llama fuera de su ambito.

Como arreglamos esto, usando **const**
```cpp
int add(const int &a,const int &b) {
    a = 999;
    return a + b;
}
int main() {
    int num1 = 2;
    int num2 = 3;
    int sum = add(num1,num2);
    std::cout << "suma: " << sum << std::endl;
}

```
Ahora no podemos modificar el las variables dentro de la funcion y ademas ahorramos memoria, y dado eso el codigo anterior arrojara un error ya que intentamos modificar el valor de **a**


#### Conclusion 
Ahora qe vimos como pasar por valor y referencia, aprendimos como ahorrar memoria y numero de operaciones de tu codigo de C++, ademas vimos como podemos proteger nuestra variable que es 
enviada a una funcion que potencialmente podria ser modificada. Esto sin duda ayudara a mejorar tu codigo, me despido adios.