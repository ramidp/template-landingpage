<script setup>
import GalleryItems from './individuals/GalleryItems.vue';
import banners from '../data/banners.json'
import { ref } from 'vue'


const prop = defineProps({
        theme: Object,
        data: Object
          })

const bannerRe = ref(banners)

// const events = {
//     'forward' : () => {
//         if (bannerId.value < banners.length) {
//             bannerId.value = bannerId.value + 1
//         } 
//     },
//     'backwards' : () => {
//         if (bannerId.value > 1 ) {b
//             bannerId.value = bannerId.value - 1
//         } 
//     }
// }

             
// Loop de funcion para que cambie de posición un valor de un arreglo con timer.
// Gracias al Loop, lo que hace es que se ejecute eternamente la función con el setTimeOut
// Cree una 2da variable que grabe el name del index 0, para usar un v-if en las imagenes y asi poder hacer una transición

const bannerId = ref(bannerRe.value[0].name) 

const myLoop = () => {  
  
  setTimeout(() => {
    bannerId.value = bannerRe.value[1].name
    bannerRe.value.push(bannerRe.value.shift())
      myLoop()
  },3000)
}

myLoop();  

</script>

<template>

<span
    id="galeria"
    ></span>

  <div 
  class="sect1-container">   

      <h1>Tentate con estas promos que tenemos para vos</h1>

        <GalleryItems
            :bannerRe='bannerRe'            
            :theme="theme"
            :banners="banners"
            :bannerId="bannerId"
        />    

    </div>

 
</template>

<style lang='scss' scoped>

  span {
    padding-top: 40px;
    margin-top: -40px;
  }

  .sect1-container {
    padding: 30px 10px 0 10px;
    width: calc(100% - 20px);
    height: calc(60vh - 60px);
    background-color: v-bind('prop.theme.fourth');
    display: flex;
    justify-content: flex-start;
    flex-direction: column;
    align-items: center;    
    gap: 0 30px;
    padding-top: 100px;
  }

  h1 {
    text-align: center;
    color: white;
    font-size: 40px;
    text-shadow: 0px 0px 10px rgba(184, 0, 138, 0.514);
    margin-bottom: 50px;

    @media (max-width: 1100px) {
      font-size: 30px;
    }
    @media (max-width: 764px) {
      font-size: 28px;
    }
  }

</style>
