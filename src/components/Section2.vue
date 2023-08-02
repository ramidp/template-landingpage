<script setup>
import photos from '../data/photos.json'
import { ref, onMounted } from 'vue'
import { library } from '@fortawesome/fontawesome-svg-core'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import { faArrowLeft, faArrowRight, faArrowDown, faArrowUp} from '@fortawesome/free-solid-svg-icons';



library.add(faArrowLeft, faArrowRight, faArrowDown, faArrowUp)  


// import Aos from 'aos'
// import 'aos/dist/aos.css'

// onMounted (() => {
// Aos.init({
//     duration: 1500,
//     once: false,
//     mirror: true,
//     });
// })

const prop = defineProps({
        theme: Object,
        data: Object,
          })

const arrayChanged = ref(photos)

const forward = () => {
    arrayChanged.value.unshift(arrayChanged.value.pop())
}

const backwards = () => {
    arrayChanged.value.push(arrayChanged.value.shift())
}

const backArrow = '<'

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

    <div class="sect2-container">

        <div
        class="carousel"
        >
            <button
            v-if="mobile"
             @click="backwards">
             <FontAwesomeIcon :icon="['fa' , 'arrow-up']"/>
            </button>

            
            <button
            v-else
             @click="backwards">            
             <FontAwesomeIcon :icon="['fa' , 'arrow-left']"/>
            </button>

                <img
                v-if='web'
                v-for="photo of arrayChanged.slice(0,4)"
                :src="photo.url" alt="">

                <img
                v-if='tablet'
                v-for="photo of arrayChanged.slice(0,3)"
                :src="photo.url" alt="">

                <img
                v-if='mobile'
                v-for="photo of arrayChanged.slice(0,3)"
                :src="photo.url" alt="">

            <button
            v-if="mobile"
            @click="forward"
            >
            <FontAwesomeIcon :icon="['fa' , 'arrow-down']"/>
            </button>
            <button
            v-else
            @click="forward"
            >
            <FontAwesomeIcon :icon="['fa' , 'arrow-right']"/>

            </button>

        </div>

        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1440 150">
        <path :fill='theme.second' fill-opacity="1" d="M0,96L60,80C120,64,240,32,360,37.3C480,43,600,85,720,90.7C840,96,960,64,1080,58.7C1200,53,1320,75,1380,85.3L1440,96L1440,320L1380,320C1320,320,1200,320,1080,320C960,320,840,320,720,320C600,320,480,320,360,320C240,320,120,320,60,320L0,320Z"></path>
        </svg>


    </div>

</template>

<style lang="scss" scoped>

.sect2-container {
    width: 100%;
    min-height: 70vh;
    height: auto;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    background-color: v-bind('prop.theme.fourth');
    padding-top: 100px;

    @media (max-width: 764px) {
        padding-top: 50px;
    }

    svg {
    width: 100%;
    bottom: 0; 

  }

    .carousel {
        width: 100%;
        height: auto;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
        gap: 0 30px;

        @media (max-width: 764px) {
            flex-direction: column;
            gap: 30px 0;
        }

        button {
            background-color: v-bind('prop.theme.third');
            border: none;
            padding: 30px;
            transition: 500ms ease all;
            border-radius: 10px;
            
            svg {
                color: white;
                font-size: 20px;
                fill: white;

            @media (max-width: 764px) {
                font-size: 16px;
            }

            }

            @media (max-width: 1100px) {
                padding: 30px 15px;
            }

            @media (max-width: 764px) {
                padding: 10px 50px;
            }
    
            &:hover {
                cursor: pointer;
                transform: scale(1.1);
            }
    
            &:active {
                transform: scale(1.4);
            }
        }
    
        img {
            width: 15vw;
            height: 20vh;
            border-radius: 20px;
            box-shadow: 0px 0px 10px 5px rgba(128, 0, 128, 0.452);
            object-fit: cover;
            transition: 500ms ease all;
            animation-name: fade;
            animation-duration: 1000ms;

            @media (max-width: 764px) {
                width: 70vw;
                height: 15vh;
            }
    
            @keyframes fade {
                0% { filter: opacity(0%)}
                100% { filter: opacity(100%)}
            }
        }
    }

}

</style>