<script setup>
import Wallpaper2 from './Wallpaper2.vue';
import { library } from '@fortawesome/fontawesome-svg-core'
import { faIceCream } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import Section1 from '../components/Section1.vue';
import Section3 from '../components/Section3.vue';
import Section2 from '../components/Section2.vue';
import Section4 from '../components/Section4.vue';


library.add(faIceCream)  

const prop = defineProps({
        theme: Object,
        data: Object
          })
</script>

<template>

  
  <div class="main-container">

    <Wallpaper2/>

      <h1>{{ data.slogan1 }}
        <br>
        {{ data.slogan2 }}
        <font-awesome-icon :icon="['fas', 'ice-cream']" />    
      </h1>
  
      <a href="#contacto">
        Haz tu pedido!
      </a>    
  
        <p>Dirección:
          <br>
          {{ data.address }}
        </p>



      <!-- <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 120">
        <path :fill='theme.fourth' fill-opacity="1" d="M0,96L60,80C120,64,240,32,360,37.3C480,43,600,85,720,90.7C840,96,960,64,1080,58.7C1200,53,1320,75,1380,85.3L1440,96L1440,320L1380,320C1320,320,1200,320,1080,320C960,320,840,320,720,320C600,320,480,320,360,320C240,320,120,320,60,320L0,320Z"></path>
        </svg> -->


        <!-- Banners y Promos de importancia que sean mostrados como 2da prioridad -->
        <Section1
        :theme="theme"
        :data="data"
        />
        
        <!-- Carousel de imagenes para tentar -->
        <Section2
        :theme="theme"
        :data="data"
        />
        
        <!-- Productos importantes o subcategorias de productos (Ejemplo, en hamburgueseria: Hamburguesas, Papas, Gaseosas, Postres) -->
        <Section3
        :theme="theme"
        :data="data"
        />
        
        
        <!-- Formulario en caso de quererse -->
        <Section4
        :theme="theme"
        :data="data"
        />



    
  </div>

 
</template>

<style lang='scss' scoped>

  .main-container {
    width: 100%;
    height: auto;
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    align-items: center;
    gap: 0 30px;
    background-color: transparent ;

    h1 {
      padding-top: 50px;
      margin-bottom: 20px;
      text-align: center;
      color: v-bind('prop.theme.second');
      font-size: 100px;
      text-shadow: 0px 0px 10px white;
 
      @media (max-width: 764px) {
        font-size: 70px;
      }
    }

    a {
      text-decoration: none;
      color: white;
      padding: 20px 50px;
      font-size: 20px;
      border-radius: 20px;
      border: 1px solid white;
      background-color: v-bind('prop.theme.second');
      transition: 300ms ease all;

      @media (max-width: 764px) {
        padding: 10px 25px;
        font-size: 18px;
      }

      &:hover {
        cursor: pointer;
        transform: scale(1.1)
      }
    }
    
    p {
      text-align: center;
      font-size: 50px;
      height: 20vh;
      font-weight: 700;
      color: white;
      text-shadow: 0px 0px 5px rgba(68, 1, 68, 0.582);

      @media (max-width: 764px) {        
        font-size: 30px;
      }

    }

  }

</style>
