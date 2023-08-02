<script setup>

// import { library } from '@fortawesome/fontawesome-svg-core'
// import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
// import { faArrowLeft, faArrowRight } from '@fortawesome/free-solid-svg-icons';


// library.add(faArrowLeft, faArrowRight)  

const prop = defineProps({
        theme: Object,
        banners : Array,       
        bannerRe : Array,
        bannerId : String,
 })

//  const emit =  defineEmits({
//         'backwards' : Function,
//         'forward' : Function,
//     });
    

</script>

<template>

  <div class="gallery-container">
    

      <!-- <FontAwesomeIcon
      :style="{       
        color: prop.bannerId == 1 ? 'transparent' : 'purple',       
        }"    
        @click="$emit('backwards')"      
        :icon="['fa' , 'arrow-left']"/>       -->
      
      
        
      <div
      class="promo-container"
      v-for="(banner, index) of bannerRe"
      >    
        
        <TransitionGroup
        name="fade"      
        >
        <div
        v-show="prop.bannerId == banner.name"      
        :key="banner.id"
        class="animation-promo"
        >  

        <div
        class="text-fixed"
        >
          <h1>{{ banner.name }}</h1>
          <p>{{ banner.text1 }}</p>
          <p>{{ banner.text2 }}</p>

        </div>      
        
        <img
        :key="banner.id"
        :src="`${banner.url}`" :alt='`${banner.name}`'>    
        
      </div>
    </TransitionGroup>
    </div>
    
      

    <!-- <FontAwesomeIcon
    :style="{        
        color: prop.bannerId == banners.length ? 'transparent' : 'purple',
        }"    
    @click="$emit('forward')"
    :icon="['fa' , 'arrow-right']"/>      -->

  </div> 

 
</template>

<style lang='scss' scoped>

  .gallery-container {    
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 0 10px;

    svg {
        cursor: pointer;
        font-size: 30px;
    }

  .fade-enter-active {
  transition: all 800ms linear;
    }

    .fade-leave-active {
      transition: all 800ms linear,
    }

    .fade-enter-from,
    .fade-leave-to {    
      opacity: 0;
    }

    .animation-promo {
      display: flex;
      width: 100%;
      justify-content: center;
      align-items: center;
      position: absolute;
      left: 0;


      .text-fixed {
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
        width: 100%;
        z-index: 7;

        p {
          margin: 0;
          text-align: center;
          font-size: 30px;
          color: white;
          text-shadow: 0px 0px 5px black;

          @media (max-width: 764px) {
            font-size: 20px;
          }
        }
        
        h1 {
          text-align: center;
          margin: 0;
          margin-bottom: 30px;
          color: white;
          font-size: 70px;
          text-shadow: 0px 0px 5px black;

          @media (max-width: 764px) {
            font-size: 40px;
          }
        }
      }

        img {
            box-shadow: 0px 0px 10px 5px rgba(110, 0, 64, 0.308);
            height: 30vh;
            width: 90%;
            object-fit: cover;
            object-position: 50%;
            filter: opacity(70%);  
            
            @media (max-width: 764px) {
            width: calc(100% - 10px);
          }

            
        } 
    }
  }

</style>
