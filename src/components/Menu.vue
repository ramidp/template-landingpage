<script setup>
import { ref } from 'vue'

const prop = defineProps({
        theme: Object,
        data: Object
          })


const mobile = ref(false)
const web = ref(false)
const tablet = ref(false)


if (window.innerWidth > 1100) {
    web.value = true;
    mobile.value = false;
    tablet.value = false;
} else if (window.innerWidth < 1100 && window.innerWidth > 764) {
    web.value = false;
    mobile.value = false;
    tablet.value = true;    
} else {
    mobile.value = true;
    web.value = false;
    tablet.value = false;
}



</script>

<template>

    <svg 
    v-if="web == true"
    xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 120">
    <path 
    fill="#e7008a" fill-opacity="1" d="M0,96L60,80C120,64,240,32,360,37.3C480,43,600,85,720,90.7C840,96,960,64,1080,58.7C1200,53,1320,75,1380,85.3L1440,96L1440,0L1380,0C1320,0,1200,0,1080,0C960,0,840,0,720,0C600,0,480,0,360,0C240,0,120,0,60,0L0,0Z"></path>
    </svg>
  
  <div class="menu-container">

    <a 
    class="logo"
    href="#top">
      <h1>{{ data.name }}        
      </h1>
    </a>    

      <a 
        class="anchors"
        href="#galeria">
        Galeria
      </a>  
    
        <a     
          class="anchors"
          href="#productos">
          Productos
        </a>  
  
        <a 
          class="anchors"
          href="#contacto">
            Contacto
        </a>       

  </div>

 
</template>

<style lang='scss' scoped>

svg {
  position: fixed;
  z-index: 10;
  width: 100%;

  @media (max-width: 1100px) {
    transform: scale(3);
  }

  @media (max-width: 764px) {
    transform: scale(5);
  }
  @media (max-width: 550px) {
    transform: scale(8);
  }
}

  .menu-container {
    width: 100%;
    display: flex;
    height: 10vh;
    justify-content: center;
    flex-direction: row;
    align-items: center;
    gap: 0 50px;
    z-index: 100;
    position: fixed;

    @media (max-width: 1100px) {
      background-color: v-bind('prop.theme.third');
      box-shadow: 0px 0px 5px 5px rgba(70, 70, 70, 0.418);

    }
    
    @media (max-width: 764px) {
      gap: 0 30px;
  }

    .logo {
    
      @media (max-width: 1100px) {
        display: none;
      }
    }

    a {
      text-decoration: none;

      h1 {
        color: v-bind('prop.theme.second');
        background-color: white;
        padding: 10px 15px;
        border-radius: 5px 15px;
        box-shadow: 0px 0px 10px 5px rgba(54, 2, 54, 0.473);
        transition: 300ms ease all;
        text-align: center;
        text-shadow: 0px 0px 5px violet;
  
        &:hover {
          cursor: pointer;
          transform: scale(1.1);
        }
      
      }
    } 
    

    .anchors {
      text-decoration: none;
      color: white;
      font-size: 22px;
      transition: 300ms ease all;
      font-weight: 700;

      @media (max-width: 764px) {
        font-size: 20px;
      }


      &:hover {
        color: rgb(255, 75, 105);        
      }
    }
  }

</style>
