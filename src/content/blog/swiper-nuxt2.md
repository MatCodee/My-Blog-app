---
title: 'Como instalar Swiper en Nuxt 2'
description: 'Como implementar la libreria Swiper en Nuxt 2'
pubDate: 'Jul 01 2022'
heroImage: '/category/nuxt.jpg'
category: 'Nuxt'
---

Instalamos usando npm u otro.
```
npm i swiper
```

Importamos directamente estas librerias en el archivo
```js
import Swiper from 'swiper/bundle';
import 'swiper/swiper-bundle.min.css';
```

```vue
<script>
import Swiper from 'swiper/bundle';
import 'swiper/swiper-bundle.min.css';

export default {
    data() {
        return {
            swiper: null,
        };
    },
    updated() {
        // Destruye Swiper existente antes de crear uno nuevo
        if (this.swiper) {
            this.swiper.destroy();
        }

        // Inicializa Swiper con la referencia al contenedor
        this.swiper = new Swiper(this.$refs.swiperContainer, {
            slidesPerView: 4,
            spaceBetween: 40,
            pagination: {
                el: '.swiper-pagination',
            },
            breakpoints: {
                350: {
                    slidesPerView: 1,
                    spaceBetween: 30,
                },
                668: {
                    slidesPerView: 2,
                    spaceBetween: 30,
                },
                992: {
                    slidesPerView: 3,
                    spaceBetween: 40,
                },
                1800: {
                    slidesPerView: 4,
                    spaceBetween: 40,
                }
            },
            navigation: {
                nextEl: '.swiper-button-next',
                prevEl: '.swiper-button-prev',
            },
        });
    },
    beforeDestroy() {
        // Destruye Swiper antes de que el componente se destruya para evitar fugas de memoria
        if (this.swiper) {
            this.swiper.destroy();
        }
    },

};
</script>
```
Porque tenemos que actualizar nuestro swiper, debido a que no se defresca automaticamente en nuxt 2, pero en nuxt 3 y vue 3 no es necesario hacer esto.

```html

<template>
    <div ref="swiperContainer" class="swiper-container">
        <div class="swiper-wrapper">
            <div class="swiper-slide">Slide 1</div>
            <div class="swiper-slide">Slide 2</div>
            <div class="swiper-slide">Slide 3</div>
        </div>
        <div class="swiper-button-prev"></div>
        <div class="swiper-button-next"></div>
    </div>
</template>
```