<script setup>
import { ref } from 'vue'
import { library } from '@fortawesome/fontawesome-svg-core'
import { faIceCream } from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(faIceCream)  

const hidden = ref(false)

setTimeout(() => {
    hidden.value = true
}, 1800)


</script>

<template>

    <div
    :style="{display: hidden == true ? 'none' : 'flex'}"   
    class="loading-container">

      <font-awesome-icon :icon="['fa', 'ice-cream']" />    

    </div>

</template>

<style lang='scss' scoped>

.loading-container {
    width: 100%;
    height: 100vh;
    background-color: violet;
    position: fixed;
    justify-content: center;
    align-items: flex-start;
    padding-top: 300px;
    z-index: 1000;
    animation: fade 1s forwards;
    animation-delay: 500ms;

    @keyframes fade {
        0% { opacity: 100% }
        100% { opacity: 0% }
    }

    svg {
        font-size: 200px;
        color: white;
        animation: swirl-out-bck 0.6s ease-in both;
        animation-delay: 300ms;

        @media (max-width: 764px) {
            font-size: 100px;
        }
  

        @-webkit-keyframes swirl-out-bck {
        0% {
            -webkit-transform: rotate(0) scale(1);
                    transform: rotate(0) scale(1);
            opacity: 1;
        }
        100% {
            -webkit-transform: rotate(-540deg) scale(0);
                    transform: rotate(-540deg) scale(0);
            opacity: 0;
        }
        }
        @keyframes swirl-out-bck {
        0% {
            -webkit-transform: rotate(0) scale(1);
                    transform: rotate(0) scale(1);
            opacity: 1;
        }
        100% {
            -webkit-transform: rotate(-540deg) scale(0);
                    transform: rotate(-540deg) scale(0);
            opacity: 0;
        }
        }

    }

}


</style>
