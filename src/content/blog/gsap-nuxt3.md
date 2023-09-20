---
title: 'Cómo instalar GSAP en Nuxt 3'
description: 'Aprende cómo instalar GSAP de manera sencilla en Nuxt 3'
pubDate: 'Jul 01 2022'
heroImage: '/category/nuxt.jpg'
category: 'Nuxt'
---

En este artículo, aprenderás cómo instalar GSAP (GreenSock Animation Platform) de forma sencilla en tu proyecto Nuxt 3. GSAP es una biblioteca de animación popular que te permite crear animaciones suaves y atractivas en tus aplicaciones web.

### Paso 1: Instalar GSAP

El primer paso que debes seguir es instalar el paquete GSAP utilizando npm. Abre tu terminal y ejecuta el siguiente comando:
Nota: Puedes usar cualquier otro, como yarl o pnpm
```
npm i gsap@latest
```

### Paso 2: Configurar Nuxt

Después de haber instalado GSAP, necesitas configurar Nuxt para que funcione correctamente con GSAP. Abre tu archivo nuxt.config.ts y realiza la siguiente modificación:
```ts
export default defineNuxtConfig({
    // ... Otras configuraciones de Nuxt ...
    build: {
        transpile: ['gsap']
    }
    // ... Más configuraciones de Nuxt ...
})
```
Esta configuración permite que GSAP sea transpilado correctamente en tu proyecto Nuxt.

### Paso 3: Utilizar GSAP en tus vistas


Una vez que has instalado y configurado GSAP, puedes empezar a usarlo en tus vistas. Aquí tienes un ejemplo de cómo puedes animar elementos en tu vista utilizando GSAP:
```vue
<script setup>
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

gsap.registerPlugin(ScrollTrigger);

onMounted(() => {
  const tl = gsap.timeline({ defaults: { ease: 'power3.inOut' } });
  tl.from('#title', { delay: .5, duration: 0.8, y: '+=100', autoAlpha: 0 })
    .from('#subtitle', { delay: .6, duration: 1, y: '+=20', autoAlpha: 0 }, '-=1.25')
});
</script>
<template>
    <div>
        <h1 id="title" class="text-gray-900 dark:text-white font-bold text-5xl md:text-6xl xl:text-7xl">Su servicio <span
            class="text-primary dark:text-white"> en un solo lugar.</span></h1>
        <p id="subtitle" class="mt-8 w-2/3 text-2xl text-gray-700 dark:text-gray-300">
          Organice y mejora la productividad de su trabajo</p>
    </div>
</template>
```
En este ejemplo, hemos registrado el plugin ScrollTrigger de GSAP y creado una animación simple que se ejecutará cuando la vista se monte. Puedes personalizar esta animación según tus necesidades.

¡Listo! Ahora tienes GSAP instalado y configurado en tu proyecto Nuxt 3, y puedes comenzar a crear animaciones impresionantes en tus vistas.