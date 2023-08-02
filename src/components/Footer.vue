<script setup>

import { library } from '@fortawesome/fontawesome-svg-core'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import AstaLogo from '/asta-transparente.png'
import { faTwitter, faYoutube, faInstagram, faFacebook  } from '@fortawesome/free-brands-svg-icons';



library.add(faFacebook, faInstagram, faTwitter, faYoutube)  

const prop = defineProps({
        theme: Object,
        data: Object
          })


</script>

<template>

  <div class="footer-container">

    <div
    class="over-wallpaper"
    >

    <a 
    v-for="media of data.media"
    :href="`${media.url}`">
    <FontAwesomeIcon :icon="['fab' , `${media.icon}`]"/>
    </a>     

      
    </div>

    
    <div
    class="sign-absolute"
    >
    <p>Derechos reservados IceCream 2023</p>
    <a 
    target="_blank"
    href="https://www.astaestudio.com">
    <img :src="AstaLogo" alt="">
  </a>
</div>


<svg 
class="wave"
xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 220">
<path fill="gray" fill-opacity="1" d="M0,96L60,80C120,64,240,32,360,37.3C480,43,600,85,720,90.7C840,96,960,64,1080,58.7C1200,53,1320,75,1380,85.3L1440,96L1440,320L1380,320C1320,320,1200,320,1080,320C960,320,840,320,720,320C600,320,480,320,360,320C240,320,120,320,60,320L0,320Z"></path>
</svg>
      
    

  </div>

 
</template>

<style lang='scss' scoped>

.footer-container {
    width: calc(100%);
    height: calc(50vh);
    display: flex;
    justify-content: flex-end;
    flex-direction: column;
    align-items: center;
    gap: 0 30px;  
    background-color: v-bind('prop.theme.second');

    @media (max-width: 764px) {
        justify-content: space-between;
      }


    .over-wallpaper { 
      display: flex;
      gap: 0 50px;

      @media (max-width: 764px) {
       padding-top: 50px;
       display: grid;
       grid-template-columns: repeat(2,  50%);
       grid-template-rows: repeat(2,  50%);
       gap: 20px;
      }


      svg {
        color: white;
        font-size: 50px;
        z-index: 10;
        transition: 300ms ease all;

        &:hover {
          cursor: pointer;
          transform: scale(1.2)
        }
        }
    }

    .sign-absolute {
      display: flex;
      justify-content: center;
      align-items: center;
      gap: 0 30px;
      position: absolute;
      padding: 20px 0;

      @media (max-width: 764px) {
       position: relative;
       flex-direction: column;
      }


      img {
        height: 50px;
        transition: 300ms ease all;
        
        &:hover {
          filter: contrast(150%)
        }
      }
  
      
      p {
        color: white;
        font-size: 16px;
      }
    }


    }


</style>
