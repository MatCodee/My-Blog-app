---
title: 'Pasar Parámetros por Referencia y por Valor en C++'
description: 'Aprende a manejar parámetros en funciones de C++ mediante paso por referencia y por valor'
pubDate: 'Jul 01 2022'
heroImage: '/category/cpp.jpg'
category: 'c++'
---


Cuando trabajamos con funciones en lenguajes de programación, a menudo nos preguntamos si estamos manipulando una copia de una variable o el valor real en la memoria. En C y C++, es crucial entender cómo funcionan los operadores `&` y `*` para gestionar correctamente nuestros parámetros.

Por ejemplo, consideremos el siguiente código:
```cpp
int add(int a,int b) {
    return a + b;
}

```
¿Crees que esta función necesita el operador &?



##### Paso por valor:
En términos simples, pasar un parámetro por valor implica enviar una copia de la variable.

##### Paso por referencia:
Pasar un parámetro por referencia significa pasar la variable real, es decir, la que está en la memoria.


#### Explicacion:
Si observamos el ejemplo anterior, cuando pasamos a y b, el compilador copia el valor de esas variables y las envía a la función. Esto significa que estamos utilizando memoria adicional para copiar esas variables y pasarlas como parámetros.

¿No sería mejor pasar las variables directamente? Bueno, aquí te explicamos cómo hacerlo de manera más eficiente en C++.

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
En apariencia, no hay cambios, pero en la memoria del programa no se crea una copia adicional ni se utiliza memoria adicional.

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