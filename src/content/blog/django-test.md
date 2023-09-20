---
title: 'Test en Django'
description: 'Como genera Test unitarios con django'
pubDate: 'Jul 01 2022'
heroImage: '/category/django.jpg'
category: 'django'
---


### Test unitarios en Django usando templates
Hoy veremos como crear **Test unitarios** con Django en plantillas, esto es muy importante y ahora o veo como algo indispensable para 
un programador que quiere construir codigo de calidad a nivel empresarial, viendo desde un punto de vista de empresa los clientes
quieren el mejor producto un producto sin fallas y por eso los test unitarios son necesarios.

Requisitos:
- Pytest
- Fake


Pytest es una libreria que nos permite configrar y separar nuestros Test en Django, esto se debe a que cuando los proyectos en el backend de django
son grandes y escalan mucho mantener ordenado la estructura de proyectos es indispensable para trabajar en equipo, errores de codigo, etc.


Fake es una libreria que nos permite insertar informacion falsa en nuestros proyectos de manera que se pueda testar el funcionamiento de nuestra
base de datos

#### Test simple de Url
Cuando queremos testear si nuestras rutas estas funcionando podemos crear estas simple pruebas de url
Ej: utilizaremos una vista llamada **Home** donde vamos a verificar si retorna de forma exitosa o no.
```python
from django.test import TestCase
from django.urls import reverse

class TestUrlViews(TestCase):
    def test_home(self):
        url_home = reverse('home')
        response = self.client.get(url_home)
        self.assertEqual(response.status_code, 200)
```
Pero **reverse** nos permite acceder al identificador de nuestra url asi que debemos verificar si esta implementado correctamente en nuestro urls.py
utilizando como ejemplo la vista de **HomeView**
```python
from django.urls import path
from .views import HomeView
urlpatterns = [
    path('',HomeView.as_view(),name='home'),
]
```
En este caso lo que queremos con nuestra pruebaunitaria es comprobar que el estado de nuestra ruta sea un 200 OK.

#### Test en nuestra Database
#### Test en Logins
#### Test de csrf extern o token