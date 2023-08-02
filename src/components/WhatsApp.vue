<script setup>

import { library } from '@fortawesome/fontawesome-svg-core'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faWhatsapp } from '@fortawesome/free-brands-svg-icons'

library.add(faWhatsapp)  
 
const prop = defineProps({
        theme: Object,
        data: Object
          })

const number = prop.data.tel2.replace(/\s/g, '')

const mensaje = 'Hola, me gustaría hacer una consulta.'

</script>

<template>
    <div class="whatsapp">

        <a :href='"https://api.whatsapp.com/send?phone=" + `${number}` + "&text=" + `${mensaje}`'

        target="_blank"
        >
            <FontAwesomeIcon :icon="['fab' , 'whatsapp']"/>
        </a>

    </div>

</template>

<style lang="scss" scoped>

.whatsapp {
    display: flex;
    right: 1.5vw;
    bottom: 5vh;
    position: fixed;
    z-index: 10;
    animation-name: bounce-in-bottom;
    animation-duration: 2.5s;
    animation-fill-mode: forwards;

        @keyframes bounce-in-bottom {
  0% {
    -webkit-transform: translateY(500px);
            transform: translateY(500px);
    -webkit-animation-timing-function: ease-in;
            animation-timing-function: ease-in;
    opacity: 0;
  }
  38% {
    -webkit-transform: translateY(0);
            transform: translateY(0);
    -webkit-animation-timing-function: ease-out;
            animation-timing-function: ease-out;
    opacity: 1;
  }
  55% {
    -webkit-transform: translateY(40px);
            transform: translateY(40px);
    -webkit-animation-timing-function: ease-in;
            animation-timing-function: ease-in;
  }
  72% {
    -webkit-transform: translateY(0);
            transform: translateY(0);
    -webkit-animation-timing-function: ease-out;
            animation-timing-function: ease-out;
  }
  81% {
    -webkit-transform: translateY(28px);
            transform: translateY(28px);
    -webkit-animation-timing-function: ease-in;
            animation-timing-function: ease-in;
  }
  90% {
    -webkit-transform: translateY(0);
            transform: translateY(0);
    -webkit-animation-timing-function: ease-out;
            animation-timing-function: ease-out;
  }
  95% {
    -webkit-transform: translateY(8px);
            transform: translateY(8px);
    -webkit-animation-timing-function: ease-in;
            animation-timing-function: ease-in;
  }
  100% {
    -webkit-transform: translateY(0);
            transform: translateY(0);
    -webkit-animation-timing-function: ease-out;
            animation-timing-function: ease-out;
  }
}

        a {
            svg {
                transition: 500ms ease all;
                font-size: 30px;
                color: white;
                background-color:  green;
                padding: 12px;
                border-radius: 50%;

                
                &:hover {
                    transform: scale(1.2);
                }
            }
    }
}


</style>