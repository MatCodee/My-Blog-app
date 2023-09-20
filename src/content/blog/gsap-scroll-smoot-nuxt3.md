---
title: 'Implementación de Scroll Suave con GSAP en Nuxt 3'
description: 'Aprende a implementar el scroll suave en tu aplicación Nuxt utilizando GSAP'
pubDate: 'Jul 01 2022'
heroImage: '/category/nuxt.jpg'
category: 'Nuxt'
---


En este artículo, aprenderás cómo implementar el scroll suave en tu aplicación Nuxt 3 utilizando GSAP. El scroll suave es una técnica que mejora la experiencia del usuario al permitir transiciones suaves al desplazarse por una página web.

### Paso 1: Instalar GSAP

El primer paso consiste en instalar GSAP en tu proyecto Nuxt 3. Si aún no lo has hecho, abre tu terminal y ejecuta el siguiente comando:
```
npm i gsap@latest
```

### Paso 2: Configurar Nuxt

Para que GSAP funcione correctamente en tu proyecto Nuxt 3, debes realizar una configuración adicional en tu archivo nuxt.config.ts. Abre el archivo y asegúrate de incluir lo siguiente:

En tu archivo **nuxt.config.ts** implementa esto
```ts
export default defineNuxtConfig({
    // ... Otras configuraciones de Nuxt ...
    build: {
        transpile: ['gsap']
    }
    // ... Más configuraciones de Nuxt ...
})
```

### Paso 3: Implementar Scroll Suave
Ahora que has instalado y configurado GSAP, puedes implementar el scroll suave en tu aplicación Nuxt. A continuación, se muestra un ejemplo de cómo puedes hacerlo:

```vue
<script setup>
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';
import { ScrollSmoother } from 'gsap-trial/ScrollSmoother';

if (typeof window !== 'undefined') {
  gsap.config({
    trialWarn: false,
  });
  gsap.registerPlugin(ScrollTrigger, ScrollSmoother);
}

const main = ref();
let ctx;
let smoother;
onMounted(() => {
  ctx = gsap.context(() => {
    smoother = ScrollSmoother.create({
      smooth: 2, 
      effects: true,
    });
  }, main.value);
});

onUnmounted(() => {
  ctx.revert();
});


</script>
<template>
    <div class="bg-white dark:bg-gray-900">
      <main ref="{main}">
        <slot />
      </main>
    </div>
</template>
```

En este ejemplo, hemos implementado el scroll suave utilizando **GSAP** y **gsap-trial/ScrollSmoother**. Asegúrate de personalizar los valores según tus preferencias.

¡Listo! Ahora has implementado con éxito el scroll suave en tu aplicación Nuxt 3 utilizando GSAP. Los usuarios disfrutarán de una experiencia de navegación más agradable gracias a las transiciones suaves al desplazarse por tu sitio web.